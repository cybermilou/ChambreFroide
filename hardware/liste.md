 Bill of Materials (BOM) – Chambre froide positive DIY

Cette liste regroupe tout le matériel nécessaire pour construire une chambre froide positive (~7 m³) pilotée par microcontrôleur, à partir d’un groupe froid de congélateur.

Les éléments sont classés par catégorie, avec trois niveaux :
- **MUST** : indispensable
- **SHOULD** : fortement recommandé
- **COULD** : optionnel / amélioration

---

## 1. Groupe frigorifique (récupération)

### MUST
- Congélateur domestique fonctionnel  
  - type coffre ou armoire  
  - circuit frigorifique intact  
  - fluide courant (R600a ou R134a)   
- Compresseur + condenseur + évaporateur d’origine  
- Ventilation du condenseur (intégrée ou externe)

---

## 2. Enceinte / chambre froide

### MUST
- Joints supplémentaires (mousse ou caoutchouc)
- Passe-câbles étanches
- Bac ou tuyau d’évacuation des condensats

### SHOULD
- Grilles de protection mécanique autour du groupe froid
- Supports / équerres pour fixation propre

---

## 3. Électronique de commande

### Microcontrôleur
- **MUST**
  - ESP32 /  ATmega328P  (au choix, préférence pour le ATmega)
- **SHOULD**
  - ESP32 (si journalisation ou extensions futures)

---

## 4. Capteurs

### Température
- **MUST**
  - Sonde DS18B20 étanche (×1 minimum)
- **SHOULD**
  - 1 sonde supplémentaire (redondance ou tests)

### Humidité (optionnelle)
- **COULD**
  - Capteur SHT31 

---

## 5. Commande du compresseur (230 V)

### MUST
- Contacteur ou relais de puissance adapté au courant du compresseur  
  - bobine 230 V ou 12 V
- Relais statique (SSR) **ou** relais mécanique (selon choix)
- Disjoncteur dédié ou fusible adapté
- Bornier de raccordement
- Boîtier électrique fermé (3d)

### SHOULD
- Voyant lumineux état compresseur

---

## 6. Alimentation basse tension

### MUST
- Alimentation 230 V → 12 V DC (2–5 A)
- Alimentation 5 V (ou step-down depuis 12 V)
- Fusibles basse tension

### SHOULD
- Module buck step-down réglable
- Interrupteur général basse tension

---

## 7. Ventilation interne

### MUST
- 1 à 2 ventilateurs 12 V type PC (120 ou 140 mm)
- Grille de protection ventilateur

### SHOULD
- Support ou cadre de fixation
- Filtre simple (anti-poussière)

### COULD
- Contrôle logiciel de vitesse (PWM)

---

## 8. Interface utilisateur

### MUST
- Écran LCD ou OLED (I2C recommandé)
- Bouton ou interrupteur pour mode été / hiver

### SHOULD
- Bouton reset
- LED état (alimentation / compresseur)

### COULD
- Encodeur rotatif
- Buzzer léger pour alerte

---

## 9. Câblage & connectique

### MUST
- Câbles 230 V (section adaptée)
- Câbles basse tension
- Gaines thermorétractables
- Serre-câbles
- Dominos ou WAGO
- Borniers DIN
- Repères de fils
- support DIP-28 pour ATmega

### SHOULD
- Goulottes
- Passe-fils caoutchouc
- Connecteurs démontables

---

## 10. Sécurité

### MUST
- Mise à la terre correcte
- Séparation physique BT / 230 V
- Boîtier fermé et ventilé
- Thermostat mécanique de sécurité
- Protection contre contact accidentel

### SHOULD
- Etiquettes de sécurité
- Schéma électrique imprimé dans le coffret

---

## 14. Electronique

- Carte pour PCB
- SSD1306 (écran)
- Résistances 10kΩ (RESET pull-up)
- Résistances 4.7kΩ (pull_down)
- Résistances 330Ω (LED)
- LED
- Diodes de roue libre
- Connecteurs entrées/sorties
- Header ISP 2×3 (cable programmation)
- Boutons poussoir (changement mode ete/hiver)
- ÉBoutons bascules (marche arret)

---

## 13. Consommables

- Gaines thermorétractables
- Colliers nylon
- Ruban isolant
- Vis / écrous
- Serre-fils
- Étiquettes

---
