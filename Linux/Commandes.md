---
title: Commandes utiles
description: 
published: true
date: 2021-05-08T10:18:16.486Z
tags: 
editor: markdown
dateCreated: 2021-04-28T18:24:13.228Z
---

# Système

|     |     |
| --- | --- |
| `reboot` | Redémarre |
| `shutdown -now` | Éteint sans délais |
| `systemctl (start/stop/restart/status) <service>` | Démarre/Arrête/Redémarre/Affiche le statut d'un service |
| `uname -a` | Afficher les informations systèmes de linux |
| `uname -r` | Afficher la version du noyau |
| `uptime` | Afficher le temps d'activité du système et affiche la charge |
| `hostname` | Affiche le nom d'hôte de la machine |
| `hostname -I` | Affiche l'adresse IP de l'hôte |
| `last reboot` | Afficher l'historique des redémarrages |
| `date` | Afficher la date et l'heure du système |
| `cal` | Affiche le calendrier du mois |
| `w` | Affiche qui est en ligne |
| `whoami` | Affiche où nous sommes connecté en tant que qui |

# Matériel

|     |     |
| --- | --- |
| `dmesg` | Affiche les messages du noyau |
| `cat /proc/cpuinfo` | Affiche les informations du CPU |
| `cat /proc/meminfo` | Affiche les informations de la RAM |
| `free -h` | Affiche la mémoire libre et utilisé (-h pour lisible par l'homme, -m for MB et -g pour GB) |
| `lspci -tv` | Affiche les périphériques PCI |
| `lsusb -tv` | Affiche les périphériques USB |
| `dmidecode` | Affiche les information DMI/SMBIOS (informations systèmes) depuis le BIOS |
| `hdparm -i /dev/sda` | Affiche les informations du disque /dev/sda |
| `hdparm -rT /dev/sda` | Faire un test de vitesse de lecture sur le disque /dev/sda |
| `badblocks -s /dev/sda` | Test le disque /dev/sda pour d'éventuels blocks défectueux |

# Réseau

| Ancienne commande : | Nouvelle commande : |
| --- | --- |
| `ifconfig -a` | `ip a` |
| `ifconfig enp6s0 down` | `ip link set enp6s0 down` |
| `ifconfig enp6s0 up` | `ip link set enp6s0 up` |
| `ifconfig enp6s0 192.168.2.24` | `ip addr add 192.168.2.24/24 dev enp6s0` |
| `ifconfig enp6s0 netmask 255.255.255.0` | `ip addr add 192.168.1.1/24 dev enp6s0` |
| `ifconfig enp6s0 mtu 9000` | `ip link set enp6s0 mtu 9000` |
| `ifconfig enp6s0:0 192.168.2.25` | `ip addr add 192.168.2.25/24 dev enp6s0` |
| `netstat` | `ss` |
| `netstat -tulpn` | `ss -tulpn` |
| `netstat -neopa` | `ss -neopa` |
| `netstat -g` | `ip maddr` |
| `route` | `ip r` |
| `route add -net 192.168.2.0 netmask 255.255.255.0 dev enp6s0` | `ip route add 192.168.2.0/24 dev enp6s0` |
| `route add default gw 192.168.2.254` | `ip route add default via 192.168.2.254` |
| `arp -a` | `ip neigh` |
| `arp -v` | `ip -s neigh` |
| `arp -s 192.168.2.33 1:2:3:4:5:6` | `ip neigh add 192.168.3.33 lladdr 1:2:3:4:5:6 dev enp6s0` |
| `arp -i enp6s0 -d 192.168.2.254` | `ip neigh del 192.168.2.254 dev wlp7s0` |

# Fichiers et répertoires

## ls - Lister le contenu d'un répertoire

**Permet de lister le contenu d'un répertoire**

```plaintext
ls <option> répertoire
```

| Option | Commentaire |
| --- | --- |
| `-a` | Lister tout le répertoire (y compris fichier caché) |
| `-l` | Afficher le répertoire sous forme de tableau, avec permission, ... |
| `-i` | Affiche les inodes |
| `-h` | Affiche la taille dans un format lisible par l'homme (Mo par exemple) |
| `-R` | Liste également les sous-répertoires |
| `-s` | Affiche la taille des répertoires |

## pwd - Afficher le répertoire courant

**Affiche le répertoire dans lequel on se situe.**

```plaintext
pwd
```

## mkdir - Créer un répertoire

**Créer un répertoire.**

```plaintext
mkdir -p /chemin/répertoire/à/créer
```

| Option | Commentaire |
| --- | --- |
| `-p` | Créer les répertoires parents si ces derniers n'existent pas |

*Exemple : Je souhaite créer un répertoire **truc** dans /home/user1/test1, mais le fichier test1 n'existe pas.*

```plaintext
mkdir -p /home/user1/test1/truc
```

## cd - Changer de répertoire

**Permet de se déplacer dans l'arborescence**

```plaintext
cd /répertoire/de/destination
```

## cat - Afficher le contenu d'un fichier

**Permet d'ouvrir un fichier et d'afficher son contenu.**

```plaintext
cat <option> fichier
```

| Option | Commentaire |
| --- | --- |
| `-b` | Numéroter toutes les lignes non vides |
| `-n` | Numéroter toutes les lignes |

## df - Afficher la taille d'un répertoire

**Permet d'afficher la taille d'un répertoire.**

```plaintext
df <option> répertoire
```

| Option | Commentaire |
| --- | --- |
| `-h` | Permet d'obtenir un résultat plus lisible pour un humain (*ex Mo, Ko,...*) |
| `-i` | Affiche les inodes |
| `-k` | Affiche le résultat en kilobytes |
| `-m` | Affiche le résultat en megabytes |
| `-d **n**.` | Affiche la taille des sous-répertoires jusqu'au **n**ème |

## mv - Déplacer un fichier ou dossier

**Permet de déplacer un fichier ou un répertoire.**

```plaintext
mv <option> /chemin/source /chemin/destination
```

| Option | Commentaire |
| --- | --- |
| `-f` | Forcer le déplacement |
| `-i` | Demander la confirmation de l'utilisateur |

## rm - Supprimer un fichier ou dossier

**Permet de supprimer un fichier ou un dossier**

```plaintext
rm <option> /chemin/truc/a/supprimer
```

| Option | Commentaire |
| --- | --- |
| `-d` | Efface un répertoire |
| `-f` | Force la suppression |
| `-i` | Demande confirmation à l'utilisateur (*Inutile avec* `*-f*`) |
| `-r` | Récursif |

## tar - Compression et décompression

**Permet de compresser ou décompresser en fonction des options**

```plaintext
tar -[options] <nom_fichier_destination> <fichier_ou_dossier_source>
```

| Option | Commentaire |
| --- | --- |
| `-c` | Création d'une archive |
| `-v` | Verbose |
| `-f` | Indique un nom de fichier de destination |
| `-z` | Compression gzip |
| `-j` | Compression bzip |
| `-x` | Extraction d'une archive |
| `-t` | Lire le contenu d'une archive |
| `-r` | Ajouter un fichier à une archive existante |

*Exemple : Archiver un dossier.*

```plaintext
tar -cvf test.tar /chemin/dossier/a/compresser
```

Exemple : Désarchiver un dossier.

```plaintext
tar -xvf test.tar /chemin/dossier/destination
```

# Sessions, Utilisateurs et Permissions

## groups - Afficher les groupes d'appartenance d'un utilisateur

**Permet d'afficher dans quels groupes se trouve l'utilisateur**

```plaintext
groups utilisateur
```

## passwd - Changer le mot de passe

**Permet de changer le mot de passe d'un utilisateur**

```plaintext
passwd <option> utilisateur
```

| Option | Commande |
| --- | --- |
| `-d` | Supprimer le mot de passe |
| `-e` | Faire expirer le mot de passe |
| `-i` | Rendre un compte inactif |
| `-l` | Verouille le mot de passe et empêche sa modification par l'utilisateur |
| `-S` | Affiche le status du compte |
| `-u` | Déverouille un mot de passe |

# Logiciel

## Tipee

|     |     |
| --- | --- |
| `tipee` | Connaitre le temps restant de la journée |
| `tipee punch` | Badger les heures |

Lien : [Gitlab](https://gitlab.infomaniak.ch/mickaelasseline/python-tipee)

## Git

|     |     |
| --- | --- |
| `git status` | Permets d'afficher le statut du dépôt dans lequel nous sommes (quelle branche, s'il y a des commit à réaliser…) |
| `git add nom_du_fichier` | Permet de “tracker” (suivre) le fichier, et ainsi, le faire reconnaître par Git pour des prochaines actions (merge, commit, status…) |
| `git init “nom_du_dossier”` | Initialise le dossier, créant ainsi un dossier caché “.git" qui sera reconnu par l'outil Git et les plateformes comme GitHub, GitLab… Sans cela, le dossier ne sera jamais utilisable par Git. |
| `git log` | Affiche les dernières actions réalisées sur le repository (incluant les métadatas, les commit ID, commit messages…) |
| `git clone` | Clone un projet sur sa machine. |
| `git commit -am “message”` | Met à jour le commit avec un message défini. |
| `git fetch` | Récupère les informations d'un repository sans télécharger sur la machine. |
| `git push` | Envoi la mise à jour au git distant (dit “remote”). Prends en compte le dossier dans lequel on se situe. |
| `git pull` | Récupère les dernières mises à jours du répertoire distant |