# TP LINUX 2

## Configuration VM

OS: Alpine linux (VM Edition)
CPU: 2 vCPU
RAM: 2048MB
DISK: 10GB
NETWORK: Bridge Mode | IP Locale: `192.168.2.36`

## Objectif

1. Créer un webhook Discord pour alertes de sécurité
2. Surveiller l’accès à un fichier sensible avec inotify et envoyer une alerte
3. Surveiller les connexions SSH hors horaires (9h–18h) et alerter
4. Automatiser l’exécution continue avec cron

---

### 1. Préparation et configuration du webhook

Créer un webhook dans un salon dédié (serveur Discord sécurité) et récupérer son URL (`WEBHOOK_URL`).

Test rapide du webhook :
```
WEBHOOK_URL="https://discord.com/api/webhooks/ID/TOKEN"
curl -H "Content-Type: application/json" -X POST -d '{"content":"Test webhook ✅"}' "$WEBHOOK_URL"
```

---

### 2. Surveillance des accès à un fichier sensible

Fichier sensible choisi : `/etc/secret.txt`

```
sudo apk add inotify-tools
```

Script de surveillance :
```sh
#!/bin/sh
set -euo pipefail

FILE_TO_WATCH="/etc/secret.txt"
WEBHOOK_URL="https://discord.com/api/webhooks/YOUR_WEBHOOK_URL"

# Crée le fichier s'il n'existe pas
[ -f "$FILE_TO_WATCH" ] || sudo install -m 600 /dev/null "$FILE_TO_WATCH"

echo "Surveillance de $FILE_TO_WATCH (événement: open)"
while inotifywait -q -e open "$FILE_TO_WATCH"; do
  host="$(hostname)"
  user="$(who am i 2>/dev/null | awk '{print $1}')"
  ts="$(date -Is)"
  msg="🚨 Accès détecté au fichier secret: $FILE_TO_WATCH | hôte=$host, user=${user:-unknown}, ts=$ts"
  curl -s -H "Content-Type: application/json" -X POST \
    -d "{\"content\":\"$msg\"}" "$WEBHOOK_URL" >/dev/null
done
```

Rendre exécutable et lancer en arrière-plan :
```
sudo chmod +x /usr/local/bin/watch_secret.sh
nohup /usr/local/bin/watch_secret.sh >/var/log/watch_secret.log 2>&1 &
```

---

### 3. Surveillance des connexions SSH hors horaires

Plage autorisée : 09:00–18:00 (tout avant 09:00 et à partir de 18:00 = alerte)

Script d’analyse (journalctl ou fallback sur /var/log/auth.log) :
```sh
#!/bin/sh
set -euo pipefail

WEBHOOK_URL="https://discord.com/api/webhooks/YOUR_WEBHOOK_URL"
OFFICE_START=9   # inclus
OFFICE_END=18    # exclus

send_alert() {
  local ts="$1"
  local user="$2"
  local src="$3"
  local msg="🕒 Connexion SSH hors horaires: user=$user, from=$src, ts=$ts"
  curl -s -H "Content-Type: application/json" -X POST \
    -d "{\"content\":\"$msg\"}" "$WEBHOOK_URL" >/dev/null
}

# Méthode 1 : journalctl (systemd)
if command -v journalctl >/dev/null 2>&1; then
  journalctl -u ssh -u sshd --since "-5 minutes" --output=short-iso \
  | grep -E "Accepted (publickey|password) for " \
  | while read -r line; do
      ts="$(echo "$line" | awk '{print $1" "$2}')"
      user="$(echo "$line" | sed -n 's/.*Accepted .* for \([^ ]*\) from.*/\1/p')"
      src="$(echo "$line"  | sed -n 's/.* from \([^ ]*\) port.*/\1/p')"

      hour="$(date -d "$ts" +%H 2>/dev/null || echo 99)"
      if [ "$hour" = "99" ]; then
        hour="$(echo "$line" | awk '{print substr($2,1,2)}')"
      fi

      if [ "$hour" -lt "$OFFICE_START" ] || [ "$hour" -ge "$OFFICE_END" ]; then
        send_alert "$ts" "$user" "$src"
      fi
    done
  exit 0
fi

# Méthode 2 : Fichier auth.log
LOG="/var/log/auth.log"
[ -r "$LOG" ] || exit 0

grep -E "sshd.*Accepted (publickey|password) for " "$LOG" \
| tail -n 300 \
| grep "$(date "+%b %e")" \
| while read -r line; do
    ts="$(echo "$line" | awk '{print $1" "$2" "$3}')"
    user="$(echo "$line" | sed -n 's/.*Accepted .* for \([^ ]*\) from.*/\1/p')"
    src="$(echo "$line"  | sed -n 's/.* from \([^ ]*\) port.*/\1/p')"
    hour="$(echo "$line" | awk '{print substr($3,1,2)}')"

    if [ "$hour" -lt "$OFFICE_START" ] || [ "$hour" -ge "$OFFICE_END" ]; then
      send_alert "$ts" "$user" "$src"
    fi
  done
```

Rendre exécutable :
```/dev/null/enable_ssh_check.sh#L1-1
sudo chmod +x /usr/local/bin/check_ssh_after_hours.sh
```

---

### 4. Automatisation avec cron

Activer le service cron :

Alpine :
```
sudo rc-service crond start
sudo rc-update add crond boot
```

Ajouter les tâches planifiées :
```
@reboot nohup /usr/local/bin/watch_secret.sh >/var/log/watch_secret.log 2>&1 &
*/5 * * * * /usr/local/bin/check_ssh_after_hours.sh
```

Éditer la crontab :
```/dev/null/edit_crontab.sh#L1-1
crontab -e
```
