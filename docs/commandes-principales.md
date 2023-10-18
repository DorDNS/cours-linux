# Commandes principales

## 1. Premières commandes

!!! note "Qu’est-ce qu’une commande ?"

    Une *commande* est une séquence de mots se terminant par un caractère de nouvelle ligne. Autrement dit, une commande est une séquence de caractères qui se termine par la touche `<Entrée>`. Le premier mot est le nom de la commande, les autres sont ses *arguments*. La commande est exécutée par le shell, qui est un programme qui interprète la ligne de commande.

    ```shell
    $ touch file.txt
    ```

    Ici la commande est `touch` et son argument est `file.txt`. Le signe `$` au début de la ligne est l'invite de commande. Il ne fait pas partie de la commande.

    Chaque mot de la ligne de commande est séparé par un ou plusieurs espaces. Le Shell interprète les espaces comme des séparateurs entre les mots. Le Shell interprète le caractère de nouvelle ligne comme la fin de la commande.

!!! note "Parcourir les commandes et manipuler le Shell"

    Lorsque l’on appuie sur la touche `↑`, on **remonte** les commandes entrées. 

    Lorsque l’on appuie sur la touche `↓`, on **redescend** les commandes entrées depuis là où on est remonté. 

    Lorsque l’on appuie sur `C-l` (`Ctrl` et `l` en même temps), le Shell **remonte la dernière ligne de commande** pour l’afficher en haut de la page (sans effacer l’historique précédent).

    Lorsque l’on appuie sur `C-u`, cela permet d’**effacer de l’historique une commande spécifique** que l’on recherche.

    Lorsque l’on appuie sur `C-d`, on **ferme la fenêtre** du Shell.

    En ouvrant un nouveau terminal Debian, puis en appuyant sur `C-p` alors on **retrouve les commandes** entrées dans la fenêtre précédente.

    En entrant la commande `PS1=’$ ‘`, alors on **simplifie l’affichage en début de ligne de commande** dans le Shell par un simple `$`.

## 2. Répertoires et fichiers

!!! note "Chemin d'accès"

    La référence à une ressource (fichier ou répertoire) s'appelle un chemin d'accès (en anglais : path). Dans ce chemin, sous Linux, les noms des répertoires et éventuel fichier sont séparés par un slash `/` (alors qu'on utilise un antislash `\` sous Windows).

    Il existe deux types de chemin : absolu et relatif.

    1. Un **chemin absolu** se base sur la racine de l'arborescence et commence par `/`, par exemple : `/home/debian` est le chemin absolu vers le répertoire personnel de l'utilisateur debian. Il reste valable quel que soit le contexte.

    2. Un **chemin relatif** est a priori relatif au répertoire courant où se trouve l'utilisateur. Par exemple, si le répertoire courant est `/home/debian`, le chemin relatif `./Documents` fait référence au répertoire `/home/debian/Documents`. Un chemin qui commence par autre chose que `/` ou `~` est un chemin relatif.

    Le `.` fait référence au répertoire courant. Les `..` font référence au répertoire parent.

!!! note "Parcourir des répertoires et des fichiers"

    La commande `pwd` **affiche le chemin vers le répertoire courant** (celui sur lequel on se trouve).

    En entrant la commande `ls`, on **liste tous les fichiers et répertoires présents dans le répertoire courant**.

    La commande `cd` permet de **se déplacer** dans l’arborescence des fichiers. 

    - On l’accompagne de l’argument `..` (avec un espace entre `cd` et `..`) pour **revenir au répertoire parent**.
    - Pour **revenir directement à la racine**, on utilise l’argument `/`.
    - Puis on peut mettre en argument le **chemin (absolu ou relatif) vers un répertoire** en particulier pour s’y déplacer (ex: `cd /usr/include`).

    Si l’on souhaite **revenir directement au répertoire HOME**, alors on passe par le symbole `~` (commande `Option - N` sur Mac). Par exemple, la commande `cd ~` nous ramène directement à ce répertoire.

!!! note "Afficher le contenu de fichiers"

    Pour **afficher le contenu** d’un fichier donné, on utilise la commande `cat` accompagnée du nom du fichier en argument.

    !!! success "Exemple"

        En entrant d’abord `cd /usr/include` on se retrouve dans le répertoire contenant toutes les bibliothèques de langage C.

        Pour afficher le contenu de la bibliothèque `stdlib.h` alors on entre la commande suivante :

        ```shell
        $ cat stdlib.h
        ```

!!! note "Créer des fichiers et des répertoires"

    Pour **créer un répertoire**, on utilise la commande `mkdir` accompagnée en argument du nom que l’on souhaite lui donner. Le répertoire est alors créé dans le répertoire courant.

    Si l’on veut créer un répertoire dans un autre répertoire déjà existant, alors on met le chemin absolu vers l’emplacement en terminant ce chemin par le nom du répertoire que l’on souhaite créer. On peut aussi utiliser la `~` pour créer un répertoire à partir du répertoire HOME.

    Si l’on **crée un répertoire dans un répertoire qui n’existe pas** avec `mkdir` seulement, alors ça ne fonctionnera pas. Une manière de régler ce problème est de mettre l’option `-p` après la commande `mkdir` pour “forcer” la création du répertoire parent qui jusque alors n’existait pas.

    !!! success "Exemple"

        On a l’arborescence suivante dans le répertoire `HOME` :
        
        <img src="../images/arbo_ctp1.png" alt="" width="500"/>

        Si l’on entre la commande :

        ```bash
        $ mkdir tp_shell
        ```

        alors on a créé le répertoire `tp_shell` dans le répertoire HOME.

        Mais la commande 

        ```bash
        $ mkdir vivant/plante/fleur
        ```

        ne permet pas la création des répertoires indiqués en argument.

        Pour régler ce problème, on entre alors la commande suivante :

        ```bash
        $ mkdir -p vivant/plante/fleur
        ```

        On a donc, dans le répertoire HOME, le répertoire `vivant` qui contient le répertoire `plante`, qui lui-même contient le répertoire `fleur`.