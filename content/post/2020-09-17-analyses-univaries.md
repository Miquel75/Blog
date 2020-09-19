---
title: Analyses univariés
author: Miquel Pons
date: '2020-09-17'
slug: analyses-univaries
categories: [R]
tags: [analyses univariés, statistique descriptives, visualisation]
---


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

L'analyse univarié est l'analyse d'une seule variable. C'est de l'analyse descriptive. En plus de **summary** utilisé précédemment, vous pouvez employer les fonctions suivantes.

**mean** permet d'obtenir la moyenne. 

Si l'on prend le même jeu de donnée que précédemment.

``` {r }

setwd ("C:/Users/Miquel Pons/Desktop")

table <- read.table("poissons.txt", sep = ";") 

```

On veut la moyenne de la variable profondeur "Prof"

``` {r }

mean (table$Prof)

```


**sd** permet d'avoir l'écart type qui donne une mesure de la dispersion des valeur. 

``` {r }

sd (table$Prof)

```

**min** donne la valeur minimum. 

``` {r }

min (table$Prof)

```

**max** donne la valeur maximum.

``` {r }

max (table$Prof)

```

**range** décrit l'étendu de votre variable. 

``` {r }

range (table$Prof)

```

**median** vous donne la médiane, la valeur permettant d'avoir autant de valeurs supérieurs la médiane que inférieurs. 

``` {r }

median (table$Prof)

```


**quantile** permet bien évidemment d'obtenir les quantiles, des valeurs qui divisent les données en intervalles contenant le même nombre de données. Ils permettent donc une mesure de la répartition. Comme vous pouvez le constater, le quantile qui sépare les données en deux groupes (50%) est la médiane. Les valeurs de 25%, 50% et 75% sont appelés quartiles. 

``` {r }

quantile (table$Prof)

```

# Visualisation 

**hist** permet d'afficher un histogramme présentant la répartition d'une variable continue. 

``` {r }

hist (table$Prof)

```



**table** vous donne le nombre de lignes pour chaque valeur de votre variable. Ici vous pouvez constater qu'il n'est pas bon de nommer vos données "table" puisque cela peut porter a confusion. Nous allons donc créer un autre objet contenant table. 

``` {r }


poissons <- table

table (poissons$Prof)

plot (table(poissons$Prof))

```

**pie** permet d'afficher un visuel de la répartition d'une variable sous forme de camembert. Ce format est peu utilisé car est considéré peu intuitif visuellement pour bien voir les quantités. Cependant ça reste sympa pour des infographies ou des présentations. 

``` {r }

pie (table(poissons$Zone))

```

**plot(density())** donne la densité d'une variable quantitative.La fonction plot est la fonction général permettant la représentation graphique. Il y a beaucoup de différentes options qu'il vous appartient de découvrir. Des exemples seront données par la suite.

``` {r }

plot(density(poissons$Prof))

```


**boxplot** affiche une représentation graphique de la répartition des valeurs d'une variable quantitative que l'on appelle boîte à moustache. SUr ce graphique les quartiles, valeurs permettant la répartitions des données en quantiles, sont représentés.


``` {r }

boxplot(poissons$Prof)

```

**dotchart**

``` {r }

dotchart(as.matrix(table(poissons$Zone))) #étant donné que R attend une matrice pour ce graphique, il convient d'utiliser as.matrix afin de rentrer les valeurs sous forme de matrice

```
