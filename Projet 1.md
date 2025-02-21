---
title: "Projet COVID-19 🏥"
date: 1
---


## **Mission : Analyse sur la santé et le COVID-19**

Cette mission a été réalisée dans un cadre personnel, dans le but de structuer une démarche complète EDA - Machine Learning.
Le détail du fichier d’analyse, du rapport est consultable ici : [Projet](https://github.com/AudreySaussaye/Projets/tree/main/covid_19)


## **Description rapide du Projet**

L'objectif de ce projet est l'analyse de données de santé, dans le cadre de résultats de patients afin de construire un modèle de prédiction sur la positivté d'un patient au Covid 19.

## **Méthodologie**

La méthodologie retenue s'est fait sur un processus classique :
*    EDA
*    Machine Learning
*    Choix du Modèle

## **EDA - Les enjeux**

L'enjeu principal est de faibiliser au maximum l'interprétation du jeu de données, comprendre les relations entre les variables afin de proposer un modèle solide de prédiction. Nous sommes sur des données de santé, il y a toujours une partie "sensible" à intégrer sur la bonne qualité de l'analyse afin de ne pas faire de prédictions qui pourraient impacter la santé publique (même si nous sommes sur un projet personnel 😉, toujours intégrer la notion de perfection, ça fait partie des bons réflexes). 

Le fichier de départ contenait 111 colonnes, avec diverses informations de santé pour quelques 5 000 patients.<br>
Premier step lors de l'EDA : l'analyse de forme, les types de colonnes, les valeurs manquantes et l'identification de notre cible :

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid1.png" alt="Description de l'image" width="35%"> <img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid2.png" alt="Description de l'image" width="35%">



<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid3.png" alt="Description de l'image" width="100%">



Une fois la partie "forme" réalisée, on passe au "fond" afin de comprendre les différentes variables, examiner leur comportement avec la cible ou entre elles, etc. Ici nous avions un fort taux de valeurs manquantes (entre 76, 89 et plus de 90%). Il a fallu identifier des "clusters" de type de variable, et séparer les jeux afin de voir si certaines catégories de colonnes avaient plus d'appétence que d'autres à noter une corrélation avec les tests Covid.

Certaines colonnes ont marqué quelques différences entre "Positif" et "Négatif", d'autres, comme l'âge en quantile, ont marqué une forte distinction, mais malheureusement inexploitables, du fait de la non traduction des catégories.


<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid4.png" alt="Description de l'image" width="35%"> <img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid5.png" alt="Description de l'image" width="35%">


C'est une **étape clé** en data analyse : ne jamais inventer une interprétation pour la faire coller à nos intuitions. Malgré la relation significative de l'absence de COVID sur certaines tranches, ou la progression sur d'autres, il nous faut abandonner cette variable pour la suite.

Les corrélations entre les autres virus et le Covid ont été testées pour valider les "doubles maladies" :

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid6.png" alt="Description de l'image" width="35%"> <img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid7.png" alt="Description de l'image" width="35%">


Après avoir analysé les différentes colonnes, on a l'intuition que certaines colonnes sont plus clés que d'autres, notamment les taux de Leucocytes, Monocytes, etc.
Lorsque nous sommes confrontés à une quantité importante de variables à tester, on peut effectuer le test de student, qui nous permet de valider certaines hypothèses.

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid8.png" alt="Description de l'image" width="100%">


Le test de student a rejeté l'hypothèse d'un taux équivalent de certaines analyses quel que soit le résultat Covid, validant ainsi nos intuitions.
Tous les éléments sont analysés, on peut passer à la partie du Machine Learning.

## **Machine learning - Les enjeux**

L'enjeu du machine learning est bien évidemment de trouver le modèle le plus robuste et le plus performant à prédire notre cible (ici, le patient est-il atteint du Covid 19).<br>
La prédiction étant "Oui" ou "Non", nous sommes sur un modèle de classification. En machine learning, il est courant de tester plusieurs modèles, afin de s'approcher du modèle idéal. 

L'objectif n'est pas non plus de partir directement sur un modèle trop lourd, parfois il faut commencer simplement et faire évoluer au besoin pour optimiser notre facteur temps.

Ici, le premier "model test" s'est fait sur un DecisionTreeClassifier. Bien entendu, il faut préparer les données, créer des jeux d'entraînement et de test afin d'entraîner le modèle sur une partie du Dataset et le valider sur la deuxième de manière complètement indépendante (TrainTestSplit).

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid9.png" alt="Description de l'image" width="100%">

Les scores n'étant pas très bons (le modèle avait du mal à repérer les positifs), il a fallu faire évoluer le modèle. Pour le faire évoluer, il faut comprendre comment se comporte le modèle. Le "Learning Curve" a rapidement montré un surapprentissage : le modèle était trop parfaitement collé aux données d'entraînement,  ne sachant pas interpréter de nouvelles données :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid10.png" alt="Description de l'image" width="35%">


Après plusieurs tests et une analyse des coefficients d'importance dans le modèle, le constat était assez clair : certaines colonnes n'ont pas d'intérêt, et le modèle, quel que soit les paramètres choisis, ne satisfait pas nos conditions :

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid11.png" alt="Description de l'image" width="35%">


L'optimisation automatisée est un bon outil pour valider et croiser efficacement différents modèles. 
Après avoir défini quelques modèles, ainsi que des hyperparamètres associés (ici RandomForest, AdaBoost, SVM et KNN), une légère optimisation a permis d'isoler deux modèles plus performants, SVM et KNN, avec toutefois de meilleurs résultats pour SVM.

## **Choix du Modèle**

Les SVM sont un outil puissant pour la classification et la régression. Ils excellent dans la recherche de séparations claires entre les données, même si celles-ci sont complexes. <br>
On tente donc de trouver, pour ce modèle, la combinaison idéale :


<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid12.png" alt="Description de l'image" width="35%">


Après un GridSearch, nous obtenons :

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid13.png" alt="Description de l'image" width="35%">


Suivant le cas, nous pouvons essayer de trouver le meilleur compromis précision / rappel :

<img src="https://raw.githubusercontent.com/AudreySaussaye/Projets/refs/heads/main/covid_19/images/covid14.png" alt="Description de l'image" width="35%">

Nous avons privilégié le recall dans nos scores. En effet, le recall minimise les faux négatifs, ce qui est utile dans notre cas précis (sujet de santé, il faut nous assurer de ne pas rater un cas qui pourrait s'avérer sévère). 
