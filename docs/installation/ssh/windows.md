---
hide:
  - toc
---

# Connexion SSH sous Windows

La connexion via SSH permet de pouvoir envoyer des commandes de tous types au Raspberry Pi.


- Afin d’obtenir l’adresse IP de votre Raspberry Pi sur votre réseau, téléchargez : :material-web: <a href="https://www.advanced-ip-scanner.com/fr/" target="_blank">Advanced IP Scanner</a>

- Exécutez le fichier et sélectionnez **Exécuter** - Lancer la version portable :

![01](../../assets/img/installation/ssh/windows/01.png){ width="600" }
 
- Une fois démarré cliquez sur **Analyser** :

![02](../../assets/img/installation/ssh/windows/02.png){ width="600" }
 
- Récupérez ensuite l’adresse IP correspondante à votre Raspberry Pi (il porte le même nom que le nom d’hôte renseigné dans **Raspberry Pi Imager**) :

![03](../../assets/img/installation/ssh/windows/03.png){ width="600" }

- Téléchargez et installez ensuite le logiciel : :material-web: <a href="https://mobaxterm.mobatek.net/download-home-edition.html" target="_blank">MobaXterm</a>

- Lancez-le puis cliquez sur l'icône **Session** :

![04](../../assets/img/installation/ssh/windows/04.png){ width="600" }

- Puis sur **SSH** :

![05](../../assets/img/installation/ssh/windows/05.png){ width="600" }
 
- Renseignez l'adresse IP de votre Raspberry Pi dans le champ **Remote Host**, cochez la case **Specify username** et saisissez le nom d'utilisateur pi dans le champ puis cliquez sur **OK** :

![06](../../assets/img/installation/ssh/windows/06.png){ width="600" }
 
- Sur la fenêtre qui s'affiche, saisissez votre mot de passe précédemment défini dans **Raspberry Pi Imager** (il ne s'affiche pas à la saisie, cela est normal) :
 
![07](../../assets/img/installation/ssh/windows/07.png){ width="600" }
 
- Une fenêtre d'autorisation va s'afficher, autorisez-la. Il est également possible qu’une autre fenêtre vous demandant de changer le mot de passe s'affiche, ignorez-là.

- Une fois connecté, sur la partie gauche de la fenêtre vous avez l'accès aux dossiers et fichiers de votre Raspberry Pi et à la fenêtre d'invite de commande SSH sur la partie droite :

![08](../../assets/img/installation/ssh/windows/08.png){ width="600" }
 
<br />

Vous pouvez ensuite continuer vers la section :material-arrow-right-box: [Installation des dépendances](../dependances.md).
