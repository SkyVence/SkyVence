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
install -o skyvence -g skyvence -m 700 -d /home/alice/.ssh
install -o skyvence -g skyvence -m 600 /dev/stdin /home/alice/.ssh/authorized_keys <<'EOF'
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


