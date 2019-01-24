# Projet_Julia

Ce projet fonctionne sous **Java 11**.
Le sujet du complet du projet ce trouve à la racine sous le nom de sujet.pdf

## Lancement

Le fichier Julia.jar ce situe à la racine du projet, il permet d'éxecuter celui-ci.

Pour lancer le projet, ce placer via un terminal à la racine de celui-ci (là où Julia.jar ce trouve) et executer la commande suivante :  
`java --module-path ./javafx-sdk-11.0.1/lib --add-modules=javafx.controls,javafx.fxml -jar Julia.jar graphique`

## Architecture

L'arborescence du projet est la suivante. Elle s'inspire du modèle MVC :

```sh
    src
├── model
│   ├── Calculus.java
│   ├── Complex.java
│   ├── Grid.java
│   ├── Julia.java
│   ├── Mandelbrot.java
│   ├── ModelTest.java
│   └── PolynomialFactory.java
└── view
    ├── command
    │   └── TerminalMain.java
    ├── graphic
    │   ├── FunctionBox.java
    │   ├── JuliaBox.java
    │   ├── MainStage.java
    │   └── MandelbrotBox.java
    ├── ImageSaver.java
    └── lib
        ├── error.png
        ├── play-button-1.png
        ├── plus.png
        └── stop-1.png
```

## Implémentations

### Ensembles de Julia et Mandelbrot

Les ensembles de Julia ont été implémentés dans le package _model_ au travers de la classe abstraite `Calculus`. Celle-ci est
définie comme la classe servant à calculer la couleur d'un pixel via le nombre d'itérations, la fonction, et la limite. Le paramètre d'itération est toujours modifiable pour les deux ensembles. La fonction polynôme est modifiable pour Julia dans les modes graphique et interactif. La limite n'est modifiable dans aucun mode, faute de preuve mathématique, mais la classe Calculus est conçue pour pouvoir la modifier si besoin. <br />

Pour les deux ensembles, il est possible d'effectuer le calcul en mode normal avec un nombre fixe d'itérations ou en mode infini.
Il est possible de modifier le zoom ainsi que la position de l'origine dans le repère orthonormé.

### Multhreading

Tous les calculs sont faits en multithread. Ils utilisent le maximum de coeurs moins un qui s'occupera de gérer l'interface graphique ou d'autres ressources. Les calculs ne peuvent être effectués en monothread.

### Mode infini

Il est possible de lancer un calcul qui s'arrête quand la fonction diverge ou est sûr de converger. Pour cela, on vérifie si le module de la différence est supérieur à 1 ou si l'on a trouvé un point fixe. Il est possible d'arrêter le calcul grâce au bouton stop.

## Copyrights

© BELLO MARAIS

auteurs :

- Pablito BELLO
- Etienne MARAIS
