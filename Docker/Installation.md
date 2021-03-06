---
title: Installation
description: Installation de Docker sous Debian, Ubuntu, Arch, Manjaro, CentOS, Fedora, Redhat, MacOS et même Windows !
published: true
date: 2021-05-01T16:01:28.967Z
tags: 
editor: markdown
dateCreated: 2021-04-28T15:17:42.761Z
---

# Installation
Le package d'installation Docker disponible dans le référentiel officiel Debian n'est peut-être pas la dernière version. Pour nous assurer de disposer de la dernière version, nous installerons Docker à partir du référentiel Docker officiel. 
Pour ce faire, nous allons ajouter une nouvelle source de package, ajouter la clé GPG de Docker pour nous assurer que les téléchargements sont valides, puis installer le package.

## Debian & Ubuntu
  1 - Mettez à jour votre liste de packages existante :
 ```
 sudo apt update
 ```
  2 - Installez quelques packages prérequis qui permettent à `apt` d'utiliser des packages via HTTPS : 
 ```
 sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common
 ```
  3 - Ajoutez la clé GPG du référentiel Docker officiel à votre système :
 ```
 curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
 ```
  4 - Ajoutez le référentiel Docker aux sources APT :
 ```
 sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
 ```
  5 - Mettez à jour la base de données des packages avec les packages Docker du repo nouvellement ajouté :
 ```
 sudo apt update
 ```
  6 - Installez Docker :
 ```
 sudo apt install docker-ce
 ```
  7 - Activez et lancer le daemon Docker :
 ```
 sudo systemctl enable docker
 sudo systemctl start docker
 ```  
 
## Arch & Manjaro

## CentOS & Fedora

## MacOS

## Windows
Je vais me permettre de te tutoyer juste quelques lignes.
Si tu es sous Windows, installe Linux et on verra plus tard pour Docker 😘
Plus serieusement, le client Docker pour Windows n'est pas foufou : il utilise WSL pour faire une VM et ensuite installer Docker dedans.
Passe directement par un Debian sous WSL et fait l'installation de Docker dedans.
Bon courage ! Paix à ton âme. Il est jamais trop tard pour entrée dans la lumière. 🖖



# Utiliser les commandes Docker sans Sudo
