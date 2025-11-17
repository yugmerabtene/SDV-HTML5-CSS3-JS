# MODULE-01 – HTML5

**Public cible :** Développeur Fullstack / Développeur Web
**Objectif général :** Savoir construire une page web complète, structurée et sémantique en HTML5, conforme aux standards du W3C.

---

## 1. Introduction à l’histoire et au fonctionnement d’Internet et du Web

### 1.1. Des premiers ordinateurs au Web

L’histoire du HTML commence bien avant Internet lui-même.
Pour comprendre le Web, il faut revenir aux grandes étapes de l’informatique :

* **Années 1940–1950 :**
  Les premiers ordinateurs électroniques, comme **ENIAC** (1946) ou **UNIVAC I** (1951), occupent des salles entières.
  Ils n’ont ni clavier ni écran : les programmes sont saisis via des **cartes perforées**.
  Ils servent principalement à des calculs scientifiques et militaires.

* **Années 1950–1970 :**
  Les composants électroniques évoluent : apparition du **transistor** (1947, Bell Labs), puis des **circuits intégrés**.
  En **1971**, Intel lance le premier **microprocesseur** (Intel 4004) : c’est la naissance de l’ordinateur personnel.

* **Années 1960–1970 :**
  L’enjeu devient la **communication entre ordinateurs**.
  En **1969**, le réseau **ARPANET** est mis en place sous l’impulsion du département de la Défense américain.
  C’est l’ancêtre d’Internet : quelques universités et centres de recherche partagent ainsi des données.
  Dans les années 70, les protocoles **TCP/IP** sont définis : ils restent aujourd’hui encore la base de la communication sur Internet.

### 1.2. Internet et Web : deux notions différentes

Il est important de distinguer :

* **Internet** : réseau mondial d’ordinateurs interconnectés, basé sur les protocoles TCP/IP.
* **World Wide Web (Web)** : un service qui fonctionne au-dessus d’Internet, permettant de consulter des **pages** via un **navigateur**.

On peut résumer ainsi :

> Internet est l’infrastructure (l’autoroute),
> le Web est un des services qui l’utilisent (une des voitures qui circulent dessus).

### 1.3. Tim Berners-Lee et la naissance du Web

En **1989**, **Tim Berners-Lee**, chercheur au **CERN**, cherche un moyen de faciliter le partage de documents scientifiques entre chercheurs.
Il propose un système fondé sur trois idées :

1. Un **langage de description de documents** :
   **HTML – HyperText Markup Language**.

2. Un **système d’adressage unique** :
   **URL – Uniform Resource Locator**.

3. Un **protocole de communication** :
   **HTTP – HyperText Transfer Protocol**.

Il développe aussi le premier **navigateur Web** (WorldWideWeb, renommé ensuite Nexus).

En **1990**, ces briques sont combinées : c’est la naissance du **World Wide Web**.

---

## 2. Qu’est-ce que le HTML ?

### 2.1. Définition

**HTML (HyperText Markup Language)** est un **langage de balisage** utilisé pour structurer le contenu d’une page web.

Important :

* HTML **n’est pas** un langage de programmation (comme JavaScript, Python ou Java).
* HTML est un langage **descriptif** : il décrit la nature et la hiérarchie des éléments d’une page (titres, paragraphes, images, liens, formulaires, etc.).
* Il s’appuie sur des **balises** (ou *tags*), généralement par paires :
  `balise ouvrante` / `balise fermante`.

Exemple simple :

```html
<p>Ceci est un paragraphe.</p>
```

### 2.2. Le concept d’hypertexte

Le terme **HyperText** renvoie à la capacité de lier des documents entre eux.

Exemple :

```html
<a href="https://www.example.com">Visiter le site Example</a>
```

Ce lien permet de passer d’un document à un autre.
La **navigation** entre documents est au cœur du Web, d’où l’image de **toile (web)**.

---

## 3. Structure d’un document HTML5

### 3.1. Structure minimale

Une page HTML5 standard possède toujours la structure suivante :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Ma première page HTML</title>
</head>
<body>
  <h1>Bonjour, monde</h1>
  <p>Ceci est ma première page en HTML.</p>
</body>
</html>
```

Décomposition :

* `<!DOCTYPE html>` : indique au navigateur que le document est en **HTML5**.
* `<html lang="fr">` : élément racine, `lang="fr"` précise la langue du document (utile pour l’accessibilité et le référencement).
* `<head>` : contient des **métadonnées** (titre, encodage, description, etc.).
* `<body>` : contient le **contenu visible** de la page (textes, images, liens, formulaires…).

### 3.2. Métadonnées importantes dans `<head>`

Exemple plus complet :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Page d'exemple pour découvrir HTML5.">
  <title>Découverte de HTML5</title>
</head>
<body>
  <h1>Découverte de HTML5</h1>
</body>
</html>
```

* `<meta charset="UTF-8">` : indique l’encodage de caractères (UTF-8, standard moderne).
* `<meta name="viewport" ...>` : nécessaire pour une bonne adaptation sur mobiles (responsive).
* `<meta name="description" ...>` : résumé de la page, utilisé par les moteurs de recherche.
* `<title>` : titre qui apparaît dans l’onglet du navigateur.

---

## 4. Éléments de base : titres, paragraphes, séparateurs

### 4.1. Les titres : `<h1>` à `<h6>`

Les balises de titre structurent la hiérarchie du contenu.

```html
<h1>Titre principal de la page</h1>
<h2>Sous-titre de section</h2>
<h3>Sous-section</h3>
```

* `<h1>` : titre principal, unique par page idéalement.
* `<h2>` à `<h6>` : sous-niveaux hiérarchiques.

Exemple structuré :

```html
<h1>Documentation du projet</h1>

<h2>Introduction</h2>
<p>Ce document présente le projet.</p>

<h2>Architecture</h2>
<h3>Front-end</h3>
<p>Description de la partie front-end.</p>
<h3>Back-end</h3>
<p>Description de la partie back-end.</p>
```

### 4.2. Les paragraphes : `<p>`

```html
<p>Ceci est un paragraphe de texte normal.</p>
<p>Chaque paragraphe est séparé des autres.</p>
```

### 4.3. Saut de ligne `<br>` et ligne horizontale `<hr>`

* `<br>` : force un **retour à la ligne** à l’intérieur d’un paragraphe.
* `<hr>` : représente un **séparateur thématique** (ligne horizontale).

Exemple :

```html
<p>Ligne 1<br>Ligne 2<br>Ligne 3</p>

<hr>

<p>Nouvelle section après une séparation visuelle.</p>
```

---

## 5. Attributs HTML

### 5.1. Syntaxe générale

Les **attributs** donnent des informations supplémentaires sur une balise.

```html
<balise attribut="valeur">Contenu</balise>
```

Exemples courants :

```html
<p id="intro">Paragraphe d'introduction.</p>
<p title="Info bulle">Survolez ce texte pour voir l'info bulle.</p>
<img src="photo.jpg" alt="Portrait de l'auteur">
```

Attributs très utilisés :

* `id` : identifiant unique dans la page.
* `class` : classification (souvent utilisée pour le style ou le JS, même si nous restons ici en HTML).
* `title` : info-bulle.
* `src` : source d’une image ou d’un média.
* `alt` : texte alternatif d’une image (accessibilité).
* `href` : URL cible d’un lien.
* `lang` : langue d’un élément.

---

## 6. Mise en forme sémantique du texte

### 6.1. Importance, emphase et surlignage

```html
<p>Ce texte est <strong>très important</strong> dans le contexte.</p>
<p>Ce mot est <em>mis en avant</em> par emphase.</p>
<p>Ce terme est <mark>à retenir</mark> pour l'examen.</p>
```

* `<strong>` : importance forte (souvent rendu en gras, mais ce qui compte est le sens).
* `<em>` : emphase (souvent rendu en italique).
* `<mark>` : mise en évidence (fond surligné).

### 6.2. Texte secondaire et annotations

```html
<p>Texte principal. <small>Note de bas de page ou information secondaire.</small></p>
```

### 6.3. Indices, exposants, code, texte préformaté

```html
<p>Formule chimique : H<sub>2</sub>O</p>
<p>Formule mathématique : E = mc<sup>2</sup></p>

<p>Code en ligne : <code>console.log("Hello");</code></p>

<pre>
Ligne 1
    Ligne 2 indentée
        Ligne 3
</pre>
```

* `<sub>` : indice.
* `<sup>` : exposant.
* `<code>` : fragment de code.
* `<pre>` : texte préservant les espaces et retours à la ligne.

### 6.4. Citations

```html
<p>Comme le dit souvent mon formateur : <q>Le HTML structure, le CSS embellit.</q></p>

<blockquote>
  Ceci est une citation plus longue, pouvant s'étendre sur plusieurs lignes.
</blockquote>
```

* `<q>` : citation courte intégrée à une phrase.
* `<blockquote>` : citation longue en bloc.

### 6.5. Abréviations, œuvres citées

```html
<p>Le <abbr title="HyperText Markup Language">HTML</abbr> est à la base du Web.</p>

<p>Le livre <cite>Clean Code</cite> est une référence en développement logiciel.</p>
```

---

## 7. Listes

### 7.1. Liste non ordonnée : `<ul>` / `<li>`

```html
<h2>Technologies étudiées</h2>
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ul>
```

### 7.2. Liste ordonnée : `<ol>` / `<li>`

```html
<h2>Étapes d'installation</h2>
<ol>
  <li>Télécharger l'éditeur de code.</li>
  <li>Installer l'éditeur.</li>
  <li>Créer un premier fichier HTML.</li>
</ol>
```

### 7.3. Liste de définitions : `<dl>`, `<dt>`, `<dd>`

```html
<dl>
  <dt>HTML</dt>
  <dd>Langage de structure des pages web.</dd>

  <dt>CSS</dt>
  <dd>Langage de présentation (mise en forme) des pages.</dd>
</dl>
```

---

## 8. Liens et navigation

### 8.1. Lien simple

```html
<p>Visitez le site de la formation :
  <a href="https://www.kodpix.com">Kodpix</a>
</p>
```

### 8.2. Lien ouvrant un nouvel onglet

```html
<a href="https://www.w3.org" target="_blank" rel="noopener noreferrer">
  Site du W3C
</a>
```

* `target="_blank"` : ouvre dans un nouvel onglet.
* `rel="noopener noreferrer"` : recommandé pour des raisons de sécurité.

### 8.3. Lien interne (ancre)

```html
<a href="#contact">Aller à la section contact</a>

<!-- Plus bas dans la page -->
<h2 id="contact">Contact</h2>
<p>Formulaire de contact prochainement.</p>
```

### 8.4. Lien de téléchargement

```html
<a href="programme_formation.pdf" download>
  Télécharger le programme de formation
</a>
```

---

## 9. Images et médias

### 9.1. Image simple

```html
<img src="portrait.jpg" alt="Photo du formateur" width="200" height="200">
```

* `src` : chemin vers l’image.
* `alt` : description textuelle (obligatoire pour l’accessibilité).
* `width`, `height` : dimensions (en pixels).

### 9.2. Figure et légende

```html
<figure>
  <img src="schema-html.png" alt="Schéma de la structure HTML">
  <figcaption>Figure 1 – Structure d'une page HTML5.</figcaption>
</figure>
```

### 9.3. Audio

```html
<audio controls>
  <source src="podcast.mp3" type="audio/mpeg">
  Votre navigateur ne supporte pas l'élément audio.
</audio>
```

### 9.4. Vidéo

```html
<video controls width="320">
  <source src="video_demo.mp4" type="video/mp4">
  Votre navigateur ne supporte pas l'élément vidéo.
</video>
```

### 9.5. Sous-titres (track)

```html
<video controls>
  <source src="presentation.mp4" type="video/mp4">
  <track src="sous-titres.vtt" kind="subtitles" srclang="fr" label="Français">
</video>
```

---

## 10. Éléments de structure : bloc et inline

### 10.1. Éléments de type bloc

Les éléments de type **bloc** prennent toute la largeur disponible et commencent sur une nouvelle ligne.

Exemples : `<div>`, `<p>`, `<h1>`…

```html
<div>
  <h2>Titre de section</h2>
  <p>Paragraphe dans un bloc.</p>
</div>
```

### 10.2. Éléments de type inline

Les éléments **inline** occupent uniquement la largeur nécessaire à leur contenu.

Exemples : `<span>`, `<a>`, `<strong>`, `<em>`…

```html
<p>Ce texte contient un <span>élément en ligne</span> dans un paragraphe.</p>
```

### 10.3. `<div>` et `<span>`

* `<div>` : conteneur générique de type bloc.
* `<span>` : conteneur générique de type inline.

```html
<div>
  <p>Texte avec un <span>mot mis en avant</span> au milieu.</p>
</div>
```

---

## 11. HTML5 sémantique : les grandes zones structurelles

### 11.1. Structure générale d’une page

```html
<header>
  <h1>Nom du site</h1>
  <nav>
    <a href="#accueil">Accueil</a>
    <a href="#services">Services</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<main>
  <section id="accueil">
    <h2>Accueil</h2>
    <p>Bienvenue sur notre site.</p>
  </section>

  <section id="services">
    <h2>Nos services</h2>
    <article>
      <h3>Service 1</h3>
      <p>Description du service 1.</p>
    </article>
    <article>
      <h3>Service 2</h3>
      <p>Description du service 2.</p>
    </article>
  </section>

  <aside>
    <h2>Actualités</h2>
    <p>Dernières nouvelles de l'entreprise.</p>
  </aside>
</main>

<footer>
  <p>© 2025 – Nom de l'entreprise</p>
</footer>
```

### 11.2. Rôle de chaque balise

* `<header>` : en-tête d’une page ou d’une section (logo, titre, navigation).
* `<nav>` : zone de navigation principale.
* `<main>` : contenu principal de la page (unique).
* `<section>` : section thématique (groupe logique de contenu).
* `<article>` : contenu autonome (article de blog, fiche produit, etc.).
* `<aside>` : contenu secondaire (publicités, liens, encadrés).
* `<footer>` : pied de page (mentions légales, copyright, contacts).

---

## 12. Tableaux

### 12.1. Tableau simple

```html
<table border="1">
  <tr>
    <th>Nom</th>
    <th>Âge</th>
  </tr>
  <tr>
    <td>Marie</td>
    <td>22</td>
  </tr>
  <tr>
    <td>Lucas</td>
    <td>24</td>
  </tr>
</table>
```

### 12.2. Tableau structuré complet

```html
<table border="1">
  <caption>Liste des apprenants</caption>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Âge</th>
      <th>Formation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Anne</td>
      <td>25</td>
      <td>Développement Web</td>
    </tr>
    <tr>
      <td>Karim</td>
      <td>27</td>
      <td>Cybersécurité</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Total : 2 apprenants</td>
    </tr>
  </tfoot>
</table>
```

---

## 13. Formulaires HTML5

### 13.1. Structure de base

```html
<form action="#" method="post">
  <fieldset>
    <legend>Informations personnelles</legend>

    <label for="nom">Nom :</label>
    <input type="text" id="nom" name="nom" required><br>

    <label for="email">Email :</label>
    <input type="email" id="email" name="email"><br>

    <input type="submit" value="Envoyer">
  </fieldset>
</form>
```

### 13.2. Types d’input HTML5

Exemples :

```html
<input type="text" name="texte">
<input type="password" name="motdepasse">
<input type="email" name="email">
<input type="number" name="age" min="0" max="120">
<input type="date" name="date_naissance">
<input type="color" name="couleur_preferee">
<input type="file" name="cv">
<input type="checkbox" name="newsletter">
<input type="radio" name="sexe" value="Homme">
<input type="radio" name="sexe" value="Femme">
<input type="submit" value="Envoyer">
<input type="reset" value="Effacer">
```

### 13.3. Listes déroulantes et datalist

```html
<label for="pays">Pays :</label>
<select id="pays" name="pays">
  <option value="fr">France</option>
  <option value="be">Belgique</option>
  <option value="ch">Suisse</option>
</select>
```

```html
<label for="navigateur">Navigateur :</label>
<input list="navigateur-list" id="navigateur" name="navigateur">
<datalist id="navigateur-list">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Edge">
</datalist>
```

### 13.4. Zone de texte multi-lignes

```html
<label for="message">Message :</label><br>
<textarea id="message" name="message" rows="4" cols="40"></textarea>
```

---

## 14. Métadonnées et structure du document

Rappel des balises principales dans `<head>` :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Titre de la page</title>
  <meta name="description" content="Description de la page">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
  <!-- Contenu -->
</body>
</html>
```

Principales balises :

* `<!DOCTYPE html>` : type de document.
* `<html>` : racine du document.
* `<head>` : métadonnées.
* `<meta>` : encodage, description, viewport, etc.
* `<title>` : titre de la page.

---

## 15. Entités HTML, symboles et caractères spéciaux

Certains caractères spéciaux doivent être écrits sous forme d’**entités** :

| Caractère              | Entité HTML |
| ---------------------- | ----------- |
| `<`                    | `&lt;`      |
| `>`                    | `&gt;`      |
| `&`                    | `&amp;`     |
| `"`                    | `&quot;`    |
| `'`                    | `&apos;`    |
| ` ` (espace insécable) | `&nbsp;`    |

Exemples :

```html
<p>Afficher un chevron : &lt;div&gt;</p>
<p>Copyright : &copy; 2025</p>
<p>Flèche : &rarr;</p>
```

---

## 16. Balises obsolètes et bonnes pratiques

### 16.1. Balises à éviter

Certaines balises anciennes ne doivent plus être utilisées :

| Ancienne balise | Remplacement                       |
| --------------- | ---------------------------------- |
| `<center>`      | Mise en forme via CSS              |
| `<font>`        | CSS (`font-family`, `color`, etc.) |
| `<u>`           | CSS `text-decoration: underline;`  |
| `<marquee>`     | Animations CSS ou JavaScript       |

### 16.2. Bonnes pratiques

* Utiliser des balises **sémantiques** dès que possible (`<header>`, `<main>`, `<article>`, etc.).
* Respecter la **hiérarchie des titres** (`<h1>` puis `<h2>`, etc.).
* Toujours fournir un attribut `alt` descriptif pour les images.
* Systématiquement vérifier son code avec un validateur (W3C).
* Indenter le code pour le rendre lisible.
* soit transformer ce module en **support prêt à imprimer** (avec un plan numéroté propre, introduction de chapitre, conclusion et exercices),
* soit en **version “enseignant”** avec des encadrés “À expliquer à l’oral”, “Démonstration live”, “Questions à poser aux étudiants”.
