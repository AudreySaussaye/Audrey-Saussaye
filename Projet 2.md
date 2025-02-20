---
title: "Projet Central Park 🐿️"
date: 2
---


## **Mission : Analyse sur l'observation des écureuils à Central Park**

Cette mission a été réalisée dans le cadre de ma formation à la Wild Code School pour l'évènement Mission Data. Sur deux jours, il fallait répondre à une problématique Client.<br>
Le détail du fichier d'analyse, du rapport est consultable ici : [Projet](https://github.com/PikaChou82/AudreySaussaye/tree/main/projets/central_park)

## **Description rapide du Projet**

Le Client est le Comité de sauvegarde de Central Park ( ou *Central Park Conservancy*) C'est une organisation privée à but non lucratif fondée en 1980, et dont le CA de 2022 s'élève à $ M148.
Il nous contacte dans le but de réaliser :

> Création d’un tableau de bord interactif (rédigé en anglais).

L’utilisateur final est l’ensemble des guides de Central Park. Durant leurs visites guidées, ils souhaiteraient transmettre davantage d’informations sur les écureuils vivant dans le parc. Cet animal étant notamment apprécié des enfants, c’est une vraie opportunité d’améliorer le contenu des visites, plus particulièrement pour
des groupes scolaires.

> Le document doit être intégralement rédigé en anglais américain, langue parlée par les guides.<br>

## **Méthodologie**

La méthodologie retenue s'est fait sur un processus classique :
*    EDA
*    Dataviz
*    Rapport

## **EDA - Les enjeux**

Les analyses se sont faites via un peu plus de 3 000 observations, avec différentes colonnes qu'il a fallu décrypter, comprendre et nettoyer au besoin. Dans ce genre d'analyses, il est important de s'assurer de comprendre la définition des données d'entrées en terme de concept et d'interprétabilité. Les enjeux clés étaient notamment la partie comportementale des animaux, que ce soit concernant leurs activités mais aussi leurs réactions. On s'assure également d'avoir une certaine exhaustivité des informations dans les différentes colonnes. Ici, nous avions certaines colonnes dont le taux de valeurs manquantes était fort :

<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell1.png" alt="Description de l'image" width="100%">


Lorsque nous travaillons sur des données que nous ne maîtrisons pas, par exemple les différentes espèces d'écureuils dans le monde, il est important de se documenter afin d'avoir le niveau de qualifications attendu par notre client. Aussi, une recherche a été réalisée en parallèle sur la couleur des fourrures et leur dénomination :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell2.png" alt="Description de l'image" width="100%">



Avant d'attaquer la datavisualisation, il est recommandé de sortir les premiers indicateurs qui nous semblent pertinents afin de nous assurer de la direction à prendre dans le rapport final. Ici, il y avait un besoin de valider si les comportements pouvaient être spécifiques et s'il y avait des zones plus "propices" à l'observation des écureuils :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell3.png" alt="Description de l'image" width="100%">

<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell4.png" alt="Description de l'image" width="100%">

<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell5.png" alt="Description de l'image" width="100%">


## **DATAVIZ - Les enjeux**

La datavisualisation est l'étape clé. Elle est notre moyen de communication de nos insights et nos recommandations. Lorsqu'on livre un rapport, il faut que notre public soit capable de comprendre en 5 secondes chaque visuel. Il faut donc privilégier un style sobre, et documenter. Si l'utilisateur final se pose sans cesse la question du périmètre ou de l'unité d'un KPI, il l'abandonnera ou l'utilisera à mauvais escient.

Le visuel demandé est pour des guides touristiques, public qui n'a pas forcément l'habitude des outils que nous proposerons. Il est important de toujours veiller à se mettre "à la place de".  L'un des enjeux était de proposer une carte de visualisation. Avec les nombreuses observations réalisées, une carte de chaleur était une option, mais la multiplicité d'éléments géolocalisés peut être lourde pour certains outils. Le choix a donc été de "reproduire" Central Park pour une meilleure navigabilité :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell6.png" alt="Description de l'image" width="35%">


L'intéractivité et la ludicité peut être un bon atout pour faire adhérer et utiliser. Pour cela, les info-bulles sont très pratiques et personnalisables pour une expérience maximum :



<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell7.png" alt="Description de l'image" width="35%">


Toutes les informations, même qualitatives peuvent être mises en forme. Ainsi, sur les réactions, on peut travailler quelque chose de plus simple mais tout aussi efficace :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell8.png" alt="Description de l'image" width="100%">


Enfin, il faut toujours s'assurer de répondre correctement au besoin. L'objectif était de permettre aux guides de proposer aux touristes d'apercevoir les écureuils. Un "plan de route" intéractif a été ajouté pour que le trajet soit optimisé avec le couple gagnant écureuils / points clés :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Audrey-Saussaye/refs/heads/main/projets/central_park/images/squirell9.png" alt="Description de l'image" width="50%">


En fonction de chaque point de visite, le guide peut retrouver la zone, le point clé, et les spécificités clés des écureuils sur place.


## **Rapport de synthèse**

Le rapport final n'est pas à négliger, quand bien même le tableau de bord est compris. Il permet de resituer toutes les étapes, du besoin au livrable, afin de s'assurer que toutes les parties se sont entendues sur les objectifs, le périmètre....

C'est aussi le moment de faire les recommandations et le "guide utilisateur" pour que le tableau puisse être communiqué à tout nouvel utilisateur.
