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

Créer un webhook dans un salon dédié et récupérer son URL (`WEBHOOK_URL`).

Test rapide du webhook :
```
WEBHOOK_URL="https://discord.com/api/webhooks/ID/TOKEN"
curl -H "Content-Type: application/json" -X POST -d '{"content":"Test webhook ✅"}' "$WEBHOOK_URL"
```

---

### 2. Surveillance des accès à un fichier sensible

Fichier sensible choisi : `/etc/secret.txt`

```
apk add inotify-tools
```

Script de surveillance :
```sh
#!/bin/sh

FILE_TO_WATCH="/etc/secret.txt"
WEBHOOK_URL="https://discord.com/api/webhooks/<webhookurl>"

while inotifywait -e open "$FILE_TO_WATCH"; do
  curl -H "Content-Type: application/json" -X POST -d "{\"content\": \"🚨 Accès détecté au fichier secret: $FILE_TO_WATCH\"}" $WEBHOOK_URL
done
```

Rendre exécutable et lancer en arrière-plan :
```
chmod +x /usr/local/bin/watch_secret.sh
nohup /usr/local/bin/watch_secret.sh &
```

---

### 3. Surveillance des connexions SSH hors horaires

Plage autorisée : 09:00–18:00 (tout avant 09:00 et à partir de 18:00 = alerte)

```sh
#!/bin/sh
WEBHOOK_URL="https://discord.com/api/webhooks/<webhookurl>"

# Cherche toutes les connexions SSH dans les dernières 5 minutes
LOG="/var/log/auth.log"
LIMIT=$(date --date='5 minutes ago' '+%b %d %H:%M')
OUT_OF_HOURS=$(awk -v lim="$LIMIT" '$0 > lim {if ($0 ~ /Accepted/) { split($3,time,":"); h=time[1]; if (h<9||h>=18) print $0 }}' $LOG)

if [ -n "$OUT_OF_HOURS" ]; then
  curl -H "Content-Type: application/json" -X POST \
    -d '{"content": "🚨 Connexion SSH hors horaires : '"$(echo "$OUT_OF_HOURS" | tail -1)"'"}' $WEBHOOK_URL
fi

```

Rendre exécutable :
```sh
chmod +x /usr/local/bin/check_ssh_after_hours.sh
```

---

### 4. Automatisation avec cron

Activer le service cron :

Alpine :
```sh
rc-service crond start
rc-update add crond boot
```

Ajouter les tâches planifiées :
```sh
@reboot nohup /usr/local/bin/watch_secret.sh &
*/5 * * * * /usr/local/bin/check_ssh_after_hours.sh
```

Éditer la crontab :
```sh
crontab -e
```
