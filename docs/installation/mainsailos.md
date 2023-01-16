---
hide:
  - toc
---

# Installation de MainsailOS

MainsailOS est le sytème d'exploitation du Raspberry Pi. Il s'appuie sur Raspberry Pi OS Lite en incluant Klipper, Moonraker et Mainsail dans le fichier image à installer, ce qui rend la configuration rapide et plus facile à utiliser.


- Téléchargez et installez le logiciel : :simple-raspberrypi: <a href="https://www.raspberrypi.com/software/" target="_blank">Raspberry Pi Imager</a>

- Lors de l'ouverture de Raspberry Pi Imager, les éléments suivants s'affichent :

![01](../assets/img/installation/mainsailos/01.png){ width="600" }

- Insérez votre carte microSD dans votre ordinateur.

- Sélectionnez **CHOISISSEZ L'OS**, une fenêtre contextuelle s'ouvre et faites défiler jusqu'à **Formatter** :

![02](../assets/img/installation/mainsailos/02.png){ width="600" }

- Cliquez sur **CHOISISSEZ LE STOCKAGE** et sélectionnez votre carte microSD :

![03](../assets/img/installation/mainsailos/03.png){ width="600" }

- Cliquez ensuite sur **ECRIRE** et confirmez le formatage de la carte microSD :

![04](../assets/img/installation/mainsailos/04.png){ width="600" }
 
- Une fois l'opération terminée sélectionnez **FORMATTER** :

![05](../assets/img/installation/mainsailos/05.png){ width="600" }

- Faites défiler jusqu'à **Other specific-purpose OS** :

![06](../assets/img/installation/mainsailos/06.png){ width="600" }

- Sélectionnez **3D printing** :

![07](../assets/img/installation/mainsailos/07.png){ width="600" }

- Sélectionnez **Mainsail OS** :
 
![08](../assets/img/installation/mainsailos/08.png){ width="600" }

- Sélectionnez la version désirée (32-bit ou 64-bit) :

![09](../assets/img/installation/mainsailos/09.png){ width="600" }
 
- Cliquez ensuite sur **CHOISISSEZ LE STOCKAGE** et sélectionnez votre carte microSD :
 
![10](../assets/img/installation/mainsailos/10.png){ width="600" }

- Le nom d'hôte, le SSH, le Wi-Fi, la langue et de nombreux autres paramètres peuvent désormais être parcourus et préconfigurés dans un menu de configuration, en cliquant sur la petite roue dentée dans le coin en bas à droite :

![11](../assets/img/installation/mainsailos/11.png){ width="600" }

- Configurez les divers paramètres comme suit :

{==

:warning: **Veuillez ne pas changer le nom d’utilisateur pi !** La configuration de MainsailOS repose sur cet utilisateur.

==}

![12](../assets/img/installation/mainsailos/12.png)
 
  <u>Note</u> : Si vous modifiez le paramètre <i>Set hotname</i>, l'URL de votre Raspberry Pi sera modifiée en conséquence.
<br />
  Comme indiqué dans la capture d'écran ci-dessus, votre URL sera : <a href="http://flsun-super-racer.local" target="_blank">http://flsun-super-racer.local</a>
                                                                                                                            
- Cliquez ensuite sur **SAVE** pour sauvegarder ces paramètres.

- Vous pouvez ensuite cliquer sur **ÉCRIRE** :

![13](../assets/img/installation/mainsailos/13.png){ width="600" }
 
- Puis acceptez l'avertissement :

![14](../assets/img/installation/mainsailos/14.png){ width="600" }

- Cela prendra un certain temps pour écrire l'image sur la carte microSD :

![15](../assets/img/installation/mainsailos/15.png){ width="600" }
 
- Une fois l’écriture terminée, une vérification sera effectuée :

![16](../assets/img/installation/mainsailos/16.png){ width="600" }

- Une fois la vérification terminée, cliquez sur **CONTINUER** :

![17](../assets/img/installation/mainsailos/17.png){ width="600" }
 
- L'installation est maintenant terminée.

- Vous pouvez fermer **Raspberry Pi Imager**, insérer la carte microSD dans votre Raspberry Pi et le démarrer.

<br />

Vous pouvez ensuite continuer vers la section de connexion SSH en fonction de votre système d'exploitation :

:material-arrow-right-box: [Connexion SSH sous Windows](ssh/windows.md)

:material-arrow-right-box: [Connexion SSH sous macOS](ssh/macos.md)

