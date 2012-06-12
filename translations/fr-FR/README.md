# Principes d'écriture de CSS consistant et idiomatique

Le présent document liste des recommandations raisonnables pour développer avec CSS.

Il n'est pas destiné à être normatif et je ne souhaite pas imposer mes préférences de style de code aux gens. Toutefois, ces lignes directrices encouragent fortement le fait d'utiliser des modèles existants, communs et sensés.

Ceci est un document évolutif et les nouvelles idées sont toujours les bienvenues.
Merci de contribuer.

## Traductions

* [Français] (https://github.com/necolas/idiomatic-css/tree/master/translations/fr-FR)
* [Italien](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [Serbe](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)


## Table des matières

1. [Principes généraux](#principes-generaux)
2. [Espaces](#espaces)
3. [Commentaires](#commentaires)
4. [Format](#format)
5. [Nommage](#nommage)
6. [Exemple pratique](#exemple)
7. [Organisation](#organisation)
8. [ Compilation et déploiement ](#compilation-et-deploiement )

[Remerciements](#remerciements )


<a name="principes-generaux"></a>
## 1. Principes généraux

> "Part of being a good steward pour un projet réussi est de comprendre qu'écrire du code pour soi-même est une mauvaise idée™. Si des milliers de personnes utilisent votre code, alors écrivez votre code en visant une clarté maximale, et non en fonction de croyances personnelles comme comment devenir plus intelligent en lisant les specs." - Idan Gazit

* Tout code présent dans n'importe quelle base de code doit avoir l'air d'avoir été écrit par une seule personne, peu importe le nombre de gens qui y ont contribué.
* Appliquez les conventions de style de manière stricte.
* En cas de doute, utilisez des modèles existants et communs.


<a name="espaces"></a>
## 2. Espaces

Un seul style devrait exister pour la totalité du code source de votre projet. Soyez toujours consistant dans votre utilisation des espaces. Utilisez des espaces pour améliorer la lisibilité.

* Ne mélangez _jamais_ les espaces et les tabulations pour l'indentation.
* Choisissez entre des retraits (espaces) ou de vraies tabulations. Tenez vous en à votre choix sans y déroger. (Préférence: espaces)
* Si vous utilisez les espaces, choisissez le nombre de caractères utilisés pour chaque niveau d'indentation.
(Préférence: 4 espaces)

Astuce: Configurez votre éditeur afin qu'il affiche les "caractères invisibles". Cela vous permettra de supprimer les espaces en fin de ligne, et les lignes vides non intentionnelles et évitera de polluer vos soumissions.

<a name="commentaires"></a>
## 3. Commentaires

Bien commenter son code est important. Prenez le temps de décrire vos modules, comment ils fonctionnent, leurs limites, et la manière dont ils sont conçus. Ne laissez pas les autres membres de l'équipe deviner le but d'une partie inhabituelle de code difficile à comprendre.
Le style des commentaires devrait être simple et cohérent au sein d'une même base de code.

* Placez les commentaires sur une nouvelle ligne au-dessus de leur sujet.
* Evitez les commentaires en fin de ligne.
* Gardez des lignes d'une longueur raisonnable, par exemple, 80 colonnes.
* Faites une utilisation libre des commentaires afin de séparer le code CSS en sections distinctes.
* Use "sentence case" comments and consistent text indentation.

Astuce: configurez votre éditeur afin qu'il fournisse des raccourcis pour insérer des modéles de commentaires prédéfinis.

#### Exemple en CSS :

```css
/* ==========================================================================
   Section de bloc de commentaires
   ========================================================================== */

/* Sous-section de bloc de commentaires
   ========================================================================== */

/*
 * Groupe de bloc de commentaires.
 * Parfait pour les explications sur plusieurs lignes et la documentation.
 */

/* Commentaire simple */
```

#### Exemple en SCSS :

```scss
// ==========================================================================
// Section de bloc de commentaires
// ==========================================================================

// Sous-section de bloc de commentaires
// ==========================================================================

//
// Groupe de bloc de commentaires.
// Parfait pour les explications sur plusieurs lignes
// et la documentation

// Commentaire simple
```


<a name="format"></a>
## 4. Formatage

Le format de code choisi doit assurer que le code soit: simple à lire; simple
à commenter clairement; minimize les chances d'introduire accidentellement
des erreurs; et résultant en différentiels et blames utiles.

1. Un sélecteur distinct par ligne pour un ensemble de règles à sélecteurs multiples.
2. Un expace unique avant l'accolade ouvrante d'un ensemble de règles.
3. Une déclaration par ligne dans un bloc de déclarations.
4. Un niveau d'indentation pour chaque déclaration.
5. Un espace unique après le double point d'une déclaration.
6. Toujours inclure un point-virgule à la fin de la dernière déclaration dans
   un bloc de déclarations.
7. Placez l'accolade fermante d'un ensemble de règles sur la même colonne que le premier caractère de l'ensemble de règles.
8. Séparez chaque ensemble de règles par une ligne vide.

```css
.selecteur-1,
.selecteur-2,
.selecteur-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### Ordre des déclarations
Les déclarations devraient être ordonnées en accord avec un principe unique. Ma
préférence va à un regroupement des propriétés connexes et que les propriétés
structurellement importantes (par ex. le positionnement et le box-model) soient
déclarées avant lpropriétés de typographie, d'arrière-plan et de couleur.

```css
.selecteur {
    position: relative;
    display: block;
    width: 50%;
    height: 100px;
    padding: 10px;
    border: 0;
    margin: 10px;
    color: #fff
    background: #000;
}
```

Un ordonnancement alphabétique est aussi populaire, mais le désavantage est que
cela sépare des proriétés connexes. Par exemple, les décalages de positionnement
ne sont plus gorupées ensemble et les propriétés de box-model peuvent finir
éparpillées dans l'ensemble du bloc de déclaration.

#### Exceptions et légèrs écarts

De grands blocs de déclarations uniques peuvent utiliser un format différent sur
une seule ligne. Dans ce cas, un espace devrait être inséré après l'accolade
ouvrante et avant l'accolade fermante.

```css
.selecteur-1 { width: 10%; }
.selecteur-2 { width: 20%; }
.selecteur-3 { width: 30%; }
```

De longues valeurs, séprarée par des virgules, de propriété - comme des ensembles
de dégradés ou d'ombrages - peuvent être diposées sur plusieurs lignes dans
un effort afin d'améliorer la lisibilité et de produire des différentiels plus
utiles. Il existe différents formats qui peuvent être utilisés; un exemple est
montré ci-dessous.

```css
.selecteur {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### En vrac

* Utilisez des valeurs hexadécimales en minuscules, par ex., `#aaa`.
* Utilisez des simples ou doubles guillemets de manière cohérente. De préférence
  des doubles guillements, par ex., `content: ""`.
* Entourez toujours les valeurs des attributs dans les sélecteurs,
  par ex., `input[type="checkout"]`.
* _Lorsque c'est permit_, évitez de spécifier les unités pour les valeurs
  égales à zéro, par ex., `margin: 0`.

### Pre processeurs: considérations additionnelles pour le format

Les différents pre processeurs CSS possèdent différents capacités, fonctionnalités
et syntaxes. Vos conventions devraient être étendues afin de s'accomoder aux
particularités de n'importe quel pre processeur utilisé. Les lignes directrices
suivantes font référence à Sass.

* Limitez l'imbrication à 1 niveau de profondeur. Réexamminez toute imbrication
  supérieur à 2 niveaux de profondeur. Ceci permet d'éviter des sélecteurs CSS
  trop spécifiques.
* Evitez un grand nombre de règles imbriquées. Séparez-les lorsqu'elle commencent
  à impacter la lisibilité. Préférez éviter des imbrications qui s'étendent sur
  plus de 20 lignes.
* Placez toujours les déclarations `@extend` sur la première ligne du bloc de
  déclarations.
* Lorsque c'est possible, groupez les déclarations `@include` en haut du bloc de
  déclarations, après les déclarations `@extend`.
* Envisagez de préfixer les fonctions personnalisées avec `x-` ou un autre préfixe.
  Ceci peut aider à éviter toute confusion entre vos fonctions et celles native à CSS,
  ou à entrer en conflit avec des fonctions des bibliothèques.

```scss
.selecteur-1 {
    @extend .autre-regle;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // autres déclarations
}
```


<a name="nommage"></a>
## 5. Nommage

Vous n'êtes pas un compilateur/compresseur de code humain, alors ne prétendez pas en être un.

Utilisez des noms clairs et réfléchis pour les classes HTML. Choisissez un modçle de nommage consistent et compréhensif qui a du sens à la fois dans les fichiers HTML et dans les fichiers CSS.

```css
/* Exemple de code mal nommé */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Exemple de code bien nommé */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="exemple"></a>
## 6. Exemple pratique

Un exemple de plusieurs conventions.

```css
/* ==========================================================================
   Construction de la grille
   ========================================================================== */

/*
 * Exemple de HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Empêche d'entourer les cellules en inline-block */
    white-space: nowrap;
    /* Suppression des espaces entre les cellules */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Définition de l'espacement entre les cellules */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Réinitialisation de la gestion des espaces */
    white-space: normal;
    /* Réinitialisation de la taille de police */
    font-size: 16px;
}

/* Etats des cellules */

.cell.is-animating {
    background-color: #fffdec;
}

/* Dimensions des cellules
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Styles de cellule
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organisation"></a>
## 7. Organisation

L'organisation du code est une partie importante de n'importe quelle base de code CSS et cruciale pour les grosses bases de code.

* Séparer de manière logique les différentes parties de code.
* Utilisez des fichiers distincts (concaténés au cours de l'étape de compilation) pour aider à séparer le code des différents composants.
* Si vous utilisez un pré-processeur, stockez le code récurrent dans des variables pour la couleur, la typographie, etc.


<a name="compilation-et-deploiement"></a>
## 8. Compilation et déploiement

Les projets devraient toujours essayer de mentionner des façons génériques grâce auxquelles le code source peut être validé, testé, compressé, et versionné en préparation à l'utilisation en production. Pour cette tâche, [grunt](https://github.com/cowboy/grunt) de Ben Alman est un excellent outil.


<a name="remerciements"></a>
## Remerciements

Merci à tous ceux qui ont contribué à [idiomatic.js](https://github.com/rwldrn/idiomatic.js). Cela a été une source d'inspiration, de citations et de conventions.
