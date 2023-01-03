## Alimentation en eau de la cuve d'arrosage

#### Quelques liens :
- Home Assistant : [HomeAssistant](https://www.home-assistant.io/) 
- Esphome : [Esphome](https://esphome.io/index.html) 
- Esphome-flasher : [Esphome-flasher](https://github.com/esphome/esphome-flasher/releases)

Ce petit montage est utilisé afin d'ouvrir l'electrovanne pour remplir la cuve d'eau d'arrosage.

### Fonctionnement :

Mode automatique et mode degradé

Automatique: (via capteur de niveau et parametrages dans home-assistant) 
 - l'electrovanne s'ouvre à une heure déterminée si la cuve est en dessous de 90% et jusqu'a ce que la cuve soit pleine. 
 - L'electrovanne s'ouvre si la cuve descend en dessous de 10% jusqu'a ce que la cuve soit pleine. 

Dégradé/Autonome: (capteur de niveau hs, homeassistant hs,etc... via l'interface web interne de l'esp)   
 - l'ectrovanne s'ouvre toutes les 24 heures pendant une durée déterminée.

### Liste des composants :

- 1x ftdi 3.3v (1er flash)
- 1x esp8266 esp01s + board 
- 1x relais
- 1x convertisseur 5v dc=>3.3v (ams1117)
- 1x DHT22 (Température boitier arrosage)
- 1x resistance 4.7K ohm
- 1x pcb 2.54mm
- 1x interrupteur
- 1x fusible 20x5 1A + porte fusible
- 2x borniers 
- 1x connecteur 3 pins male + femelle
- 1x lcd 16x2 i2c (Affichage des données de monitoring de l'arrosage)
- 1x level shifter 

### Cablage :

![links](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/shema.png?raw=true)

### Montage :

![links](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/pcb.png?raw=true)


### HomeAssistant :

#### Esphome :

1. créer un nouveau noeud dans esphome.  
2. le nommer 'esp_remplissage_cuve' ou comme vous le souhaitez... 
3. copier le code du fichier esp_remplissage_cuve.yaml  
4. Adapter le code (wifi, non des entités, etc...)
5. télécharger le binaire et flasher avec esphome flasher  ou flasher directement depuis le navigateur

#### DashBoard :

Rien de très spécial ici, 1 carte d'entités  + 2 mini graph

![links](https://github.com/NicoDupont/esp_ventilation_rack_info/blob/main/img/dashboardha.png?raw=true)
    






