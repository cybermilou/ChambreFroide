# Chambre froide positive DIY (4–7 °C)

## Objectif du projet

Créer une petite chambre froide positive d’environ **7 m³**, destinée au stockage de légumes, à partir :
- d’un **groupe froid de congélateur domestique récupéré**,
- d’un système de **commande électronique personnalisé (Arduino ou équivalent)**,
- d’une pièce déjà isolée avec des **panneaux de chambre froide professionnels**.

Le projet vise une solution :
- fiable,
- simple à maintenir,
- peu énergivore,
- tolérante aux absences,
- évolutive,
- compréhensible techniquement.

---

## Cahier des charges

### Température cible
- Mode hiver : **4 °C**
- Mode été : **7 °C**
- Hystérésis : ±1 °C
- Priorité donnée à la stabilité plutôt qu’à la précision extrême

### Volume
- Environ **7 m³**

### Environnement
- Installation dans un garage naturellement frais
- Enceinte entourée de panneaux isolants type chambre froide

---

## Principe général de fonctionnement

Le système repose sur :
1. un **groupe frigorifique de congélateur conservé intact**,
2. une **commande externe du compresseur** via relais ou contacteur,
3. une **régulation logicielle** assurée par microcontrôleur,
4. une **ventilation interne** pour homogénéiser la température,
5. une **gestion simple du dégivrage**.

---

## Architecture fonctionnelle

### Bloc frigorifique
- Compresseur et condenseur issus d’un congélateur domestique
- Évaporateur placé dans la chambre froide
- Circuit frigorifique non modifié
- Condenseur ventilé et dégagé pour une bonne dissipation thermique

### Commande
- Microcontrôleur : Arduino / ESP32
- Relais ou contacteur pour piloter le compresseur
- Temporisation anti-redémarrage intégrée
- Sélecteur de mode été / hiver
- Afficheur pour l’état du système

---

## Capteurs

### Température
- Sonde **DS18B20 étanche**
- Positionnée :
  - à hauteur moyenne,
  - loin de l’évaporateur,
  - hors flux direct de ventilation.

### Humidité (optionnel)
- Capteur type **SHT31**
- Utilisé uniquement à des fins de surveillance
- Non critique pour la régulation

---

## Ventilation interne

### Objectif
Assurer une température homogène et limiter la formation de givre.

### Solution retenue
- 1 ou 2 ventilateurs 12 V (type PC, 120–140 mm)
- Débit modéré
- Fonctionnement continu ou intermittent

### Rôle
- réduire les zones froides,
- limiter la condensation locale,
- stabiliser les mesures de température.

---

## Gestion du dégivrage

Le système ne possède pas de résistance de dégivrage active.

### Méthode retenue
- arrêt périodique du compresseur,
- maintien ou arrêt contrôlé de la ventilation,
- dégivrage passif par remontée progressive en température.

### Paramètres typiques
- cycle toutes les 8 à 12 heures,
- durée : 15 à 30 minutes,
- reprise avec temporisation de sécurité.

---

## Logique de régulation

### Paramètres principaux
- Consigne hiver : 4 °C  
- Consigne été : 7 °C  
- Hystérésis : ±1 °C  
- Temps minimum OFF compresseur : 3 à 5 minutes  
- Temps minimum ON compresseur : 1 à 2 minutes  

### Règles de fonctionnement
- Si température > consigne + hystérésis → démarrage du compresseur
- Si température < consigne − hystérésis → arrêt du compresseur
- Blocage de redémarrage tant que la temporisation n’est pas écoulée

---

## Interface utilisateur

### Éléments prévus
- écran LCD ou OLED affichant :
  - température actuelle,
  - mode actif (été / hiver),
  - état du compresseur
- bouton ou interrupteur pour sélectionner le mode été / hiver
- éventuellement :
  - bouton de reset,
  - LED d’état ou d’alerte

---

## Sécurité

### Sécurité électrique
- disjoncteur dédié
- mise à la terre obligatoire
- boîtier fermé
- séparation stricte basse tension / 230 V

### Sécurité thermique
- thermostat mécanique indépendant monté en série
- coupure de sécurité en cas de dépassement anormal

### Sécurité frigorifique
- aucune modification du circuit frigorifique
- aucun perçage de tube
- aucune recharge de fluide
- respect des contraintes du compresseur

---

## Hypothèses d’utilisation

- ouvertures de porte limitées
- charge thermique modérée
- fonctionnement autonome possible plusieurs jours

---

## Évolutions possibles

- enregistrement des températures et humidité
- export USB ou Wi-Fi
- alertes de dépassement
- interface web
- automatisation avancée du dégivrage
- ajout d’un système de déshumidification passif
- supervision à distance
- alarme en cas de défauts

---

## Objectif final

Construire une chambre froide :
- fiable,
- silencieuse,
- économe,
- compréhensible,
- maintenable,
- évolutive,

à partir de matériel recyclé, avec une logique claire et documentée.

