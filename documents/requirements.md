# Requirements

## Objectif

Définir les exigences fonctionnelles, techniques et de sécurité pour la chambre froide positive DIY (~7 m³) pilotée par microcontrôleur.

Les exigences sont classées par priorité :
- **MUST** : indispensable pour que le système soit considéré comme réussi
- **SHOULD** : fortement recommandé
- **COULD** : optionnel / nice-to-have

---

## Contexte et hypothèses

- Volume : **~7 m³**
- Local : garage naturellement frais
- Isolation : panneaux type chambre froide pro (épais)
- Groupe froid : congélateur domestique **récupéré**, circuit frigorifique **non modifié**
- Usage : stockage non critique (hors exigences HACCP strictes)

---

## Exigences fonctionnelles

### Température

- **MUST** : Maintenir une température moyenne dans la chambre comprise entre **3 °C et 8 °C** en fonctionnement normal.
- **MUST** : Disposer de deux modes :
  - **Mode Hiver** : consigne **4 °C**
  - **Mode Été** : consigne **7 °C**
- **MUST** : Intégrer une **hystérésis configurable** (valeur par défaut cible : **±1 °C**).
- **SHOULD** : Éviter les gradients internes importants ; objectif de dispersion spatiale typique : **≤ 2 °C** (avec ventilation).

### Pilotage compresseur

- **MUST** : Empêcher tout redémarrage immédiat du compresseur après arrêt via un **temps minimum OFF** (cible : **300 s**).
- **MUST** : Piloter le compresseur via un organe de puissance adapté (relais/SSR/contactor).
- **SHOULD** : Implémenter un **temps minimum ON** (cible : **60–120 s**) pour limiter les cycles courts.
- **MUST** : Démarrer/arrêter le compresseur uniquement selon la logique de régulation et les sécurités.

### Ventilation interne

- **MUST** : Assurer une circulation d’air interne (ventilation) pour homogénéiser la température.
- **SHOULD** : Permettre un contrôle simple (ON continu, ou ON intermittent configurable).

### Dégivrage

- **MUST** : Prévoir une stratégie de dégivrage **passif** (arrêt compresseur périodique).
- **SHOULD** : Rendre le cycle de dégivrage configurable (périodicité + durée).
- **COULD** : Détecter un besoin de dégivrage via observation (ex. dérive de performance) ou capteur optionnel (non prioritaire).

---

## Exigences d’interface utilisateur

- **MUST** : Afficher la température mesurée.
- **MUST** : Indiquer l’état du compresseur (ON/OFF).
- **MUST** : Permettre la sélection du mode **Hiver/Été** (interrupteur/bouton).
- **SHOULD** : Afficher le mode actif et la consigne.
- **COULD** : Afficher humidité (si capteur présent), timers (anti-redémarrage, dégivrage), alarmes.

---

## Exigences capteurs

### Température

- **MUST** : Utiliser une sonde de température robuste et stable (ex. **DS18B20 étanche**).
- **MUST** : Résolution : **≤ 0,5 °C**.
- **SHOULD** : Précision effective : **±0,5 °C** après calibration simple.
- **MUST** : Placement de la sonde défini dans le guide (zone représentative, loin de l’évaporateur et de la porte).

### Humidité (optionnel)

- **COULD** : Mesurer l’humidité relative pour monitoring (capteur type **SHT31** recommandé).
- **NOTE** : Le capteur d’humidité n’est pas utilisé pour la régulation principale dans la version initiale.

---

## Exigences de sécurité

### Électrique (230 V)

- **MUST** : Séparation stricte entre basse tension (5/12 V) et secteur (230 V).
- **MUST** : Boîtier électrique fermé, câblage sécurisé, mise à la terre.
- **MUST** : Protection électrique adaptée (disjoncteur/fusible selon installation).
- **MUST** : Utiliser un organe de coupure dimensionné pour le courant de démarrage du compresseur.

### Sécurité thermique indépendante

- **MUST** : Ajouter une sécurité matérielle indépendante du microcontrôleur :
  - thermostat mécanique en série, ou
  - limiteur de température, ou
  - dispositif équivalent coupant le compresseur en cas de dérive.

### Frigorifique

- **MUST** : Ne pas percer, ouvrir, ressouder ni recharger le circuit frigorifique dans le cadre du projet.
- **MUST** : Assurer une ventilation suffisante du condenseur (éviter l’échauffement).
- **SHOULD** : Prévoir une protection mécanique évitant tout contact/arrachement des tuyaux.

---

## Exigences de fiabilité et maintenance

- **MUST** : Le système doit pouvoir fonctionner en autonomie plusieurs jours, sans intervention.
- **MUST** : La logique de régulation doit rester opérationnelle après coupure électrique (reboot propre).
- **SHOULD** : Paramètres configurables stockés de façon persistante (EEPROM / flash) ou compilés clairement.
- **SHOULD** : Documentation des procédures de maintenance (nettoyage condenseur, dégivrage, contrôle joints, etc.).
- **COULD** : Journalisation simple (port série ou fichier) des températures et états.

---

## Exigences d’installation (enveloppe)

- **MUST** : Étanchéité correcte de l’enceinte (joints/porte) pour limiter l’entrée d’humidité.
- **MUST** : Prévoir l’évacuation de la condensation (bac, drain, ou protocole).
- **SHOULD** : Ajouter de la masse thermique (bidons d’eau) si nécessaire pour stabiliser les cycles.

---

## Exigences de performance (cibles)

Ces cibles servent d’indicateurs, pas de garantie.

- **SHOULD** : Cycle compresseur : éviter les cycles < 5 min (objectif : cycles plus longs et moins fréquents).
- **SHOULD** : Température stable en régime établi à ±1 °C autour de la consigne (selon ouvertures/charge).
- **COULD** : Consommation optimisée via mode été, hystérésis adaptée, masse thermique.

---

## Définition de “Done” (critères de validation)

Le projet est considéré comme terminé (v1.0) si :

- **MUST** : La chambre tient 4 °C (mode hiver) et 7 °C (mode été) en régime établi.
- **MUST** : Le compresseur respecte un temps minimum OFF de 3–5 min.
- **MUST** : La ventilation interne homogénéise la température (pas de zone en gel).
- **MUST** : L’interface affiche température + état + mode.
- **MUST** : Une sécurité matérielle indépendante coupe en cas de dérive.
- **MUST** : Documentation d’installation + câblage + dépannage fournie dans `docs/`.

---

## Hors périmètre

- Certification alimentaire/HACCP
- Contrôle à distance obligatoire
- Modification du circuit frigorifique
- Régulation PID avancée et optimisation fine
- Garantie de disponibilité 24/7