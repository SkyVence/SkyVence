# Rapport des Missions Accomplies

## Mission 1: Navigation dans la Tour

```bash
cd Castle/Main_tower/First_floor/Second_floor/Top_of_the_tower/
```
*   `cd`: Change le répertoire courant. Ici, vous naviguez à travers plusieurs niveaux de dossiers pour atteindre le sommet de la tour.

![img](https://media.discordapp.net/attachments/1380665924415131720/1425837138976571433/image.png?ex=68e909d0&is=68e7b850&hm=78e9039b87acc0e9dfc011400f97b2b6358a153c8cc1fc35fdf27329a0e36498&=&format=webp&quality=lossless&width=716&height=400)

## Mission 2: Accès à la Cave

```bash
cd Castle/Cellar
```
*   `cd`: Change le répertoire courant pour entrer dans le dossier "Cellar" (Cave).


![img](https://cdn.discordapp.com/attachments/1380665924415131720/1425837341679030382/image.png?ex=68e90a01&is=68e7b881&hm=98cbc516d45aa115b6571843d470bc5b608c9667c924863a1f3177e71a179a8a&)

## Mission 3: Retour à la Salle du Trône

```bash
cd
cd Castle/Main_building/Throne_room
```
*   `cd`: Sans argument, `cd` vous ramène à votre répertoire personnel (`~`).
*   `cd Castle/Main_building/Throne_room`: Ensuite, vous naviguez spécifiquement vers la Salle du Trône.

![img](https://media.discordapp.net/attachments/1380665924415131720/1425838369992212591/image.png?ex=68e90af6&is=68e7b976&hm=9d2690b97ad9f6fddb1f10336d05722f37102f14b40fa3aabdb81f6e70683b9a&=&format=webp&quality=lossless&width=793&height=442)

## Mission 4: Création d'un Abri dans la Forêt

```bash
mkdir Forest/Hut
mkdir Forest/Hut/Chest
```
*   `mkdir`: Crée un nouveau répertoire (dossier). Vous avez créé un "Hut" (Cabane) dans "Forest" (Forêt), puis un "Chest" (Coffre) à l'intérieur de la "Hut".


![img](https://media.discordapp.net/attachments/1380665924415131720/1425838370327761046/image.png?ex=68e90af6&is=68e7b976&hm=fbc9cb7cf8aa5aab8ce549ba9b7c469c5ea27b5ee0f743c514eb2f991720e20f&=&format=webp&quality=lossless&width=793&height=337)


## Mission 5: Nettoyage de la Cave

```bash
cd Castle/Cellar
rm spider_*
```
*   `cd Castle/Cellar`: Vous vous déplacez dans le répertoire "Cellar" (Cave).
*   `rm spider_*`: Supprime tous les fichiers dont le nom commence par "spider_" dans le répertoire courant. Le `*` est un caractère générique qui correspond à n'importe quelle séquence de caractères.



![img](https://media.discordapp.net/attachments/1380665924415131720/1425838370679947274/image.png?ex=68e90af6&is=68e7b976&hm=4f28827f95a6406728f4fa2ba750bfea9200d64fb17f4716dbf983be4891e681&=&format=webp&quality=lossless&width=729&height=333)

## Mission 6: Déplacement des Pièces d'Or du Jardin

```bash
mv ~/Garden/coin_* ~/Forest/Hut/Chest
```
*   `mv`: Déplace (ou renomme) des fichiers et des répertoires.
*   `~/Garder/coin_*`: Sélectionne tous les fichiers commençant par "coin_" dans le dossier "Garder" de votre répertoire personnel.
*   `~/Forest/Hut/Chest`: C'est la destination où les fichiers seront déplacés.

![img](https://media.discordapp.net/attachments/1380665924415131720/1425838370973810890/image.png?ex=68e90af6&is=68e7b976&hm=cfebdde85a657c4df9ff8845fa5f8d630b8a040abfbfff86cf3a55f05a6b46b3&=&format=webp&quality=lossless&width=708&height=356)

## Mission 7: Déplacement des Pièces Cachées du Jardin

```bash
mv ~/Garden/.*_coin_* ~/Forest/Hut/Chest/
```
*   `mv`: Déplace des fichiers.
*   `~/Garder/.*_coin_*`: Sélectionne tous les fichiers *cachés* (ceux qui commencent par un `.`) et contiennent "_coin_" dans le dossier "Garder" de votre répertoire personnel.
*   `~/Forest/Hut/Chest/Chest`: C'est la destination.

![img](https://media.discordapp.net/attachments/1380665924415131720/1425838857374666823/image.png?ex=68e90b6a&is=68e7b9ea&hm=24c6b0a34a6a3a4dc178c247c8402ed8a8574d07948942af70e4a273a7563ea4&=&format=webp&quality=lossless&width=711&height=396)


## Mission 8: Élimination des Araignées Visibles

```bash
ls -A ~/Castle/Cellar
rm ~/Castle/Cellar/*_spider_*
```
*   `ls -A`: Liste tous les fichiers et répertoires, y compris les fichiers cachés (qui commencent par un `.`), dans le répertoire spécifié.
*   `rm ~/Castle/Cellar/*_spider_*`: Supprime tous les fichiers dont le nom contient "_spider_" dans le dossier "Cellar".

![img](https://cdn.discordapp.com/attachments/1380665924415131720/1425839369620553839/image.png?ex=68e90be4&is=68e7ba64&hm=585e91cd1dffb5c8150d8f1a00d08337e3b53f7a661370a81ab835e0801da6c6&)


## Mission 9: Élimination des Araignées Cachées

```bash
ls -A ~/Castle/Cellar
rm ~/Castle/Cellar/.*_spider_*
```
*   `ls -A`: Liste tous les fichiers et répertoires, y compris les fichiers cachés, dans le répertoire spécifié.
*   `rm ~/Castle/Cellar/.*_spider_*`: Supprime tous les fichiers *cachés* (ceux qui commencent par un `.`) et contiennent "_spider_" dans le dossier "Cellar".

<img width="880" height="530" alt="image" src="https://github.com/user-attachments/assets/f672e8f0-55f5-45f1-a2c9-0a76f09149a3" />


## Mission 10: Copie des Étendards

```bash
cp ~/Castle/Great_hall/standard_? ~/Forest/Hut/Chest/
```
*   `cp`: Copie des fichiers.
*   `~/Castle/Great_hall/standard_?`: Sélectionne les fichiers qui commencent par "standard_" suivi d'un *seul* caractère quelconque (représenté par `?`).
*   `~/Forest/Hut/Chest/`: C'est la destination de la copie.

<img width="692" height="336" alt="image" src="https://github.com/user-attachments/assets/ffacd5a8-af0b-46ae-a2f5-7b7b890fd4cc" />


## Mission 11: Copie des Tapisseries

```bash
cp ~/Castle/Great_hall/*_tapestry_* ~/Forest/Hut/Chest/
```
*   `cp`: Copie des fichiers.
*   `~/Castle/Great_hall/*_tapestry_*`: Sélectionne tous les fichiers qui contiennent "_tapestry_" dans leur nom, peu importe ce qui précède ou suit.
*   `~/Forest/Hut/Chest/`: C'est la destination de la copie.

<img width="690" height="359" alt="image" src="https://github.com/user-attachments/assets/a2111e5b-e65c-4b0d-9ffa-ef55ef373341" />

## Mission 12: Copie d'une Peinture Spécifique

```bash
cd Castle/Main_tower/First_floor/
cp painting_ZcMMNUWB ~/Forest/Hut/Chest/
```
*   `cd Castle/Main_tower/First_floor/`: Vous vous déplacez au premier étage de la tour.
*   `cp painting_ZcMMNUWB ~/Forest/Hut/Chest/`: Copie le fichier `painting_ZcMMNUWB` vers le coffre.

<img width="730" height="333" alt="image" src="https://github.com/user-attachments/assets/4f75a204-30bd-4435-b10a-0c9aadb229ed" />

## Mission 13: Vérification de Calendrier

```bash
cal 01 1998
```
*   `cal`: Affiche un calendrier.
*   `01 1998`: Affiche le calendrier du mois de janvier 1998.

<img width="702" height="520" alt="image" src="https://github.com/user-attachments/assets/2eacc6f3-038a-4128-96cd-9f49bb9d4fea" />



## Mission 14: Création d'un Alias pour `ls -A`

```bash
alias la="ls -A"
```
*   `alias`: Crée un raccourci (un "alias") pour une commande.
*   `la="ls -A"`: Définit "la" comme un raccourci pour la commande `ls -A` (lister tous les fichiers, y compris les cachés).

<img width="650" height="361" alt="image" src="https://github.com/user-attachments/assets/358a615d-8bf3-4fe8-a5dc-6aaf4dd398d2" />


## Mission 15: Création et Écriture dans un Journal

```bash
touch ~/Forest/Hut/Chest/journal.txt
echo "salut" >> ~/Forest/Hut/Chest/journal.txt
```
*   `touch`: Crée un nouveau fichier vide ou met à jour la date de modification d'un fichier existant. Ici, il crée `journal.txt`.
*   `echo "salut"`: Affiche la chaîne de caractères "salut".
*   `>>`: Redirige la sortie de la commande `echo` et l'ajoute à la fin du fichier `journal.txt`.

<img width="724" height="365" alt="image" src="https://github.com/user-attachments/assets/811964fe-877c-4dab-ad1e-b2c0f5b34f26" />


## Mission 16: Création d'un Alias pour le Journal

```bash
alias journal="nano ~/Forest/Hut/Chest/journal.txt"
```
*   `alias`: Crée un alias.
*   `journal="nano ~/Forest/Hut/Chest/journal.txt"`: Définit "journal" comme un raccourci pour ouvrir le fichier `journal.txt` avec l'éditeur de texte `nano`.

<img width="948" height="589" alt="image" src="https://github.com/user-attachments/assets/b41e04b3-2025-47df-9e1f-e420db62e034" />


## Mission 17: Confrontation avec la Reine des Araignées

```bash
cd .Lair_of_the_spider_queen\ OLnhgPpyLTkcbiTh BQWCYEcOkBZWYdza/
rm NPBXVDlpransGrPe_spider_queen_yHYINFMhvXRCwKDN
```
*   `cd .Lair_of_the_spider_queen...`: Vous entrez dans un répertoire caché (commence par `.` et a un nom long). Le `\` est utilisé pour échapper les espaces dans le nom du dossier.
*   `rm NPBXVDlpransGrPe_spider_queen_yHYINFMhvXRCwKDN`: Supprime un fichier spécifique lié à la reine des araignées.

<img width="698" height="367" alt="image" src="https://github.com/user-attachments/assets/6763f532-4b50-4a53-9caf-00cb0172a8b6" />


## Mission 18: Xeyes

[image](https://cdn.discordapp.com/attachments/1420763245932711958/1425827521861255228/image.png?ex=68e900db&is=68e7af5b&hm=cc694730d15f8d2f8fbe82cd143e7bd03a4f93e78c3154b1f82da23b77ebe957&)

## Mission 19: Exécution de Commandes en Arrière-Plan

```bash
gsh check & flarigo & flarigo & flarigo &
```
*   `gsh check`: Exécute la commande `gsh check`.
*   `&`: Le symbole `&` à la fin d'une commande l'exécute en arrière-plan, vous permettant de continuer à utiliser le terminal. Vous avez exécuté `gsh check` et trois instances de `flarigo` en arrière-plan.

<img width="748" height="560" alt="image" src="https://github.com/user-attachments/assets/15ffeab7-4fee-457d-bfc7-543ec99c2be7" />


## Mission 20: Commande Spécifique "charmiglio"

```bash
charmiglio bbbb
```
*   `charmiglio bbbb`: Exécute une commande spécifique "charmiglio" avec "xxxx" comme argument. La fonction nous donne me dit le bon code au bout de 4 ctrl + c qui exit le programme

<img width="744" height="366" alt="image" src="https://github.com/user-attachments/assets/d854a723-4d57-4f77-8368-96a0d81dc32e" />


## Mission 21: Récupération de la Pièce de Cuivre

```bash
find -iname *copper_coin*
mv ./01b0dcd5d57731e3/1be2f4f502669f5b/bcfc663ddbde87b/OOOOO_copper_coin_OOOOO ~/Forest/Hut/Chest/
```
*   `mv`: Déplace le fichier `OOOOO_copper_coin_OOOOO` depuis un chemin très spécifique et long vers le coffre dans la cabane.

<img width="931" height="523" alt="image" src="https://github.com/user-attachments/assets/a81186ba-287e-4f07-a076-2f95186e1b81" />


## Mission 22: Récupération de la Pièce d'Argent

```bash
find -iname *silver_coin*
mv ./052c2d51b7dc412ef5c97850/35103a80c45f/88316ab4be9adc/OOOOO_silver_coin_OOOOO ~/Forest/Hut/Chest/
```
*   `mv`: Déplace le fichier `OOOOO_silver_coin_OOOOO` depuis un chemin très spécifique vers le coffre dans la cabane.

<img width="638" height="343" alt="image" src="https://github.com/user-attachments/assets/442b4cf8-07fe-4987-8c01-c0022a239ad8" />

## Mission 23: Récupération des Pièces d'Or dans le Labyrinthe

```bash
~/Garden/Maze
[mission 23] $ find . -iname *gold_coin*
./0810a6425119/7682305e0334286bf7b/bc025679a4f6eb48c14963e1ef/GolD_CoiN_2
./cfc76281/83f0a39efd9e776caef250/6947c3ead588ee2d77a53/gold_coin_1

~/Garden/Maze
[mission 23] $ mv ./0810a6425119/7682305e0334286bf7b/bc025679a4f6eb48c14963e1ef/GolD_CoiN_2 ~/Forest/Hut/Chest/

~/Garden/Maze
[mission 23] $ mv ./cfc76281/83f0a39efd9e776caef250/6947c3ead588ee2d77a53/gold_coin_1 ~/Forest/Hut/Chest/

~/Garden/Maze
[mission 23] $ gsh check
```
*   `find . -iname *gold_coin*`: Recherche des fichiers dont le nom contient "gold_coin" (sans tenir compte de la casse grâce à `-iname`) dans le répertoire courant (`.`) et ses sous-répertoires.
*   `mv ... GolD_CoiN_2 ~/Forest/Hut/Chest/`: Déplace la première pièce d'or trouvée vers le coffre.
*   `mv ... gold_coin_1 ~/Forest/Hut/Chest/`: Déplace la seconde pièce d'or trouvée vers le coffre.
*   `gsh check`: Vérifie si la mission est complète.

<img width="692" height="141" alt="image" src="https://github.com/user-attachments/assets/b3cb2092-77b6-4c13-8e74-d74a745920fa" />

## Mission 24: Lecture du Livre des Potions

```bash
~/Mountain/Cave
[mission 24] $ head -n 6 Book_of_potions/page_07
vvvvvvvvvv
Herbal tea
^^^^^^^^^^
1) Boil water.
2) Add herbs from the forest.
3) Let it sit for five minutes and drink while hot.

~/Mountain/Cave
[mission 24] $ gsh check
```
*   `head -n 6 Book_of_potions/page_07`: Affiche les 6 premières lignes (`-n 6`) du fichier `page_07` situé dans le dossier `Book_of_potions`.
*   `gsh check`: Vérifie si la mission est complète.

<img width="686" height="357" alt="image" src="https://github.com/user-attachments/assets/fc5bc4f2-6e81-4f9a-9845-93ea12462dec" />
