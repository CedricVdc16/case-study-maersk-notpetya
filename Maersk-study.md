# Rapport – Analyse de la cyberattaque NotPetya chez Maersk (2017)
## Sommaire
- [1. Introduction](#1-introduction)
- [2. Contexte et nature de l'attaque](#2-contexte-et-nature-de-lattaque)
  - [2.1 Le malware NotPetya](#21-le-malware-notpetya)
  - [2.2 La culture de sécurité avant l'attaque](#22-la-culture-de-sécurité-avant-lattaque)
- [3. Déroulement et impact immédiat](#3-déroulement-et-impact-immédiat)
  - [3.1 La “Golden Hour”](#31-la-golden-hour)
  - [3.2 Le “miracle de Lagos”](#32-le-miracle-de-lagos)
- [4. Conséquences opérationnelles](#4-conséquences-opérationnelles)
  - [4.1 Paralysie mondiale](#41-paralysie-mondiale)
  - [4.2 Shadow IT et reconstruction](#42-shadow-it-et-reconstruction)
- [5. Gestion de crise et plan de réponse](#5-gestion-de-crise-et-plan-de-réponse)
  - [5.1 Plan initial et improvisation](#51-plan-initial-et-improvisation)
  - [5.2 Reconstruction technique](#52-reconstruction-technique)
- [6. De l'asset-focused-au-data-focused](#6-de-lasset-focused-au-data-focused)
- [7. Leçons apprises](#7-leçons-apprises)
  - [7.1 Culture et gouvernance](#71-culture-et-gouvernance)
  - [7.2 Technique et organisation](#72-technique-et-organisation)
  - [7.3 Vers une cybersécurité de résilience](#73-vers-une-cybersécurité-de-résilience)
- [8. Conclusion](#8-conclusion)
- [9. Sources](#9-sources)


## 1. Introduction

Le 27 juin 2017, le groupe A.P. Møller – Maersk, leader mondial du transport maritime de conteneurs, a été frappé par l’une des cyberattaques les plus destructrices de l’histoire récente. Le malware NotPetya, initialement ciblé contre l’Ukraine, s’est propagé à l’échelle mondiale, touchant des entreprises de tous secteurs. Maersk, du fait de son réseau IT très intégré, a été l’une des victimes les plus durement atteintes.
L’incident a paralysé ses opérations dans plus de 130 pays, provoqué une perte estimée à près de 300 millions USD. Il a également mis en lumière à la fois les failles et la résilience d’un géant industriel confronté à une crise numérique totale.
Ce rapport analyse l’attaque, la réponse de Maersk et les leçons clés à en tirer pour la cybersécurité moderne.

## 2. Contexte et nature de l’attaque
### 2.1 Le malware NotPetya

Déguisé en ransomware, NotPetya était en réalité un wiper, conçu pour détruire les systèmes plutôt que d’extorquer une rançon. Son vecteur initial : une mise à jour compromise du logiciel fiscal ukrainien M.E.Doc, utilisé par certaines filiales de Maersk opérant localement.
Une fois introduit, le malware a exploité plusieurs techniques (EternalBlue, Mimikatz, propagation SMB) pour se répandre latéralement sur le réseau interne en quelques minutes.

### 2.2 La culture de sécurité avant l’attaque

Avant 2017, la cybersécurité chez Maersk était perçue comme un support technique, non comme un pilier stratégique. Les priorités portaient sur la performance opérationnelle, pas sur la résilience. 

- Peu de segmentation réseau
- Gestion des identités et privilèges insuffisante
- Multiplication d’outils non officiels (Shadow IT)
- Plans de continuité peu (ou pas) testés et rarement mis à jour

En clair, l’entreprise avait une culture de sécurité réactive, pas préventive.

## 3. Déroulement et impact immédiat
### 3.1 La “Golden Hour”

La vitesse de propagation a rendu toute réaction structurée pratiquement impossible.
Le 27 juin à 14 h, les premiers redémarrages en chaîne sont observés. Moins d’une heure plus tard, tout le réseau mondial est paralysé.

- Environ 45 000 postes et 4 000 serveurs détruits.
- Tous les contrôleurs de domaine (Active Directory) effacés.
- Les sauvegardes en ligne inaccessibles ou corrompues.

Le CISO résumera plus tard : 
    
    « AD is king » 

sans Active Directory, plus rien ne fonctionne.

### 3.2 Le “miracle de Lagos”

Un seul serveur AD, situé à Lagos (Nigeria), avait survécu grâce à une coupure de courant. C’est à partir de ce contrôleur isolé que l’entreprise a pu reconstruire son identité numérique. Ce hasard a littéralement sauvé Maersk.

## 4. Conséquences opérationnelles
### 4.1 Paralysie mondiale

Les terminaux portuaires, entrepôts et systèmes de réservation ont cessé de fonctionner. Les équipes sont revenues à des procédures papier, avec des communications via WhatsApp, téléphones personnels et radios. Des conteneurs frigorifiques sont restés bloqués sans suivi de température, menaçant la chaîne du froid et des millions de dollars de marchandises.

### 4.2 Shadow IT et reconstruction

Le redémarrage a révélé un problème sous-jacent : le Shadow IT.
De nombreux outils internes (macros Excel, scripts, mini-applications locales) avaient été créés par des employés sans documentation officielle. Résultat : certains systèmes pouvaient être restaurés côté serveur, mais restaient inutilisables côté client, faute de connaître leur fonctionnement réel. Le CISO cite cet aspect comme une des leçons majeures :

    “Ce que tu ne documentes pas, tu le perds.”


## 5. Gestion de crise et plan de réponse
### 5.1 Plan initial et improvisation

Maersk ne disposait pas d’un plan de réponse à incident structuré. Les procédures existaient, mais dispersées par service, sans gouvernance centralisée.
La réaction a donc reposé sur l’improvisation, la coordination humaine et le bon sens. Les réseaux ont été déconnectés pour contenir la propagation, et une cellule de crise 24/7 a été mise en place. Les échanges opérationnels se sont fait… sur WhatsApp. C’est cet outil non prévu qui a permis de coordonner les équipes globalement.

### 5.2 Reconstruction technique

- Active Directory reconstruit en 9 jours (objectif futur : 24 h).
- 2000 laptops réinstallés en 49 jours.
- Hiérarchisation des priorités : AD → réseau → systèmes portuaires → booking clients.
- Microsoft, IBM et d’autres partenaires se sont mobilisés bénévolement pour aider Maersk à redémarrer.

## 6. De l’asset-focused au data-focused

Avant 2017, la cybersécurité Maersk reposait sur la protection des actifs physiques : serveurs, réseaux, équipements. Après l’attaque, le groupe a basculé vers une approche data-focused, centrée sur la valeur des données et des identités :

- Priorité à la protection des accès et identités privilégiées ;
- Application stricte du modèle CIA (Confidentiality – Integrity – Availability) ;
- Intégration d’un renseignement cyber pour surveiller la circulation de données sensibles sur le dark web ;
- Adoption du principe : « Protect the data, not just the device. »

## 7. Leçons apprises
### 7.1 Culture et gouvernance

La cybersécurité doit être portée par la direction, pas seulement l’IT. La communication transparente de Maersk a été un atout : clients et partenaires ont soutenu la reconstruction. Après la crise, le groupe a instauré 5 principes directeurs :

- Everyone is responsible for security.
- Risk accountability.
- Trust through transparency.
- Resilience = react + rebuild.
- Security is a benefit, not a burden.

### 7.2 Technique et organisation

- Segmentation réseau réelle et supervision centralisée.
- Sauvegardes isolées et testées régulièrement.
- Plan de continuité incluant des scénarios “papier”.
- Shadow IT documenté ou intégré dans le patrimoine officiel.
- Exercices de crise réguliers, comme on le ferait pour la sécurité physique.

### 7.3 Vers une cybersécurité de résilience

Maersk a compris qu’une protection totale est illusoire : 

    “100 % protection does not exist.” 

Elle a donc investi dans la reconstruction rapide, le confinement, et une culture du risque maîtrisé. L’entreprise a aussi fédéré IT et OT (grues, entrepôts, automatisation) dans une vision commune : la sécurité de la donnée et de l’accès vaut pour toute la chaîne.

En parallèle, Maersk a mis en place une véritable équipe de red teaming interne, composée en partie de jeunes profils sélectionnés pour leur capacité à penser “hors cadre”. Le CISO insiste sur l’importance de cette “lateral thinking team”, chargée d’anticiper les scénarios inattendus plutôt que de se limiter aux attaques classiques déjà connues. Leur rôle est de tester les environnements, de chercher les chemins détournés qu’un attaquant pourrait emprunter, et de challenger en continu les décisions techniques.
Cette approche a permis à Maersk de dépasser une vision purement défensive et de développer une culture proactive, où la question n’est plus “que faire si cela arrive ?”, mais bien “qu’est-ce que nous n’avons pas encore imaginé ?”.

## 8. Conclusion

L’attaque NotPetya a agi comme un électrochoc. Elle a révélé à Maersk — et à toute l’industrie — qu’aucune infrastructure n’est isolée du risque global. En l’espace d’une heure, une entreprise contrôlant 20 % du transport maritime mondial s’est retrouvée à l’arrêt complet. Mais en neuf jours, elle a retrouvé son identité numérique. Cette réussite tient moins à la technologie qu’à la chance, la mobilisation humaine, à la coopération et à une volonté de transparence rare. Depuis, Maersk est passée d’une sécurité subie à une sécurité stratégique, axée sur la donnée, la confiance et la résilience. L’incident reste une référence incontournable : un rappel brutal que la cybersécurité n’est pas qu’une affaire de firewalls, mais avant tout de culture, d’humilité et de préparation. En résumé, l’attaque NotPetya a démontré que la combinaison d’un réseau très intégré, d’un Active Directory centralisé et d’un manque de segmentation peut transformer une infection locale en crise mondiale.

## 9. Sources
En plus de la [video - youtube](https://www.youtube.com/watch?v=wQ8HIjkEe9o) j'ai effectué quelques recherches sur le net voici une liste non-exhaustive des sites consultés

- [LeMagIT.fr](https://www.lemagit.fr/etude/NotPetya-les-enseignements-tires-chez-Maersk)
- [CyberCover.fr](https://www.cyber-cover.fr/cyber-documentation/cyber-criminalite/cybercriminalite-notpetya-le-malware-a-10-milliards-de-dollars)
- [Le Monde Informatique](https://www.lemondeinformatique.fr/actualites/lire-l-impact-de-notpetya-sur-maersk-pourrait-s-elever-a-300-m$-69075.html)
- [SOSInteligence.co.uk](https://sosintel.co.uk/case-study-maersks-response-to-notpetya-how-cybersecurity-best-practices-mitigated-a-major-cyberattack/)


---

_Travail remis dans le cadre du cours Elements de réponse de cybersécurité – Année 2025-2026_  
_Mots-clés : NotPetya, Maersk, cybersécurité, résilience_
