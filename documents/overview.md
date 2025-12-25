# Overview

## Présentation générale

Ce projet vise à concevoir une **chambre froide positive artisanale**, d’environ 7 m³, utilisant un **groupe froid de congélateur domestique recyclé**, piloté par un contrôleur électronique personnalisé.

L’objectif n’est pas de reproduire une chambre froide industrielle certifiée, mais de créer un système :
- fiable sur la durée,
- compréhensible,
- réparable,
- peu énergivore,
- tolérant aux absences,
- adapté à un usage non critique,
- reutilisation a maximum de d'équipements de récupérations

---

## Philosophie du projet

Ce projet repose sur plusieurs principes forts :

### Simplicité avant sophistication
Le système doit rester compréhensible sans outils propriétaires ni dépendances complexes.  
Chaque sous-système doit pouvoir être diagnostiqué ou remplacé indépendamment.

### Robustesse plutôt que performance
La stabilité thermique, la longévité du compresseur et la sécurité passent avant la précision extrême.

### Récupération et réemploi
Le projet privilégie :
- la récupération de matériel fonctionnel,
- l’usage de composants standards,
- la limitation des pièces spécifiques.

### Contrôle local et autonomie
Le système doit fonctionner :
- sans cloud,
- sans connexion internet,
- sans service externe,
- sans dépendance logicielle fragile.

---

## Portée du projet

### Inclus
- Pilotage du compresseur via un contrôleur logique
- Régulation de température simple (mode été / hiver)
- Gestion de l’hystérésis
- Temporisation anti-redémarrage
- Ventilation interne
- Surveillance de température
- Dégivrage passif
- Interface locale simple
- Documentation complète

### Exclu volontairement
- Régulation PID avancée
- Gestion HACCP certifiée
- Traçabilité réglementaire
- Supervision cloud obligatoire
- Contrôle à distance critique
- Automates industriels propriétaires

---

## Description fonctionnelle globale

Le système est composé de quatre blocs principaux :

1. **Bloc frigorifique**
   - compresseur
   - condenseur
   - évaporateur
   - circuit frigorifique fermé et intact

2. **Bloc de commande**
   - microcontrôleur
   - relais / contacteur
   - alimentation basse tension
   - sécurité thermique indépendante

3. **Bloc capteurs**
   - sonde de température principale
   - éventuellement capteur d’humidité
   - capteurs positionnés hors zones perturbées

4. **Bloc diffusion thermique**
   - ventilation interne
   - circulation d’air douce et homogène

---

## Modes de fonctionnement

### Mode hiver
- consigne : 4 °C
- utilisé lorsque la température ambiante est basse
- priorité à la conservation stable

### Mode été
- consigne : 7 °C
- utilisé lorsque la température extérieure augmente
- réduit la sollicitation du compresseur

Le changement de mode est manuel via un bouton ou un sélecteur.

---

## Logique de régulation (vue d’ensemble)

- Lecture périodique de la température
- Comparaison à la consigne active
- Application d’une hystérésis
- Gestion du temps minimum OFF et ON
- Démarrage ou arrêt du compresseur
- Gestion indépendante de la ventilation
- Séquences de dégivrage passif planifiées

---

## Contraintes techniques connues

- le compresseur ne doit jamais redémarrer immédiatement après un arrêt
- le circuit frigorifique ne doit pas être modifié
- la ventilation ne doit pas provoquer de sur-refroidissement local
- la condensation doit pouvoir s’évacuer
- l’électronique doit être isolée du 230 V

---

## Hypothèses d’utilisation

- les produits introduits sont déjà refroidis
- la porte n’est pas ouverte fréquemment
- la charge thermique est modérée
- le local est tempéré (garage)
- les panneaux isolants sont continus et étanches

---

## Limites assumées

- précision limitée à ±1 °C
- pas de redondance électronique complète
- pas de certification sanitaire
- pas de garantie de disponibilité 24/7
- pas de gestion active de l’humidité

---

## Objectif final

Fournir une chambre froide :
- simple à comprendre,
- stable dans le temps,
- silencieuse,
- économique,
- facile à réparer,
- documentée,

permettant d’expérimenter, stocker et apprendre sans dépendre d’un système industriel fermé.

---

## Philosophie de maintenance

- préférer les composants standards
- documenter chaque modification
- tester avant d’automatiser
- garder un fonctionnement dégradé possible
- privilégier la lisibilité à la complexité