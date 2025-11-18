# Architecture générale du module

Vous pouvez organiser votre dossier de travail ainsi :

```text
projet-formation-html-css-js/
│
├── index.html
├── selecteurs.html
├── typographie.html
├── mise-en-page.html
├── animations.html
├── responsive.html
│
└── assets/
    ├── css/
    │   ├── base.css
    │   ├── selecteurs.css
    │   ├── typographie.css
    │   ├── mise-en-page.css
    │   ├── animations.css
    │   └── responsive.css
    ├── js/
    ├── img/
    └── video/
```

Les fichiers `js/`, `img/` et `video/` sont prévus pour la suite du cours, même si nous ne les utilisons pas encore ici.

---

# 1. Page d’accueil du module – `index.html` + `assets/css/base.css`

## 1.1. Objectif pédagogique

* Présenter le module CSS3 et servir de **menu d’accès** aux différents exemples.
* Mettre en place une **feuille de style globale** (`base.css`) utilisée par toutes les pages.

## 1.2. Fichier `index.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Module 02 – CSS3</title>
  <link rel="stylesheet" href="assets/css/base.css">
</head>
<body>
  <header>
    <h1>Module 02 – CSS3</h1>
    <p>Exemples de styles, de mise en page, d’animations et de responsive design.</p>
  </header>

  <main>
    <section>
      <h2>Plan des exemples</h2>
      <ul>
        <li><a href="selecteurs.html">Sélecteurs CSS</a></li>
        <li><a href="typographie.html">Typographie et texte</a></li>
        <li><a href="mise-en-page.html">Mise en page (display, position, flexbox)</a></li>
        <li><a href="animations.html">Transitions et animations CSS3</a></li>
        <li><a href="responsive.html">Responsive design (media queries)</a></li>
      </ul>
    </section>
  </main>

  <footer>
    <p>Support de cours – Formation HTML/CSS/JS</p>
  </footer>
</body>
</html>
```

## 1.3. Fichier `assets/css/base.css`

```css
/* assets/css/base.css – Styles généraux du module */

* {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
  margin: 0;
  padding: 0;
  line-height: 1.5;
  background-color: #f5f5f5;
}

header,
main,
footer {
  width: 90%;
  max-width: 960px;
  margin: 0 auto;
}

header {
  padding: 20px 0;
}

h1 {
  margin: 0 0 10px 0;
  color: #2c3e50;
}

h2 {
  color: #34495e;
}

p {
  color: #555555;
}

ul {
  list-style-type: disc;
  padding-left: 20px;
}

a {
  color: #2980b9;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

footer {
  margin-top: 40px;
  padding: 20px 0;
  border-top: 1px solid #dddddd;
  font-size: 14px;
  color: #777777;
}
```

### 1.4. Explication – grandes lignes

* `base.css` joue le rôle de **charte graphique globale** du module (police, largeur, couleurs de base, liens, etc.).
* `box-sizing: border-box;` assure un calcul plus intuitif des largeurs/hauteurs (la width inclut padding et border).
* `header, main, footer` centrent le contenu et limitent la largeur.

### 1.5. Sélecteurs utilisés

* `*` : sélecteur universel, s’applique à tous les éléments.
* `body`, `header`, `main`, `footer`, `h1`, `h2`, `p`, `ul`, `a`, `footer` : **sélecteurs de type** (par balise).
* `a:hover` : **pseudo-classe** appliquée au survol.

---

# 2. Sélecteurs CSS – `selecteurs.html` + `assets/css/selecteurs.css`

## 2.1. Objectif pédagogique

* Illustrer les principaux types de sélecteurs :
  type, classe, identifiant, relations (descendant, enfant direct), attribut, pseudo-classes et pseudo-éléments.

## 2.2. Fichier `selecteurs.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Sélecteurs CSS</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <link rel="stylesheet" href="assets/css/selecteurs.css">
</head>
<body>
  <header>
    <h1>Sélecteurs CSS</h1>
    <p>Exemples de sélecteurs de type, de classe, d’identifiant, de relation et d’attribut.</p>
  </header>

  <main>
    <section>
      <h2>Sélecteur de type</h2>
      <p>Paragraphe 1</p>
      <p>Paragraphe 2</p>
    </section>

    <section>
      <h2>Sélecteur de classe</h2>
      <p class="important">Texte avec la classe "important".</p>
      <p class="important">Autre texte important.</p>
      <p>Texte non important.</p>
    </section>

    <section>
      <h2>Sélecteur d’identifiant</h2>
      <p id="intro">Paragraphe d’introduction avec un identifiant unique.</p>
      <p>Paragraphe standard.</p>
    </section>

    <section>
      <h2>Sélecteurs de relation et d’attribut</h2>

      <article>
        <h3>Article principal</h3>
        <p>Paragraphe à l’intérieur de l’article (coloré via article p).</p>
      </article>

      <p>Paragraphe à l’extérieur de l’article (non impacté par article p).</p>

      <ul>
        <li>Élément de liste 1</li>
        <li>Élément de liste 2</li>
      </ul>

      <p>
        <a href="https://www.example.com" target="_blank">Lien avec target="_blank"</a><br>
        <a href="https://www.example.com">Lien sans target</a>
      </p>
    </section>

    <section>
      <h2>Pseudo-éléments</h2>
      <p class="demo-pseudo">
        Ce paragraphe illustre l’utilisation des pseudo-éléments
        ::first-line, ::first-letter, ::before et ::after.
      </p>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour au sommaire du module CSS</a></p>
  </footer>
</body>
</html>
```

## 2.3. Fichier `assets/css/selecteurs.css`

```css
/* assets/css/selecteurs.css – Exemples de sélecteurs CSS */

/* Sélecteur de type : ici sur les <p> de la première section uniquement */
main section:first-of-type p {
  color: darkgreen;
}

/* Sélecteur de classe */
.important {
  font-weight: bold;
  color: darkred;
}

/* Sélecteur d’identifiant */
#intro {
  font-size: 18px;
  color: #333333;
}

/* Descendant : tous les <p> situés à l’intérieur d’un <article> */
article p {
  color: blue;
}

/* Enfant direct : tous les <li> directement contenus dans un <ul> */
ul > li {
  list-style-type: square;
}

/* Sélecteur d’attribut : lien ouvrant dans un nouvel onglet */
a[target="_blank"] {
  color: red;
}

/* Pseudo-classe : état au survol */
a:hover {
  color: green;
}

/* Pseudo-éléments sur un paragraphe de démonstration */
.demo-pseudo::first-line {
  font-weight: bold;
}

.demo-pseudo::first-letter {
  font-size: 2em;
}

.demo-pseudo::before {
  content: ">> ";
}

.demo-pseudo::after {
  content: " <<";
}
```

### 2.4. Explication – grandes lignes

* Montrer que l’on peut cibler soit **tous les éléments d’un type**, soit une **classe réutilisable**, soit un **id unique**.
* Montrer la différence entre un **descendant** (n’importe où dans la hiérarchie) et un **enfant direct**.
* Introduire les **pseudo-classes** (états, par exemple `:hover`) et les **pseudo-éléments** (parties d’un élément : première lettre, première ligne, etc.).

### 2.5. Sélecteurs utilisés

* `main section:first-of-type p` : sélecteur de type, combiné avec pseudo-classe structurale `:first-of-type`.
* `.important` : **classe**.
* `#intro` : **identifiant**.
* `article p` : **descendant** (cible les `<p>` à l’intérieur d’un `<article>`).
* `ul > li` : **enfant direct**.
* `a[target="_blank"]` : **sélecteur d’attribut**.
* `a:hover` : **pseudo-classe** sur les liens.
* `.demo-pseudo::first-line`, `::first-letter`, `::before`, `::after` : **pseudo-éléments**.

---

# 3. Typographie et texte – `typographie.html` + `assets/css/typographie.css`

## 3.1. Objectif pédagogique

* Contrôler la **police**, la **taille**, l’**interlignage**, les **espacements**, l’alignement et la transformation du texte.
* Montrer l’usage de classes typographiques réutilisables.

## 3.2. Fichier `typographie.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Typographie et texte</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <link rel="stylesheet" href="assets/css/typographie.css">
</head>
<body>
  <header>
    <h1>Typographie et mise en forme du texte</h1>
    <p>Exemples de polices, tailles, interlignage, transformations et liens.</p>
  </header>

  <main>
    <section>
      <h2>Famille de police et tailles</h2>
      <p>Texte de base.</p>
      <p class="grand">Texte plus grand (classe "grand").</p>
      <p class="petit">Texte plus petit (classe "petit").</p>
    </section>

    <section>
      <h2>Alignement, interlignage, espacements</h2>
      <p class="paragraphe-avance">
        Ce paragraphe illustre l'interlignage, l'espacement des lettres et des mots,
        ainsi que l'alignement justifié sur la largeur disponible.
      </p>
    </section>

    <section>
      <h2>Transformation du texte et liens</h2>
      <h3 class="titre-centre">Titre centré en majuscules</h3>
      <p>
        <a href="#" class="lien">Lien sans soulignement au repos, souligné au survol.</a>
      </p>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour au sommaire du module CSS</a></p>
  </footer>
</body>
</html>
```

## 3.3. Fichier `assets/css/typographie.css`

```css
/* assets/css/typographie.css – Typographie et texte */

body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
}

/* Tailles relatives */

.grand {
  font-size: 1.5em;
}

.petit {
  font-size: 0.8em;
}

/* Interlignage et espacements */

.paragraphe-avance {
  line-height: 1.6;
  letter-spacing: 1px;
  word-spacing: 3px;
  text-align: justify;
}

/* Alignement et transformation */

.titre-centre {
  text-align: center;
  text-transform: uppercase;
}

/* Lien typographié */

.lien {
  text-decoration: none;
  color: #2980b9;
}

.lien:hover {
  text-decoration: underline;
}
```

### 3.4. Explication – grandes lignes

* Utilisation d’**unités relatives** (`em`) pour les tailles afin de faciliter l’adaptabilité.
* `line-height`, `letter-spacing`, `word-spacing` gèrent la **lisibilité** du texte.
* `text-transform: uppercase;` permet des effets typographiques sans modifier le HTML.
* Gestion du style des liens (avec un comportement différent au survol).

### 3.5. Sélecteurs utilisés

* `body` : sélecteur de type pour définir la police générale.
* `.grand`, `.petit`, `.paragraphe-avance`, `.titre-centre`, `.lien` : **classes** réutilisables.
* `.lien:hover` : pseudo-classe sur les liens.

---

# 4. Mise en page – `mise-en-page.html` + `assets/css/mise-en-page.css`

## 4.1. Objectif pédagogique

* Illustrer la différence entre `block`, `inline`, `inline-block`.
* Montrer le **positionnement** relatif et fixe.
* Introduire **Flexbox** pour une mise en page moderne.

## 4.2. Fichier `mise-en-page.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Mise en page – Display, position, flexbox</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <link rel="stylesheet" href="assets/css/mise-en-page.css">
</head>
<body>
  <header>
    <h1>Mise en page avec CSS</h1>
    <p>Illustration de display, positionnement et flexbox.</p>
  </header>

  <main>
    <section>
      <h2>Display : block, inline, inline-block</h2>
      <div class="bloc">Élément de type bloc</div>
      <span class="en-ligne">Inline 1</span>
      <span class="en-ligne">Inline 2</span>
      <div>
        <span class="inline-block">Inline-block 1</span>
        <span class="inline-block">Inline-block 2</span>
      </div>
    </section>

    <section>
      <h2>Positionnement relatif et fixe</h2>
      <div class="relative">Bloc positionné relativement.</div>
      <div class="fixed">Bloc fixé en bas à droite.</div>
      <p>
        Ajoutez du texte dans cette section et faites défiler la page
        pour observer le bloc fixé en bas à droite.
      </p>
    </section>

    <section>
      <h2>Mise en page avec Flexbox</h2>
      <div class="container-flex">
        <div class="item-flex">Bloc 1</div>
        <div class="item-flex">Bloc 2</div>
        <div class="item-flex">Bloc 3</div>
      </div>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour au sommaire du module CSS</a></p>
  </footer>
</body>
</html>
```

## 4.3. Fichier `assets/css/mise-en-page.css`

```css
/* assets/css/mise-en-page.css – Mise en page */

/* Display */

.bloc {
  display: block;
  background-color: #e0e0e0;
  margin-bottom: 10px;
  padding: 10px;
}

.en-ligne {
  display: inline;
  background-color: #c0ffc0;
  padding: 5px;
}

.inline-block {
  display: inline-block;
  width: 100px;
  height: 50px;
  background-color: #c0c0ff;
  margin: 5px;
  text-align: center;
  line-height: 50px;
}

/* Positionnement */

.relative {
  position: relative;
  top: 10px;
  left: 20px;
  background-color: #ffe0e0;
  padding: 10px;
  margin-bottom: 40px;
}

.fixed {
  position: fixed;
  bottom: 10px;
  right: 10px;
  background-color: #e0ffe0;
  padding: 10px;
  border: 1px solid #cccccc;
}

/* Flexbox */

.container-flex {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #333333;
  padding: 10px;
  gap: 10px;
}

.item-flex {
  flex: 1;
  padding: 10px;
  border: 1px solid #cccccc;
  background-color: #f0f0f0;
  text-align: center;
}
```

### 4.4. Explication – grandes lignes

* `display: block | inline | inline-block` montre ce que signifie **occuper toute la ligne** (block) ou seulement la largeur du contenu (inline).
* `position: relative` décale l’élément par rapport à sa position normale.
* `position: fixed` ancre l’élément à la fenêtre, même en cas de défilement.
* `display: flex` + `justify-content` + `align-items` structurent une rangée de blocs de manière moderne et responsive.

### 4.5. Sélecteurs utilisés

* `.bloc`, `.en-ligne`, `.inline-block`, `.relative`, `.fixed`, `.container-flex`, `.item-flex` : **classes** appliquées à des éléments précis pour illustrer chaque comportement.

---

# 5. Transitions et animations – `animations.html` + `assets/css/animations.css`

## 5.1. Objectif pédagogique

* Introduire les **transitions CSS** (changement progressif entre deux états).
* Illustrer une **animation** via `@keyframes`.

## 5.2. Fichier `animations.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Transitions et animations CSS3</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <link rel="stylesheet" href="assets/css/animations.css">
</head>
<body>
  <header>
    <h1>Transitions et animations CSS3</h1>
  </header>

  <main>
    <section>
      <h2>Transition sur un bouton</h2>
      <button class="btn-transition">Survolez ce bouton</button>
    </section>

    <section>
      <h2>Animation par keyframes</h2>
      <div class="alert">Message d'alerte clignotant.</div>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour au sommaire du module CSS</a></p>
  </footer>
</body>
</html>
```

## 5.3. Fichier `assets/css/animations.css`

```css
/* assets/css/animations.css – Transitions et animations */

/* Transition sur le bouton */

.btn-transition {
  background-color: #3498db;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-transition:hover {
  background-color: #2980b9;
}

/* Animation avec keyframes */

@keyframes clignote {
  0%   { opacity: 1; }
  50%  { opacity: 0; }
  100% { opacity: 1; }
}

.alert {
  background-color: #ffcccc;
  padding: 10px;
  animation-name: clignote;
  animation-duration: 1s;
  animation-iteration-count: infinite;
}
```

### 5.4. Explication – grandes lignes

* La transition est déclenchée par le changement d’état `:hover` sur `.btn-transition`, ce qui crée un effet d’animation fluide.
* L’animation `clignote` fait varier `opacity` dans le temps, appliquée à `.alert` de manière infinie (`animation-iteration-count: infinite`).

### 5.5. Sélecteurs utilisés

* `.btn-transition`, `.alert` : **classes** appliquées à un bouton et un bloc.
* `.btn-transition:hover` : pseudo-classe pour gérer l’état au survol.
* `@keyframes clignote` : bloc de définition d’animation, non un sélecteur mais une règle à part.

---

# 6. Responsive design – `responsive.html` + `assets/css/responsive.css`

## 6.1. Objectif pédagogique

* Montrer un exemple simple de **responsive design** avec une approche **mobile-first**.
* Introduire les **media queries** en fonction de la largeur d’écran.

## 6.2. Fichier `responsive.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Responsive design – Media queries</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="assets/css/base.css">
  <link rel="stylesheet" href="assets/css/responsive.css">
</head>
<body>
  <header>
    <h1>Responsive design</h1>
    <p>Exemple de mise en page adaptative (mobile-first).</p>
  </header>

  <main>
    <section>
      <h2>Grille simplifiée responsive</h2>
      <div class="container-responsive">
        <div class="bloc-responsive">Bloc 1</div>
        <div class="bloc-responsive">Bloc 2</div>
        <div class="bloc-responsive">Bloc 3</div>
      </div>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour au sommaire du module CSS</a></p>
  </footer>
</body>
</html>
```

## 6.3. Fichier `assets/css/responsive.css`

```css
/* assets/css/responsive.css – Responsive design */

/* Styles de base (mobile-first) */

.container-responsive {
  width: 90%;
  margin: 0 auto;
}

.bloc-responsive {
  background-color: #e0e0e0;
  margin-bottom: 10px;
  padding: 10px;
}

/* À partir de 768px : disposition en colonnes avec flex */

@media (min-width: 768px) {
  .container-responsive {
    display: flex;
    gap: 10px;
  }

  .bloc-responsive {
    flex: 1;
    margin-bottom: 0;
  }
}

/* À partir de 1024px : ajustement typographique */

@media (min-width: 1024px) {
  body {
    font-size: 18px;
  }
}
```

### 6.4. Explication – grandes lignes

* Les styles par défaut s’appliquent aux **petits écrans** (mobile-first).
* À partir de 768px, on applique un `display: flex` sur `.container-responsive` pour aligner les blocs en ligne.
* À partir de 1024px, on augmente légèrement la taille de la police pour améliorer le confort de lecture.

### 6.5. Sélecteurs utilisés

* `.container-responsive`, `.bloc-responsive` : classes de mise en page.
* `@media (min-width: 768px)` et `@media (min-width: 1024px)` : **media queries** conditionnant l’application des règles.
