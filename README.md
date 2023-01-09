## Alimentation en eau de la cuve d'arrosage

Ce petit montage est utilisé afin de fermer le relais qui controle l'alimentation de l'electrovanne pour remplir la cuve d'eau d'arrosage.  
Un lcd 16x2 remonte les données de monitoring de l'arrosage.

### Fonctionnement :

Mode automatique, dégradé et manuel

Automatique: (via capteur de niveau et parametrages dans home-assistant) 
 - l'electrovanne s'ouvre à une heure déterminée si la cuve est en dessous de 90% et jusqu'a ce que la cuve soit pleine. 
 - L'electrovanne s'ouvre si la cuve descend en dessous de 10% jusqu'a ce que la cuve soit pleine + déclanchement en heure creuse uniquement. 

Dégradé/Autonome: (capteur de niveau hs, homeassistant hs, etc... via l'interface web interne de l'esp)   
 - l'ectrovanne s'ouvre toutes les 24 heures pendant une durée déterminée.

Manuel:  
 - Le relais est également activable manuellement au besoin via un simple switch dans home assistant ou via l'interface web de l'esp8266.
 L'automatisme de cuve pleine stopera automatiquement le relais. 

### Liste des composants :

- 1x ftdi 3.3v (pour le 1er flash)
- 1x esp8266 esp01s + breakout board
- 1x relais
- 1x convertisseur dc 5v=>3.3v (ams1117)
- 1x interrupteur
- 1x fusible 20x5 0.5A + porte fusible
- 2x borniers (alim 5v)
- 1x DHT22 (Température+Humidité boitier arrosage) 
- 1x resistance 4.7K ohm
- 1x pcb 2.54mm, du cable, etc...
- 1x connecteur 3 pins male + femelle
- 1x lcd 16x2 i2c (Affichage des données de monitoring de l'arrosage)
- 1x level shifter (pour signal i2c entre l'esp(3.3v) et le lcd(5v))

### Cablage :

GPIO 0 et 2 => i2c  
GPIO 1 (TX) => DHT22  
GPIO 3 (RX) => Relais  

![links](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/shema.png?raw=true)

### Montage :

![prototype](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/proto.jpg?raw=true)
![final](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/pcbok.jpg?raw=true)
![integration](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/pcbbox.jpg?raw=true)


### HomeAssistant :

#### Entités :

![links](https://github.com/NicoDupont/esp_remplissage_cuve/blob/main/img/entite.png?raw=true)

#### Automatismes :

 - ouverture relais   
  si remplissage cuve > 98%    
  ou  si débimetre = 0 depuis 1 minute et alimentation en cours  
  ou  si ouvert depuis plus de 2h  
  et gestion cuve on
 - fermeture relais   
  si heure prédéfinie et remplissage cuve < 90%  
  ou si remplissage cuve <10% et heure creuse en cours
  et gestion cuve on

#### Quelques liens :
- Home Assistant : [HomeAssistant](https://www.home-assistant.io/) 
- Esphome : [Esphome](https://esphome.io/index.html) 
- Esphome-flasher : [Esphome-flasher](https://github.com/esphome/esphome-flasher/releases)
    






