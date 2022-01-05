<h1><center>Projet: Détection de la démence</center></h1>

<h1> 1. Définition de l'objectif</h1>

Mettre en place un modèle prédictif chargé de détecter la présence de démence chez un patient, en fonction des données cliniques disponibles.

<h1> 2. Analyse exploratoire de données (EDA)</h1>
<h2><center>Analyse de forme du dataset</center></h2>

- **Identification de la target** : Group
- **Nombre de lignes et de colonnnes** : 73 lignes et 15 colonnes
- **Type de variables** : 
   - Variables de type float64: 5 
   - Variables de type int64: 5
   - Variables de type object: 5
- **Identification des valeurs manquantes** : 
   - 19 valeurs manquantes pour la variable SES
   - 2 valeurs manquantes pour la variable MMSE

<h2><center>Analyse de fond du dataset</center></h2>

- **Variables supprimées**: 
    - Subject ID: identifiant du patient
    - MRI ID: identifiant de l'IRM du patient
    - Hand: main dominante, variable peu pertinente car tous les patients sont droitiers. 
    
- **Analyse de la variable à expliquer**:
- **Variable qualitatives**:
    - Group:  en fonction de leur état cognitif, les patients sont regroupés dans 3 classes.
       - Demented(souffre de démence)
       - Nondemented(pas de démence)
       - Converted(démence en cours de développement)

On observe un déséquilibre de classe, 50% de patients ne souffrant pas de démence, 40% de patients souffrant de démence et 10% de patients qui développent une démence, au cours de l'étude.
         
- **Analyse des variables explicatives**:
 - **Variables quantitatives**: 
     - nWBV: Volume total du cerveau, normalisé 
     - ASF: Volume intracranien du patient, normalisé
     - eTIV: Estimation du volume intracranien du patient, exprimé en mm3
     - Visit: Nombre de visite nécésessaire pour statuer sur la présence d'une démence
     - MR Delay: Non défini, probablement lié à la mesure de l'IRM
     - Age: Age du patient, exprimé en année
     - EDUC: Age du patient à la fin de ces études, exprimé en année
     - MMSE: Mini-Mental State Examination score (de 0(pire) à 30(meilleur)). C'est un test d'évaluation des fonctions cognitives et des capacités mnésiques d'un individu.
  - **Analyse des distributions**\
Les variables 'nWBV' et  'Age' semblent présenter une distribution gaussienne.<br><br  /> 

  - **Variable qualitatives**:
      - SES: Statut socio-économique tel qu'évalué par l'indice Hollingshead (de 1(meilleur) à 5(plus bas))
      - CDR: Taux de démence clinique (0 = pas de démence, 0.5 = démence très sévère, 1 = démence sévère, 2 = démence modérée)  
      - M/F: Sexe du patient
        
<h2><center>Tests statistiques </center></h2>

**Description des tests statistiques usuels**: 

 - **Variables quantitatives**: 
   - **Test de Pearson**: *Test de dépendance entre 2 variables quantitatives*\
Hypothèse nulle H0: les 2 variables sont indépendantes.
   - **Coefficient corrélation de Pearson**: *Quantifie la corrélation entre 2 variables quantitatives*<br><br />
 - **Variables qualitatives**: 
   - **Test du chi2**: *Test de dépendance entre 2 variables qualitatives*\
Hypothèse nulle H0: les 2 variables sont indépendantes
   - **V de Cramer**: *Quantifie la dépendance entre 2 variables qualitatives*<br><br />
 - **Variables quantitatives et qualitatives**:
   - **Test ANOVA** (Analyse de la variance à un facteur) *Test de dépendance entre une variable qualitative et une variable quantitative*\
Hypothèse nulle H0: les 2 variables sont indépendantes <br><br />

 - **Analyse des distributions**:
    - **Test de Shapiro-Wilk**: *Test de normalité de la distribution d'une série statistique*\
        Hypothèse nulle H0: la distribution suit une loi Normale 
    - **Test de Bartlett**: *Test d'homoscédasticité permettant de vérifier l'égalité des variances entre 2 séries statistiques*\
        Hypothèse nulle H0: les variances sont égales <br><br /> 
        
 - **Tests non paramétriques**: 
    - **Test de Wilcoxon**: *Test d'égalité entre les médianes de 2 séries statistiques si le test de normalité n'est pas respecté.*\
        Hypothèse nulle H0: les médianes sont égales<br><br />
        
 - **Tests paramétriques**:
     - **Test de Welch**: *Test d'égalité entre les moyennes de 2 séries statistiques, si la condition de normalité est respectée et si la condition d'homoscédasticité ne l'est pas.*\
         Hypothèse nulle H0: les moyennes sont égales
     - **Test de Student**: *Test d'égalité entre les moyennes de 2 séries statistiques, si les conditions de normalité et d'homoscédasticité sont respectées.*\
        Hypothèse nulle H0: les moyennes sont égales.
        
<h2><center>Etude des corrélations entre variables explicatives et variable à expliquer</center></h2>
        
 **Analyse entre variables explicatives et variable à expliquer**:
  -  **Variables quantitatives**:
        - Relation nWBV/Group: Hypothèse: le volume total du cerveau semble lié à l'apparition de la démence.
        - Relation Age/Group: Hypothèse: l'âge semble lié à l'apparition de la démence.
        - Relation EDUC/Group: hypothèse: la durée des études semble lié à l'apparition de la démence. Plus le patient a fait de longues études et moins le risque de développer une démence est grand.
        - Relation MMSE/Group: hypothèse: plus le score MMSE est faible et plus le risque de détecter une démence est important.\
Les variables ASF et eTIV ne semble pas lié à l'apparition de la démence chez un patients.

-  **Variables qualitatives**:
    - Relation M/F/Group: hypothèse: proportionnellement, les hommes (38% + 8%) semblent d'avantage touchés que les femmes (28% + 11%) par l'apparition d'une démence
         
         
<h2><center>Etude des corrélations entre variables explicatives </center></h2>

**Analyse entre variables explicatives**:
   - **Analyse entre variables quantitatives**:
       - Relation entre eTIV/ASF: les variables sont parfaitement corrélées, négativement.
       - Relation entre nWBV/Age: l'age du patient et le volume total du cerveau sont négativement corrélée.
   - **Analyse entre variables quantitatives et variables qualitatives**:
       - Relation Visit/MR Delay: les variables sont fortement corrélés.
       - Relation EDUC/SES: les variables sont négativement corrélés. Plus le patient à fait des études et plus le statut socioéconomique est élevé.
   - **Analyse entre variables qualitatives**
       - Relation M/F/CDR: les femmes sont moins touchées par la démence
         
<h1>3. Data-preprocessing</h1>
         
<h2><center>Features engeenering</center></h2>

- **Variables quantitatives**:
   - ratio: cette variable est le rapport entre le volume total de l'encéphale (nWBV) et le volume intracranien du patient (ASF). Cette nouvelle grandeur permet de mieux cerner le phénomène d'atrophie corticale.
- **Variable qualitatives**:
   - malade: cette variable prend la valeur 1 pour un patient atteint de démence ou qui en développera une et la valeur 0 sinon. 
        
<h2><center>Features selection</center></h2>

- **Variables quantitatives**: 
   - nWBV: éliminée car l'information de cette variable explicative est contenue dans la variable ratio.
   - ASF: éliminée car l'information de cette variable explicative est contenue dans la variable ratio.
   - eTIV: éliminée car l'information de cette variable explicative est contenue dans la variable ASF.
   - Visit: éliminé car cette variable aide au diagnostique de la démence, elle ne peut pas en être la cause.
   - MR Delay: éliminée car cette variable explicative est inconnue. 
   - Age: conservée car l'âge d'un patient est lié à la maladie.
   - EDUC: conservé car le niveau d'éducation est lié à la maladie.
   - MMSE: conservé car cette variable explicative est nécéssaire au diagnostique de la maladie.
   - ratio: conservé car cette variable explicative est nécéssaire au diagnostique de la maladie.
- **Variables qualitatives**:
   - SES: conservé car le statut est lié à la maladie.
   - CDR: éliminé car cette variable explicative est un indicateur qui mesure la sévérité de la démence, elle ne peut pas en être la cause.
   - Group: éliminée car cette ancienne variable à expliquer est remplacé par la nouvelle variable malade.  
   - M/F: conservée car le sexe du patient est lié à la maladie.
   - Malade: conservée car c'est la nouvelle variable à expliquée.
        
<h2><center>Features encoding</center></h2>

- **Variables qualitatives**:
   - M/F: M remplacé par 1 et F remplacé par 0
        
<h2><center>Imputation des valeurs manquantes</center></h2>

 - **Variables quantitatives**: 
   - MMSE: pour cette variable, les valeurs manquantes concernent le groupe des patients malades. La solution consiste à remplacer les valeurs manquantes par le mode de la variable MMSE dans le groupe des patients malades. 
 - **Variables qualitatives**:
   - SES: pour cette variable, les valeurs manquantes concernent le groupe des patients malades. La solution consiste à remplacer les valeurs manquantes par le mode de la variable SES dans le groupe des patients malades. 
   
<h2><center>Séparation du jeu de données</center></h2>

- **Jeu de données d'entrainement**: 80% des données du dataset

 - **Variables explicatives**: 
      
   - X_train: Age, EDUC, MMSE, ratio, SES, Sex
        
 - **Variables à expliquer**: 
     
   - y_train: Malade
      
- **Jeu de données de test**: 20% des données du dataset

 - **Variables explicatives**: 
      
   - X_test: Age, EDUC, MMSE, ratio, SES, Sex
        
 - **Variables à expliquer**: 
     
   - y_test: Malade
      
 <h1>4. Fonctions d'évaluations des modèles</h1>

- **Rapport de classification**\
Le rapport de classification reprend sous forme d'un tableau, les différentes métriques de classification (precision, recall, f1-score) pour chacune des classes.
- **Matrice de confusion**\
La matrice de confusion est un tableau informant sur l'exactitude de la classification.
- **Courbes d'apprentissage**\
Les courbes d'apprentissage déterminent les scores sur les jeux de données d'entrainement et de validation, par la méthode de validation croisée. Ces courbes permettent la détection du phénomène de sur-entrainement.
- **Courbes de précision et de rappel**\
Ces courbes sont limitées à la classification binaire, elles informent sur la précision et le rappel pour différents seuils de probabilité d'appartenance à chacune des classes. 
- **Courbe ROC**\
Cette courbe est limitée à la classification binaire, elle permet de visualiser l'évolution de la sensibilité en fonction de l'anti-spécificité, pour différents seuils de probabilité d'appartenance à chacune des classes.


<h1>5. Modélisation</h1>

<h2><center>Première modélisation avec un arbre de décision</center></h2>


- **Hyper-paramètres**:
    - max_depth: 3
        
- **Métriques**:
    - Précision: 79%
    - Recall: 79%
    - F1 Score: 79% 
    - Accuracy: 79%
     
- **Features importance**: 
    - MMSE: 0.54 La variable MMSE est de loin celle qui à la pondération la plus importante dans le cadre de la détection de la démence.
    - ratio:  0.19 Dans une moindre mesure, la variable ratio joue également un rôle dans la prédiction.
    - Age: 0.09 L'impact des autres variables (Age, EDUC, M/F et SES) est marginal sur la classification.
    - EDUC: 0.07
    - M/F: 0.05
    - SES: 0.05
        
- **Evaluation**
    - **Rapport de classification et matrice de confusion**:\
Les patients malades sont bien prédits et les patients non malade sont bien détectés.
    - **Courbes d'apprentissage**:\
Les scores sur les courbes d'apprentissage et de validation convergent. Pas de phénomène d'overfitting détecté.
    - **Courbe ROC**:\
La courbe montre que la sensibilité augmente lentement, à mesure que le seuil de discrimination pour la classe positive baisse.
        
<h2><center>Autres modélisations</center></h2>

**Liste des estimateurs et métriques obtenues**
 - **SVC**:
   - Précision: 90%
   - Recall: 88%
   - F1 Score: 88% 
   - Accuracy: 88%
 - **KNN**:
   - Précision: 87%
   - Recall: 85%
   - F1 Score: 85% 
   - Accuracy: 85%
 - **AdaBoostClassifier**:
   - Précision: 80%
   - Recall: 80%
   - F1 Score: 80% 
   - Accuracy: 80%
 - **RandomForestClassifier**:
   - Précision: 90%
   - Recall: 89%
   - F1 Score: 89% 
   - Accuracy: 89%
 - **XgBoostClassifier**:
   - Précision: 88%
   - Recall: 87%
   - F1 Score: 87% 
   - Accuracy: 87%
 - **Regression logistique**:
   - Précision: 87%
   - Recall: 85%
   - F1 Score: 85% 
   - Accuracy: 85%
        
Les estimateurs produisant les meilleurs scores sont: RandomForestClassifier et SVM. Ces derniers sont retenus dans le cadre de la modélisation finale, leurs optimisation se fera par réglage de leurs hyperparamètres.


<h1>6. Optimisation des estimateurs</h1>  

<h2><center>Premier estimateur: RandomForestClassifier</center></h2>

- **Hyper-paramètres optimaux obtenu avec une grille de recherche**:
    - max_depth: 7
    - max_leaf: 2
        
- **Features importance**: 
     - MMSE: 0.54
     - ratio:  0.19
     - Age: 0.09
     - EDUC: 0.07
     - M/F: 0.05
     - SES: 0.05

- **Evaluation**:
   - Précision: 97%
   - Recall: 84%
   - F1 Score: 91% 
   - Accuracy: 91%
      
<h2><center>Deuxième estimateur: SVM</center></h2>

- **Hyper-paramètres optimaux obtenu avec une grille de recherche**:
    - gamma: 0.1
    - C: 100
    - Kernel: rbf
    - degre: 1

- **Evaluation**:
   - Précision: 86%
   - Recall: 86%
   - F1 Score: 86% 
   - Accuracy: 86%
    
<h1>7. Conclusion</h1>

Après optimisation des hyperparamètres de l'estimateur RandomForestClassifier, il s'avère que ce dernier fournit les meilleurs métriques, parmi tous les modèles testés.
 
Pour la classe des patients malades, les métriques sont les suivantes:
- Précision: 97%
- Recall: 84%
- F1 Score: 90%

La classe des patients malades est donc correctement prédite et détectée par la modèlisation finale.

Le taux de bonne prédiction(Accuracy) du modèle est de 91%, il est considéré comme performant pour répondre à notre problématique.
    

      
