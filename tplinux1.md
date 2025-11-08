# TP LINUX 1


## Configuration VM

OS: Alpine linux (VM Edition)

CPU: 2 Vcpu

RAM: 2048MB

DISK: 10GB

NETWORK: Bridge Mode | IP Locale: `192.168.2.36`

## Objectif

1. Installer apache
2. Lancer le service au demarage
3. Ajouter du contenue a la page web par defaut
4. Verifier que le service fonctionne

5. Installer le par feu (ufw)
6. Ouvrir les ports 8080 et 22 dans le par feu
7. Desactiver tous les autres ports
8. Modifier la configuration apache pour utiliser le port 8080 au lieu du port 80
9. Redemarrer le service apache
10. Verifier que le service fonctionne toujours

11. Ajouter une clef ssh sur un utilisateur avec permisions sudo
12. Desactiver le login root via ssh

### 1. Installer apache

Verifier que les depots sont a jour puis installer apache2

```sh
apk update
```
```sh
apk add apache2
```

### 2. Lancer le service au demarage

Demarrer le service apache2 et l'ajouter au demarage automatique
(Je demarre le service avant de l'ajouter au demarage pour verifier qu'il fonctionne correctement)

```sh
rc-service apache2 start
```

```sh
rc-update add apache2 default
```

### 3. Ajouter du contenue a la page web par defaut

Modifier le fichier index.html par defaut pour ajouter du contenu

```sh
echo "<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Linux is Better</title>
    <style>
        body {
            background-color: #f0f0f0;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
        }
        h1 {
            color: #333;
            font-size: 48px;
            text-align: center;
            animation: fadeIn 2s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>
    <h1>Linux is better</h1>
</body>
</html>" > /var/www/localhost/htdocs/index.html
```

### 4. Verifier que le service fonctionne

Ouvrir un navigateur web et acceder a l'adresse IP de la machine virtuelle
(http://192.168.2.36) pour verifier que la page web s'affiche correctement.

![tplinux-apache2gif](https://github.com/user-attachments/assets/78ac34e9-9869-4dff-89ad-ff11a1403f3d)


### 5. Installer le par feu (ufw)

```sh
apk update
apk add ufw
rc-update add ufw
````

### 6. Ouvrir les ports 8080 et 22 dans le par feu

```sh
ufw --force reset # Reset la configuration presente
```

```sh
ufw allow 8080/tcp
```
```sh
ufw allow 22/tcp
```

### 7. Desactiver tous les autres ports

```sh
ufw default deny incoming
ufw default allow outgoing
```

### 8. Modifier la configuration apache pour utiliser le port 8080 au lieu du port 80

Modifier le fichier de configuration d'apache pour changer le port d'ecoute

Trouver dans la configuration :
```
listen <Port> # Par defaut 80
```
Replacer avec:
```
listen 8080
```

### 9. Redemarrer le service apache

```sh
rc-service apache2 restart
```

### 10. Verifier que le service fonctionne toujours

Ouvrir un navigateur web et acceder a l'adresse IP de la machine virtuelle avec le port 8080
(http://192.168.2.36:8080) pour verifier que la page web s'affiche correctement.

<img width="2547" height="1025" alt="Screenshot 2025-11-06 230347" src="https://github.com/user-attachments/assets/ef450a96-195a-45d8-ac4d-7e3d08bc1d68" />


### 11. Ajouter une clef ssh sur un utilisateur avec permisions sudo

Alpine linux utilise doas a la place de sudo ducoup je vais ajouter un groupe dans la config de doas

```sh
echo "permit persist :sky" >> /etc/doas.conf
```

Creer un utilisateur avec des permissions doas

```sh
addgroup sky
adduser -G sky skyvence
passwd skyvence
```

Creer le home de mon nouvel utilisateur et ajouter un clef ssh

```sh
install -o skyvence -g skyvence -m 700 -d /home/skyvence/.ssh
install -o skyvence -g skyvence -m 600 /dev/stdin /home/skyvence/.ssh/authorized_keys <<'EOF'
<Clef ssh Publique ici>
EOF
```

### 12. Desactiver le login root via ssh

```sshd.conf
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication no
ChallengeResponseAuthentication no
```

Redem le service sshd
```sh
rc-service sshd restart
```


#### All in one script

```sh
#!/bin/sh

set -e

# Variables - Customize these for your environment
WEB_PORT="8080"
SSH_PORT="22"
USERNAME="skyvence"
USERGROUP="sky"

# 1. Install Apache
apk update
apk add apache2
echo "✓ Apache installed"

# 2. Start Apache service at boot
rc-service apache2 start
rc-update add apache2 default
echo "✓ Apache configured to start at boot"

# 3. Add content to default web page
cat > /var/www/localhost/htdocs/index.html <<'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Linux is Better</title>
    <style>
        body {
            background-color: #f0f0f0;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
        }
        h1 {
            color: #333;
            font-size: 48px;
            text-align: center;
            animation: fadeIn 2s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>
    <h1>Linux is better</h1>
</body>
</html>
EOF
echo "✓ Web page created"

# 4. Verify Apache is working
rc-service apache2 status > /dev/null
echo "✓ Apache verified"

# 5. Install UFW firewall
apk update
apk add ufw
rc-update add ufw
echo "✓ UFW installed"

# 6 & 7. Configure firewall
ufw --force reset
ufw allow $WEB_PORT/tcp
ufw allow $SSH_PORT/tcp
ufw default deny incoming
ufw default allow outgoing
ufw --force enable
echo "✓ Firewall configured"

# 8. Configure Apache to use port 8080
sed -i "s/^Listen 80$/Listen $WEB_PORT/" /etc/apache2/httpd.conf
echo "✓ Apache port changed to $WEB_PORT"

# 9. Restart Apache
rc-service apache2 restart
echo "✓ Apache restarted"

# 10. Verify Apache is working
rc-service apache2 status > /dev/null
echo "✓ Apache verified on new port"

# 11. Create user with doas permissions
echo "permit persist :$USERGROUP" >> /etc/doas.conf
addgroup $USERGROUP 2>/dev/null || true
adduser -G $USERGROUP $USERNAME 2>/dev/null || true
passwd $USERNAME
install -o $USERNAME -g $USERGROUP -m 700 -d /home/$USERNAME/.ssh
cat > /tmp/ssh_key_temp
install -o $USERNAME -g $USERGROUP -m 600 /tmp/ssh_key_temp /home/$USERNAME/.ssh/authorized_keys
rm /tmp/ssh_key_temp
echo "✓ User created with SSH key"

# 12. Secure SSH
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
sed -i 's/^#*PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config
sed -i 's/^#*PubkeyAuthentication.*/PubkeyAuthentication yes/' /etc/ssh/sshd_config
sed -i 's/^#*PasswordAuthentication.*/PasswordAuthentication no/' /etc/ssh/sshd_config
sed -i 's/^#*ChallengeResponseAuthentication.*/ChallengeResponseAuthentication no/' /etc/ssh/sshd_config
grep -q "^PermitRootLogin" /etc/ssh/sshd_config || echo "PermitRootLogin no" >> /etc/ssh/sshd_config
grep -q "^PubkeyAuthentication" /etc/ssh/sshd_config || echo "PubkeyAuthentication yes" >> /etc/ssh/sshd_config
grep -q "^PasswordAuthentication" /etc/ssh/sshd_config || echo "PasswordAuthentication no" >> /etc/ssh/sshd_config
grep -q "^ChallengeResponseAuthentication" /etc/ssh/sshd_config || echo "ChallengeResponseAuthentication no" >> /etc/ssh/sshd_config
rc-service sshd restart
echo "✓ SSH secured"

echo "Configuration complete"
```

