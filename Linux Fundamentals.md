**FTP**

anonymous

**CP**

```bash
cp fichier /home/kali/Documents
cp source destination
```

- je peux l’utiliser pour copier un fichier dans un autre emplacement
- Pour copier un dossier dans un autre emplacement j’utilise l’option -R
**Exemple :** cp -R dossier /home/kali
- je peux copier plusieurs fichiers à la fois
**Exemple :** cp fichier fichier2 fichier3 /home/kali/Documents

```bash
cp note note2
```

- Je peux copier le contenue d’un fichier vers un nouveau

**RM**

```bash
rm fichier
rm fichier fichier2 fichier3
rm -R dossier
```

- Je peux supprimer un ou plusieurs fichiers à la fois
- Je peux également supprimer des dossiers toujours avec l’option -R

**MV**

```bash
mv fichier /home/kali/Documents
mv fichier nv_fichier
```

- Je peux changer l’emplacement d’un fichier sans créer un nouveau ou copier.
- Cela permet aussi de renommer un fichier
- Si `nv_fichier` existait déjà son contenue sera écrasé par le contenue du `fichier`

**FILE**

```bash
file fichier
***OUTPUT***
note: ASCII text
```

- Cette commande nous donne le type de fichier

### Les dossiers courants

### /etc

Ce répertoire racine est l'un des plus importants sur votre système. Le dossier **etc** (abréviation de etcetera) est un emplacement commun pour stocker les fichiers système utilisés par votre système d'exploitation.

Par exemple, le fichier **sudoers**  contient une liste des utilisateurs et des groupes qui ont la permission d'exécuter `sudo` ou un ensemble de commandes en tant qu'utilisateur root.

Sont également mis en évidence ci-dessous les fichiers **passwd** et **shadow**. Ces deux fichiers sont spéciaux pour Linux car ils montrent comment votre système stocke les mots de passe de chaque utilisateur dans un format chiffré appelé **sha512**.

### /var

Le répertoire **/var**, où "var" est l'abréviation de "variable data" (données variables), est l'un des principaux répertoires racine trouvés sur une installation Linux. Ce dossier stocke les données qui sont fréquemment consultées ou écrites par les services ou applications exécutés sur le système. Par exemple, les fichiers de log des services et applications en cours d'exécution sont écrits ici (**/var/log**), ainsi que d'autres données qui ne sont pas nécessairement associées à un utilisateur spécifique (par exemple, les bases de données et autres).

### /root

Contrairement au répertoire **/home**, le dossier **/root** est en réalité le répertoire personnel de l'utilisateur système "root". Il n'y a rien de plus à comprendre sur ce dossier, si ce n'est qu'il s'agit du répertoire personnel de l'utilisateur "root". Toutefois, il vaut la peine de le mentionner car la présomption logique serait que cet utilisateur aurait ses données dans un répertoire tel que **/home/root** par défaut.

### /tmp

C'est un répertoire racine unique trouvé sur une installation Linux. Abréviation de "temporary" (temporaire), le répertoire **/tmp** est volatile et est utilisé pour stocker des données qui ne sont nécessaires qu'une ou deux fois. À l'instar de la mémoire de votre ordinateur, une fois l'ordinateur redémarré, le contenu de ce dossier est effacé.

Ce qui est utile pour nous en tests d'intrusion (pentesting) est que tout utilisateur peut écrire dans ce dossier par défaut. Cela signifie qu'une fois que nous avons accès à une machine, ce répertoire sert de bon endroit pour stocker des éléments comme nos scripts d'énumération.

### Télécharger des documents

**SCP**

Secure Copy, cela nous permet de transférer des fichiers en utilisant le protocole SSH. Ce qui assure la confidentialité et l’intégrité des données.

On peut tout aussi bien copier des données de notre machine vers une autre machine comme d’une machine distante à notre machine.

| **Variable** | **Value** |
| --- | --- |
| The IP address of the remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on the local system | important.txt |
| Name that we wish to store the file as on the remote system | transferred.txt |

```bash
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
```

- Tout comme la commande `cp` nous utilisons une SOURCE et une DESTINATION

| **Variable** | **Value** |
| --- | --- |
| IP address of the remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on the remote system | documents.txt |
| Name that we wish to store the file as on our system | notes.txt |

```bash
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
```

**Utiliser son propre serveur web**

Python3 possède un module qui nous permet de transformer notre machine en un serveur web très facilement

```bash
python3 -m  http.server
```

- "HTTPServer" de Python3 permet d’avoir un serveur où on peut partager des données.
- Ce sera les fichiers du répertoire courant qui seront disponible avec cette commande de base.
- Le port par défaut sera 8000.

```bash
python3 -m http.server 8080
```

- Pour spécifier un port, on n’a qu’a simplement le préciser à la fin.
Donc pour cette commande le port sera 8080

```bash
python3 -m http.server --directory /chemin/vers/repertoire
```

- Pour spécifier le dossier qu’on souhaite partager, ou utilise l’option -d ou —directory en spécifiant après le chemin vers le dossier.

```bash
wget http://MACHINE_IP:8000/file
```

- Pour télécharger, on utilise la commande `wget`
- après on met **http://**[l’IP de la machine]**:**[Port]**/**[fichier voulu]
- Pour rappel, le port par défaut est 8000.

### Processus

```bash
ps -aux
```

- **a** : Affiche les processus de tous les utilisateurs.
- **u** : Affiche les processus avec des informations détaillées telles que l'utilisateur, l'utilisation du CPU, l'utilisation de la mémoire, etc.
- **x** : Affiche les processus qui ne sont pas attachés à un terminal de contrôle.

**Explication des colonnes** 

- **USER** : L'utilisateur propriétaire du processus.
- **PID** : L'identifiant unique du processus (Process ID).
- **%CPU** : Le pourcentage d'utilisation du CPU par le processus.
- **%MEM** : Le pourcentage d'utilisation de la mémoire physique (RAM) par le processus.
- **VSZ** : La taille virtuelle du processus en kilo-octets (mémoire virtuelle utilisée).
- **RSS** : La taille en mémoire résidente en kilo-octets (mémoire physique utilisée).
- **TTY** : Le terminal associé au processus. Si le processus n'est pas associé à un terminal, vous verrez `?`.
- **STAT** : Le statut du processus. Par exemple :
    - `R` : En cours d'exécution.
    - `S` : En veille (sleeping).
    - `D` : En attente (uninterruptible sleep).
    - `Z` : Zombie (le processus est terminé, mais son PID n'a pas encore été libéré par le parent).
    - `T` : Arrêté (stopped).
    - `s` : Processus de session.
    - `+` : Processus en avant-plan dans le terminal.
- **START** : L'heure ou la date de démarrage du processus.
- **TIME** : Le temps CPU total utilisé par le processus depuis son démarrage.
- **COMMAND** : La commande utilisée pour lancer le processus.

```bash
top
```

- Cette commande nous permet de voir les processus en temps-réel.
- Avec un temps de rafraichissement de 10s

```bash
kill **[PID]**
```

- la commande kill nous permet d’arrêter un processus en spécifiant son PID

Voici quelques-uns des signaux que nous pouvons envoyer à un processus lorsqu'il est tué :

- **SIGTERM** : Tue le processus, mais lui permet d'effectuer certaines tâches de nettoyage au préalable.
- **SIGKILL** : Tue le processus immédiatement - ne permet pas de faire de nettoyage après coup.
- **SIGSTOP** : Arrête/suspend un processus.

```bash
systemctl start [processus]
systemctl stop [processus]
systemctl enable [processus]
systemctl disable [processus]
```

- Le systemctl nous permet d’interagir avec le systemd
- start pour démarrer un service
- stop pour arrêter
- enable pour qu’un service se lance au démarrage de la machine
- disable pour qu’il ne se lance plus au démarrage.

**Background et Foreground** 

&

Ctrl + Z

fg

bg

### Automation

La commande crontab permet d’automatiser des taches. On peut spécifier quand ils vont s’exécuter, quand ils vont se répéter, combien de fois, etc.

 
[Crontab Generator](https://crontab-generator.org/)

| Value | Description |
| --- | --- |
| MIN | What minute to execute at |
| HOUR | What hour to execute at |
| DOM | What day of the month to execute at |
| MON | What month of the year to execute at |
| DOW | What day of the week to execute at |
| CMD | The actual command that will be executed. |

**Exemple :** `0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/`

Sauvegarder les "Documents" de "cmnatic" toutes les 12 heures.

`crontab -e`

### Logs

Nous avons brièvement abordé les fichiers de log et où ils peuvent être trouvés dans la partie 1 des Fondamentaux de Linux. Cependant, récapitulons rapidement. Situés dans le répertoire **/var/log**, ces fichiers et dossiers contiennent des informations de journalisation pour les applications et services s'exécutant sur votre système. Le système d'exploitation (OS) est devenu assez performant pour gérer automatiquement ces logs dans un processus connu sous le nom de "rotation".

J'ai mis en évidence certains logs de trois services s'exécutant sur une machine Ubuntu :

- Un serveur web Apache2
- Les logs pour le service fail2ban, qui est utilisé pour surveiller les tentatives de force brute, par exemple
- Le service UFW qui est utilisé comme pare-feu

**Types de logs**

- access log
- error log
