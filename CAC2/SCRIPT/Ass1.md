# COURS DE SCIENCE DES DONNÉES
## ENCG - 4ème Année - CAC2
# ERROUYAS AYA
# Nom du jeu: IRIS
<img src="IMG-20241010-WA0122.jpg" style="height:464px;margin-right:464px"/>

## DATASET choisissée 
L'ensemble de données Iris est l'un des plus connus et des plus utilisés en statistique et en science des données. Cependant, l'origine d'une partie au moins de ces données est restée un mystère pendant des décennies. Antony Unwin et Kim Kleinman pensent avoir retrouvé la source.
- **Dataset Characteristics** : Tabular
- **Subject Area** : Biology
- **Associated Tasks** : Classification
- **Instances** : 150
## Déscriptive de la base se donnée:
Il s'agit de l'un des premiers jeux de données utilisés dans la littérature sur les méthodes de classification et largement employé en statistique et en apprentissage automatique. Ce jeu de données contient 3 classes de 50 instances chacune, chaque classe correspondant à une espèce d'iris. Une classe est linéairement séparable des deux autres ; ces dernières ne le sont pas entre elles.

Attribut prédit : espèce d'iris.

Ce domaine est extrêmement simple.

Ces données diffèrent de celles présentées dans l'article de Fisher (identifiées par Steve Chadwick, spchadwick@espeedaz.net). Le 35e échantillon devrait être : 4,9 ; 3,1 ; 1,5 ; 0,2 ; « Iris-setosa », l'erreur se situant au niveau de la quatrième caractéristique. Le 38e échantillon devrait être : 4,9 ; 3,6 ; 1,4 ; 0,1 ; ​​« Iris-setosa », les erreurs se situant au niveau des deuxième et troisième caractéristiques.

## Les espèces d'iris:
Les trois espèces d'iris qui composent l'ensemble de données . Ces plantes ont été découvertes et mesurées par Anderson, qui a collaboré non seulement avec Fisher, mais aussi avec John Tukey. La dédicace du célèbre ouvrage de Tukey sur l'analyse exploratoire des données se lit comme suit : « À la mémoire de Charlie Winsor, biométricien, et d'Edgar Anderson, botaniste et analyste de données, auprès desquels l'auteur a beaucoup appris.»

Anderson a choisi d'étudier les iris car, comme il l'écrivait en 1928, « si nous voulons comprendre la nature ultime des espèces, nous devons réduire le problème à sa plus simple expression et étudier quelques espèces facilement reconnaissables et bien différenciées »². Ces travaux ont ouvert la voie à ses contributions aux avancées majeures de la biologie évolutive au cours des deux décennies suivantes, connues sous le nom de « Synthèse moderne ». Dans ce même article, il rapporte avoir collecté et mesuré des plants d’Iris versicolor entre 1923 et 1928. De façon inattendue, il conclut à l’existence de deux espèces, initialement difficiles à distinguer : I. versicolor et I. virginica, la première se rencontrant principalement dans le nord-est des États-Unis et la seconde dans le sud. Des études complémentaires le convainquirent que, malgré leurs similitudes, elles étaient trop différentes pour être directement apparentées. Dans un article de 1936 synthétisant ses travaux sur les iris, il suggéra qu’I. versicolor pourrait être le résultat d’une hybridation entre I. virginica et une autre espèce d’iris, et expliqua en détail pourquoi il considérait I. setosa comme un candidat évident. Il en vint à considérer ces rétrocroisements répétés, ou hybridations introgressives, comme un mécanisme évolutif important.
  
```python
from ucimlrepo import fetch_ucirepo

# fetch dataset
iris = fetch_ucirepo(id=53)

# data (as pandas dataframes)
X = iris.data.features
y = iris.data.targets

# metadata
print(iris.metadata)

# variable information
print(iris.variables)

```
name     role         type demographic  \
0  sepal length  Feature   Continuous        None   
1   sepal width  Feature   Continuous        None   
2  petal length  Feature   Continuous        None   
3   petal width  Feature   Continuous        None   
4         class   Target  Categorical        None   

                                         description units missing_values  
0                                               None    cm             no  
1                                               None    cm             no  
2                                               None    cm             no  
3                                               None    cm             no  
4  class of iris plant: Iris Setosa, Iris Versico...  None             no  
