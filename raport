# Rapport des Missions Accomplies

## Mission 1: Navigation dans la Tour

```bash
cd Castle/Main_tower/First_Floor/Second_floor/Top_of_the_tower
```
*   `cd`: Change le répertoire courant. Ici, vous naviguez à travers plusieurs niveaux de dossiers pour atteindre le sommet de la tour.

## Mission 2: Accès à la Cave

```bash
cd Castle/Cellar
```
*   `cd`: Change le répertoire courant pour entrer dans le dossier "Cellar" (Cave).

## Mission 3: Retour à la Salle du Trône

```bash
cd
cd Castle/Main_building/Throne_room
```
*   `cd`: Sans argument, `cd` vous ramène à votre répertoire personnel (`~`).
*   `cd Castle/Main_building/Throne_room`: Ensuite, vous naviguez spécifiquement vers la Salle du Trône.

## Mission 4: Création d'un Abri dans la Forêt

```bash
mkdir Forest/Hut
mkdir Forest/Hut/Chest
```
*   `mkdir`: Crée un nouveau répertoire (dossier). Vous avez créé un "Hut" (Cabane) dans "Forest" (Forêt), puis un "Chest" (Coffre) à l'intérieur de la "Hut".

## Mission 5: Nettoyage de la Cave

```bash
cd Castle/Cellar
rm spider_*
```
*   `cd Castle/Cellar`: Vous vous déplacez dans le répertoire "Cellar" (Cave).
*   `rm spider_*`: Supprime tous les fichiers dont le nom commence par "spider_" dans le répertoire courant. Le `*` est un caractère générique qui correspond à n'importe quelle séquence de caractères.

## Mission 6: Déplacement des Pièces d'Or du Jardin

```bash
mv ~/Garder/coin_* ~/Forest/Hut/Chest
```
*   `mv`: Déplace (ou renomme) des fichiers et des répertoires.
*   `~/Garder/coin_*`: Sélectionne tous les fichiers commençant par "coin_" dans le dossier "Garder" de votre répertoire personnel.
*   `~/Forest/Hut/Chest`: C'est la destination où les fichiers seront déplacés.

## Mission 7: Déplacement des Pièces Cachées du Jardin

```bash
mv ~/Garder/.*_coin_* ~/Forest/Hut/Chest/Chest
```
*   `mv`: Déplace des fichiers.
*   `~/Garder/.*_coin_*`: Sélectionne tous les fichiers *cachés* (ceux qui commencent par un `.`) et contiennent "_coin_" dans le dossier "Garder" de votre répertoire personnel.
*   `~/Forest/Hut/Chest/Chest`: C'est la destination.

## Mission 8: Élimination des Araignées Visibles

```bash
ls -A ~/Castle/Cellar
rm ~/Castle/Cellar/*_spider_*
```
*   `ls -A`: Liste tous les fichiers et répertoires, y compris les fichiers cachés (qui commencent par un `.`), dans le répertoire spécifié.
*   `rm ~/Castle/Cellar/*_spider_*`: Supprime tous les fichiers dont le nom contient "_spider_" dans le dossier "Cellar".

## Mission 9: Élimination des Araignées Cachées

```bash
ls -A ~/Castle/Cellar
rm ~/Castle/Cellar/.*_spider_*
```
*   `ls -A`: Liste tous les fichiers et répertoires, y compris les fichiers cachés, dans le répertoire spécifié.
*   `rm ~/Castle/Cellar/.*_spider_*`: Supprime tous les fichiers *cachés* (ceux qui commencent par un `.`) et contiennent "_spider_" dans le dossier "Cellar".

## Mission 10: Copie des Étendards

```bash
cp ~/Castle/Great_hall/standard_? ~/Forest/Hut/Chest/
```
*   `cp`: Copie des fichiers.
*   `~/Castle/Great_hall/standard_?`: Sélectionne les fichiers qui commencent par "standard_" suivi d'un *seul* caractère quelconque (représenté par `?`).
*   `~/Forest/Hut/Chest/`: C'est la destination de la copie.

## Mission 11: Copie des Tapisseries

```bash
cp ~/Castle/Great_hall/*_tapestry_* ~/Forest/Hut/Chest/
```
*   `cp`: Copie des fichiers.
*   `~/Castle/Great_hall/*_tapestry_*`: Sélectionne tous les fichiers qui contiennent "_tapestry_" dans leur nom, peu importe ce qui précède ou suit.
*   `~/Forest/Hut/Chest/`: C'est la destination de la copie.

## Mission 12: Copie d'une Peinture Spécifique

```bash
cd Castle/Main_tower/First_floor/
cp painting_ZcMMNUWB ~/Forest/Hut/Chest/
```
*   `cd Castle/Main_tower/First_floor/`: Vous vous déplacez au premier étage de la tour.
*   `cp painting_ZcMMNUWB ~/Forest/Hut/Chest/`: Copie le fichier `painting_ZcMMNUWB` vers le coffre.

## Mission 13: Vérification de Calendrier

```bash
cal 01 1998
```
*   `cal`: Affiche un calendrier.
*   `01 1998`: Affiche le calendrier du mois de janvier 1998.

## Mission 14: Création d'un Alias pour `ls -A`

```bash
alias la="ls -A"
```
*   `alias`: Crée un raccourci (un "alias") pour une commande.
*   `la="ls -A"`: Définit "la" comme un raccourci pour la commande `ls -A` (lister tous les fichiers, y compris les cachés).

## Mission 15: Création et Écriture dans un Journal

```bash
touch ~/Forest/Hut/Chest/journal.txt
echo "salut" >> ~/Forest/Hut/Chest/journal.txt
```
*   `touch`: Crée un nouveau fichier vide ou met à jour la date de modification d'un fichier existant. Ici, il crée `journal.txt`.
*   `echo "salut"`: Affiche la chaîne de caractères "salut".
*   `>>`: Redirige la sortie de la commande `echo` et l'ajoute à la fin du fichier `journal.txt`.

## Mission 16: Création d'un Alias pour le Journal

```bash
alias journal="nano ~/Forest/Hut/Chest/journal.txt"
```
*   `alias`: Crée un alias.
*   `journal="nano ~/Forest/Hut/Chest/journal.txt"`: Définit "journal" comme un raccourci pour ouvrir le fichier `journal.txt` avec l'éditeur de texte `nano`.

## Mission 17: Confrontation avec la Reine des Araignées

```bash
cd .Lair_of_the_spider_queen\ OLnhgPpyLTkcbiTh BQWCYEcOkBZWYdza/
rm NPBXVDlpransGrPe_spider_queen_yHYINFMhvXRCwKDN
```
*   `cd .Lair_of_the_spider_queen...`: Vous entrez dans un répertoire caché (commence par `.` et a un nom long). Le `\` est utilisé pour échapper les espaces dans le nom du dossier.
*   `rm NPBXVDlpransGrPe_spider_queen_yHYINFMhvXRCwKDN`: Supprime un fichier spécifique lié à la reine des araignées.

## Mission 18: Xeyes

[image](https://cdn.discordapp.com/attachments/1420763245932711958/1425827521861255228/image.png?ex=68e900db&is=68e7af5b&hm=cc694730d15f8d2f8fbe82cd143e7bd03a4f93e78c3154b1f82da23b77ebe957&)

## Mission 19: Exécution de Commandes en Arrière-Plan

```bash
gsh check & flarigo & flarigo & flarigo &
```
*   `gsh check`: Exécute la commande `gsh check`.
*   `&`: Le symbole `&` à la fin d'une commande l'exécute en arrière-plan, vous permettant de continuer à utiliser le terminal. Vous avez exécuté `gsh check` et trois instances de `flarigo` en arrière-plan.

## Mission 20: Commande Spécifique "charmiglio"

```bash
charmiglio xxxx
```
*   `charmiglio xxxx`: Exécute une commande spécifique "charmiglio" avec "xxxx" comme argument. La fonction exacte de cette commande n'est pas détaillée ici, mais elle est reconnue comme une mission réussie.

## Mission 21: Récupération de la Pièce de Cuivre

```bash
mv ./01b0dcd5d57731e3/1be2f4f502669f5b/bcfc663ddbde87b/OOOOO_copper_coin_OOOOO ~/Forest/Hut/Chest/
```
*   `mv`: Déplace le fichier `OOOOO_copper_coin_OOOOO` depuis un chemin très spécifique et long vers le coffre dans la cabane.

## Mission 22: Récupération de la Pièce d'Argent

```bash
mv ./052c2d51b7dc412ef5c97850/35103a80c45f/88316ab4be9adc/OOOOO_silver_coin_OOOOO ~/Forest/Hut/Chest/
```
*   `mv`: Déplace le fichier `OOOOO_silver_coin_OOOOO` depuis un chemin très spécifique vers le coffre dans la cabane.

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
