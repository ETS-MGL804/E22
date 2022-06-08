# TP 3 - Métriques et visualisation
## MGL804 – Réalisation et maintenance de logiciel
### Date de remise : 25 juin 2022 à 23 h 59

#### Table des matières
1. [Objectifs](#objectifs)
2. [Matériel et outils à utiliser](#materiel)
	- [Outils de base](#outils)
	- [Lectures de référence recommandées](#lecture)
	- [Outils auxiliaires](#auxiliaires)
3. [Installation et préparation](#installation)
4. [Travail à réaliser](#travail)
	- [Partie 1 : Introduction (le projet ``React``)](#partie1)
	- [Partie 2 : JPacman -- prise en main pratique](#partie2)
	- [Partie 3 : JPacman -- Visualisation](#partie3)
	- [Partie 4 : Discussion sur les outils de visualisation](#partie4)
	- [Partie 5 : JPacman -- Historique de refactoring avec JPacman](#partie5)
5. [Conditions de réalisation](#conditions)
6. [Aide et discussions](#discussion)
7. [Remise](#remise)

<a name="objectifs"></a>
## 1. Objectifs
Le but de ce TP est de stimuler la discussion sur les propriétés d'un programme orienté objet bien structuré. 
Ce TP vise à vous familiariser avec les outils de maintenance et réingénierie. 
Les tâches à faire sont conçues pour stimuler votre compréhension du sujet et des outils. 
Le TP vise à explorer différentes métriques de qualité et visualisations, qui sont considérés comme des outils de base pour 
construire un plan d’action ou un rapport de qualité pour un système logiciel de données.

<a name="materiel"></a>
## 2. Matériel et outils à utiliser

<a name="outils"></a>
### Outils de base
-	[IntelliJ IDEA](https://www.jetbrains.com/idea/)  (vous pouvez utiliser Eclipse, à votre discrétion, mais cela peut nécessiter des adaptations pour le projet que nous utilisons pendant les sessions du TP)
-	Le projet [JPacman](https://github.com/ouniali/jpacman).
-	Le projet [React](https://github.com/facebook/react).
-	[CodeScene](https://codescene.io/) : pas d’installation requise, mais il nécessite un compte GitHub. L'intégration de cet outil avec GitHub lui permet de visualiser vos répertoires de code. La partie dette technique (Technical Debt) affiche les cibles de refactoring. Les codes biomarqueurs (Code Biomarkers) montrent une analyse plus détaillée des odeurs (code smells), mais ce n'est disponible que pour les abonnements payants.
- [Understand](https://scitools.com/) : Un outil puissant pour la visualisation, l'analyse et la mesure de logiciel. Vous pouvez avoir une licence gratuite avec votre compte de l’ETS via ce [lien](https://scitools.com/student/). Le tutoriel [suivant](https://www.youtube.com/watch?v=GB7cbdgJ2j8&t=2037s) fournira une bonne prise en main pour commencer à utiliser l'outil.
- [JsCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) : outil de visualisation de logiciel en 3D. JsCity est une version de [CodeCity](https://wettel.github.io/codecity.html) pour analyser du code JavaScript.
- [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner) : Un API/outil qui détecte l’historique des opérations de refactoring appliquées dans un projet (Java).



<a name="lecture"></a>
### Lectures de référence recommandées
-	Chapitre 2 « First Contact » du livre Object-Oriented Reengineering Patterns (disponible en PDF sous l’onglet Références dans Moodle) : page 39 (« Where do I start? »).

<a name="auxiliaires"></a>
### Outils auxiliaires

Les outils auxiliaires **ne sont pas nécessaires** pour la réalisation du TP, mais ils peuvent être utiles pour obtenir des informations supplémentaires (ou des alternatives) sur un projet. Vous pouvez les utiliser à votre discrétion.


- [CodeCity](https://wettel.github.io/codecity.html) : Un outil de visualisation de logiciels (seulement sur Windows ou Mac. Possible sous Linux apres installation de VisualWorks pour Smalltalk). Des examples des visualisations et des fonctionnalités peuvent être trouvés [ici](http://wettel.github.io/codecity-tutorials.html).
- [Moose](http://www.moosetechnology.org/) : un outil avancé pour l'analyse et les mesures de logiciels.
- [Softwarenaut](http://scg.unibe.ch/softwarenaut) : un outil de recouvrement d'architecture (uniquement sur Windows ou Mac). Cet outil ne nécessite pas Eclipse. Un aperçu de ses fonctionnalités peut être trouvé [ici](http://vimeo.com/62767181). L'outil peut être téléchargé [ici](http://scg.unibe.ch/download/softwarenaut/).
- [Eclipse Metrics](http://metrics2.sourceforge.net/) : Ancien plugin eclipse pour extraire les métriques. Intéressant comme concept mais devient obsolete.


<a name="installation"></a>
## 3. Installation et préparation

Pour faire ce TP, préparer les outils de base indiqués dans la [section 2](#outils) (pas les [outils auxiliaires](#auxiliaires), ils sont optionnels et ne seront pas utilisés dans ce TP) 

Téléchargez/Clonez la version du projet JPacman au commit suivant:
- ID : [518223dbe2e47a83032fecf7632a89bdb25b7ed9](https://github.com/ouniali/jpacman/tree/518223dbe2e47a83032fecf7632a89bdb25b7ed9)
- Date : 24/3/2020
- Nom: Update Readme.md

Assurez-vous de suivre l'installation et les étapes décrites dans le [TP #2](https://github.com/MGL804H22/TP/blob/main/TP%202/TP%202%20-%20Assistants%20de%20Refactoring.md) (Assistants de refactoring), si vous ne l'aviez pas fait. En résumé, les étapes consistent à :
- Installer [IntelliJ IDEA](https://www.jetbrains.com/idea/), 
- Faire un fork du projet [JPacman](https://github.com/ouniali/jpacman) sur votre compte Github,
- Faire le build (construire) et l'exécuter,
- Importer votre projet sur [CodeScene](https://codescene.io/).


<a name="travail"></a>
## 4. Travail à réaliser
<a name="partie1"></a>
### Partie 1 : Introduction (le projet ``React``)

Cette première tâche a deux objectifs : <br/>
(i) vous aider à vous familiariser avec l'interface de CodeScene ;<br/>
(ii) observer si toutes les visualisations sont utiles pour la maintenance.

Visitez le site Web de [CodeScene](https://codescene.com/) et cliquez sur les examples illustratifs fournis ([Demo](https://codescene.io/showcase)). Ce sont des exemples (à partir d'une version complète de CodeScene et pas seulement de la version gratuite que nous utilisons) de projets analysés par CodeScene. Sélectionnez le projet ``React``.

Visitez le site Web de [JsCity](https://github.com/ASERG-UFMG/JSCity/wiki/JSCITY) et regardez les exemples. Vous pouvez d'abord sélectionner un exemple simple pour vous familiariser. Par la suite, sélectionnez le projet ``React`` et visualisez le (soyez patient car cela peut prendre un certain temps).

Ensuite, visitez le site Web de l'outil [Understand](https://scitools.com/) et cliquez sur les examples illustratifs fournis pour vous familiariser avec l'outil. Ensuite, télécharger/clonez, puis importez la dernière version du projet [React](https://github.com/facebook/react) avec l'outil Understand.


**Questions :**
1. Pour chacun des 3 outils, faire 2 captures d'écrans de la visualisation que vous jugez plus pertinentes pour la compréhension du programme React (en total : 2 captures d'écran * 3 outils = 6). Copiez les visualisations choisies dans votre rapport et justifiez briévement la pertinence de chacune.
2. Comment vous trouvez l'utilité de ces trois outils de visualisation pour la compréhension de logiciel ? Pouvez-vous en extraire des informations intéressantes sur le projet visualisé ?
3. Quelle visualisation serait-elle la plus utile pour planifier les activités de refactoring ? Indiquez le nom de l'outil et le type de la visualisation spécifique avec un (ou des) capture(s) d'écran dans votre rapport de TP.

<a name="partie2"></a>
### Partie 2 : JPacman -- prise en main pratique

Pour la deuxième tâche, l'objectif est de commencer à se familiariser avec le code source de [JPacman](https://github.com/ouniali/jpacman). Téléchargez/clonez le référentiel et exécutez l'application dans votre IDE. Maintenant, regardez le code source et essayez de comprendre sa structure interne (packages, classes, méthodes, variables, etc.). Dans le dossier ``docs/uml``, il y a deux diagrammes UML simplifiés.

Comme indiqué dans le livre (OORP, p.39), il s'agit de votre « premier contact » avec le logiciel qui nécessite des activités de maintenance. Comme souvent, nous nous demandons « comment commencer ? » (« Where do I start ? ») (OORP, p. 40).

En effet, JPacman est une implémentation Java qui est censée répliquer le jeu [Pacman original](https://en.wikipedia.org/wiki/Pac-Man).

**Questions :**
1. Quelles fonctionnalités manquent dans Jpacman (par rapport à la version originale) ?
2. Est-il possible d'implémenter ces fonctionnalités dès maintenant ou devrions-nous restructurer le projet pour faciliter l'ajout des nouvelles fonctionnalités ? Pourquoi ? 

<a name="partie3"></a>
### Partie 3 : JPacman -- Visualisation

La troisième partie consiste à utiliser nos outils de visualisation de choix (CodeScene et Understand) pour identifier d'éventuelles cibles de réingénierie dans JPacman. Une des approches importantes de réingénierie et maintenance consiste à étudier les entités exceptionnelles.

#### Understand
En commençant par Understand, générez une visualisation de type "TreeMap" en se basant sur la métrique ``CountLine`` pour la taille du map (option ``Map Size``) et la métrique ``MaxCyclomatic`` pour la couleur (option ``Map Color to``). Veuillez vous référer au menu *Metrics* -> *Metrics Treemap*.

**Questions :**
1. Générer la figure de visualisation et copiez-la dans votre rapport de TP.
2. Quelle est la classe la plus volumineuse dans JPacman ?
3. Quelle est la classe la plus complexe dans JPacman ?
4. Quelles sont les 8 méthodes les plus complexes dans JPacman ?
5. Quelles sont les 3 méthodes les plus larges dans JPacman ?

**NB :** Les tests bien qu'ils font partie du projet ne sont pas considérés comme des méthodes.
**NB :** Attention, la métrique MaxCyclomatique n'est pas équivalente à la métrique complexité cyclométrique de McCabe.

#### CodeScene
Maintenant, en utilisant CodeScene, répondez aux questions suivantes.

**Questions :**<br/>
6. Pouvez-vous identifier les artefacts qui semblent être exceptionnels ? <br/>
7. Ces artefacts pourraient-ils bénéficier de refactoring ? Si oui, sélectionnez trois artefacts de votre choix, et identifiez pour chaque artefact, une différente solution de refactoring à appliquer (identifiez seulement, sans les appliquer dans le code) ? Une "solution" de refactoring peut consister en une ou plusieurs opérations de refactoring. Utilisez au moins trois opérations de refactoring différentes. <br/>
8. Comment les mesures de qualité (complexité, couplage, taille) de ces artefacts sont-elles comparées aux autres ?<br/>

**NB :** Un artéfact exceptionnel est un artéfact (classe, méthode, package, etc.) qui est une exception à comparer aux autres artéfacts. Elle ne ressemble pas aux autres, donc qui n'est pas standard ou _normal_.

<a name="partie4"></a>
### Partie 4 : Discussion sur les outils
Dans ce TP, nous avons utilisé les métriques de qualité et la visualisation, démontrant leur efficacité lors de la maintenance, pour la compréhension initiale.

**Questions :**
1.	Est-ce que les outils de mesure de qualité et de visualisation utilisés dans ce TP ont pu fournir les informations requises pour assister à la compréhension et la maintenance de JPacman ? 
2.	Lequel des deux outils de visualisation (CodeScene et Understand) préférez-vous pour vous assister à la maintenance ? Pourquoi ? 
3.	Y a-t-il des situations particulières pour les utiliser ou ne pas les utiliser ? 
4.	Pouvez-vous envisager d'autres utilisations de ces outils pour d'autres tâches de maintenance ?


<a name="partie5"></a> 
### Partie 5 : JPacman -- Historique de refactoring avec JPacman

Dans cette partie, nous nous intéressons à l'historique des changements, en particulier à l'historique des refactorings appliqués par les développeurs, sans passer par outil de visualistion.
Nous utilisons l'outil [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner) qui permet de parcourir les commits et en extraire les opérations de refctoring appliqués dans un projet donné.

En se basant sur la documentation de l'outil [RefactoringMiner](https://github.com/tsantalis/RefactoringMiner), exécutez l'outil avec le projet [JPacman de hscrocha](https://github.com/hscrocha/jpacman) pour en extraire l'historique de refactoring.

**NB.** Regarder que les commits qui sont avant le 12 avril 2021. Donc ignorer ceux fait après.

**Questions**
1. Prenez une capture d'écran de votre code qui implémente RefactoringMiner et remettez le fichier.
2. Quelles sont les 3 opérations de refactoring les plus appliquées ?
3. Quelle est la classe la plus refactorisée (c-a-d, elle apparait dans des opérations de refactoring) ? Est ce que les outils de visualisation utilisés donnent de l'information utile pour assister au refactoring de cette classe ? Justifier votre réponse.
4. (Question Bonus) Quel est le développeur le plus actif en application de refactoring ?

**NB.** Vous pouvez implémenter votre script pour lire l'output générer par RefactoringMiner pour répondre aux questions.
**NB.** Assurez-vous de prendre la bonne version de JPacman (celui du lien donner ici et non le JPacman fork du professeur ou le vôtre)

<a name="conditions"></a>
## 5. Conditions de réalisation
Le travail est à effectuer en équipes de 3 étudiants au maximum.

<a name="discussion"></a>
## 6. Aide et discussions
Vous êtes encouragés à discuter du TP et à poser vos questions en utilisant le forum créé à cette fin sur Moodle ou sur Discord. Les membres de chaque équipe sont encouragés à utiliser les channels privés (textuel et vocal) créés pour leur équipe sur Discord pour discuter et travailler en équipe sur les différentes activités du TP.

<a name="remise"></a>
## 7. Remise
Le travail doit être remis électroniquement sur Moodle au plus tard le **25 juin à 23 h 59**. Vous devrez remettre une archive ``zip`` ou ``tar.gz`` contenant tous les fichiers, ainsi qu’un fichier texte indiquant le nom de tous les membres de l’équipe ayant contribué à la réalisation du travail. 
Une seule remise électronique est nécessaire par équipe. Remettez aussi individuellement le tableau de contribution tel vu dans le TP précédent.
Pour faciliter la correction, vous devez nommer votre dossier de la remise de la façon suivante :

```
MGL804E2022-TP3-EquipeYY-CodePermanent1_CodePermanent2_CodePermanent3
```

Et votre rapport ainsi : 
```
EquipeYY-Rapport.pdf
```
