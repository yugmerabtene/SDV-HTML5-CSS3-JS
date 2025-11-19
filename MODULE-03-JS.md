## 1.Architecture

```text
projet-formation-html-css-js/
│
├── index.html                (déjà créé pour HTML/CSS, vous pourrez l’étendre)
├── js-intro.html
├── js-conditions-boucles.html
├── js-fonctions.html
├── js-dom.html
├── js-fetch.html
│
└── assets/
    ├── css/
    │   └── ... (base.css, etc. déjà vus)
    ├── js/
    │   ├── js-intro.js
    │   ├── js-conditions-boucles.js
    │   ├── js-fonctions.js
    │   ├── js-dom.js
    │   └── js-fetch.js
    ├── img/
    └── video/
```

# MODULE-03 – JavaScript

## Objectifs généraux

* Utiliser les instructions de base en JavaScript : **variables**, **conditions**, **boucles**, **fonctions**.
* Manipuler le **DOM** : sélection d’éléments, modification de contenu, création de nœuds, gestion d’événements.
* Effectuer des **requêtes HTTP** avec `fetch`, utiliser les promesses et l’`async/await`.

---

## 1. Introduction et premières instructions – `js-intro.html` + `assets/js/js-intro.js`

### 1.1. Objectif pédagogique

* Comprendre comment relier un fichier JavaScript à une page HTML.
* Découvrir la console, les variables (`let`, `const`), les types simples et l’instruction `console.log`.

### 1.2. Fichier `js-intro.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Introduction à JavaScript</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <script src="assets/js/js-intro.js" defer></script>
</head>
<body>
  <header>
    <h1>Introduction à JavaScript</h1>
    <p>Variables, types et premières instructions.</p>
  </header>

  <main>
    <section>
      <h2>Zone d’affichage</h2>
      <p>Les résultats s’afficheront ici :</p>
      <div id="resultat-intro"></div>
      <p>
        Vous pouvez également ouvrir la console du navigateur
        (F12 ou clic droit → Inspecter → Onglet "Console")
        pour voir les messages générés par JavaScript.
      </p>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour à l’accueil</a></p>
  </footer>
</body>
</html>
```

### 1.3. Fichier `assets/js/js-intro.js`

```js
// assets/js/js-intro.js
// Introduction : variables, types, opérations simples

// Sélection d'un élément du DOM pour afficher un texte
const zoneResultat = document.getElementById("resultat-intro");

// Déclaration de variables
let prenom = "Alice";
const age = 25;
let estEtudiant = true;

// Affichage dans la console (pour le formateur et le débogage)
console.log("Prénom :", prenom);
console.log("Âge :", age);
console.log("Est étudiant :", estEtudiant);

// Concaténation de texte et de variables
const phrase = "Bonjour, je m'appelle " + prenom + " et j'ai " + age + " ans.";

// Opérations simples
const a = 10;
const b = 3;
const somme = a + b;
const produit = a * b;

// Construction d'un texte HTML pour la zone d'affichage
let contenuHtml = "";
contenuHtml += "<p>" + phrase + "</p>";
contenuHtml += "<p>Somme de " + a + " + " + b + " = " + somme + "</p>";
contenuHtml += "<p>Produit de " + a + " × " + b + " = " + produit + "</p>";

// Écriture dans la page
zoneResultat.innerHTML = contenuHtml;
```

### 1.4. Explications – grandes lignes

* `<script src="...js" defer></script>` : charge le fichier JavaScript externe, et exécute le script après le chargement du HTML.
* `document.getElementById("resultat-intro")` : récupération d’un élément du DOM pour y injecter du contenu.
* `let` / `const` :

  * `let` pour une variable dont la valeur peut changer,
  * `const` pour une constante (valeur fixe).
* `console.log()` : très utile pour illustrer et déboguer en cours.
* `innerHTML` : permet d’injecter du HTML (avec prudence en production, mais pédagogique ici).

### 1.5. Instructions / notions utilisées

* Déclaration de variables : `let`, `const`.
* Types simples : `string`, `number`, `boolean`.
* Opérations arithmétiques : `+`, `*`.
* Manipulation de chaînes de caractères.
* Accès au DOM : `document.getElementById`.
* Propriété DOM : `innerHTML`.

---

## 2. Conditions et boucles – `js-conditions-boucles.html` + `assets/js/js-conditions-boucles.js`

### 2.1. Objectif pédagogique

* Utiliser `if / else if / else`.
* Manipuler des comparaisons (`>`, `<`, `===`, `!==`).
* Écrire des boucles `for` et `while`.
* Afficher les résultats dans la page.

### 2.2. Fichier `js-conditions-boucles.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Conditions et boucles en JavaScript</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <script src="assets/js/js-conditions-boucles.js" defer></script>
</head>
<body>
  <header>
    <h1>Conditions et boucles</h1>
    <p>Exemples de if/else, for et while.</p>
  </header>

  <main>
    <section>
      <h2>Exemple de condition</h2>
      <div id="resultat-conditions"></div>
    </section>

    <section>
      <h2>Exemple de boucle for</h2>
      <div id="resultat-for"></div>
    </section>

    <section>
      <h2>Exemple de boucle while</h2>
      <div id="resultat-while"></div>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour à l’accueil</a></p>
  </footer>
</body>
</html>
```

### 2.3. Fichier `assets/js/js-conditions-boucles.js`

```js
// assets/js/js-conditions-boucles.js
// Conditions et boucles

const zoneConditions = document.getElementById("resultat-conditions");
const zoneFor = document.getElementById("resultat-for");
const zoneWhile = document.getElementById("resultat-while");

// ----- Conditions -----

const note = 14;
let appreciation = "";

if (note >= 16) {
  appreciation = "Excellent";
} else if (note >= 12) {
  appreciation = "Assez bien";
} else if (note >= 10) {
  appreciation = "Passable";
} else {
  appreciation = "Insuffisant";
}

zoneConditions.innerHTML = "<p>Note : " + note + " → " + appreciation + "</p>";

// ----- Boucle for -----

let listeFor = "<ul>";
for (let i = 1; i <= 5; i++) {
  listeFor += "<li>Itération n°" + i + "</li>";
}
listeFor += "</ul>";

zoneFor.innerHTML = listeFor;

// ----- Boucle while -----

let compteur = 0;
let texteWhile = "<p>Comptage avec while : ";

while (compteur < 5) {
  texteWhile += compteur + " ";
  compteur++;
}

texteWhile += "</p>";

zoneWhile.innerHTML = texteWhile;
```

### 2.4. Explications – grandes lignes

* `if / else if / else` permet de prendre des décisions en fonction de valeurs (ici, une note).
* `for (let i = 1; i <= 5; i++)` illustre une boucle déterministe (nombre d’itérations connu).
* `while (compteur < 5)` illustre une boucle conditionnelle (s’exécute tant que la condition est vraie).

### 2.5. Instructions / notions utilisées

* Structures de contrôle : `if`, `else if`, `else`.
* Comparateurs : `>=`, `<`.
* Boucle `for`.
* Boucle `while`.
* Manipulation de chaînes + DOM : construction de listes en HTML (`<ul>`, `<li>`).

---

## 3. Fonctions – `js-fonctions.html` + `assets/js/js-fonctions.js`

### 3.1. Objectif pédagogique

* Déclarer des fonctions classiques et des fonctions fléchées.
* Passer des paramètres, retourner des valeurs.
* Séparer la logique (calcul) de l’affichage (DOM).

### 3.2. Fichier `js-fonctions.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Fonctions en JavaScript</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <script src="assets/js/js-fonctions.js" defer></script>
</head>
<body>
  <header>
    <h1>Fonctions en JavaScript</h1>
    <p>Déclaration, paramètres, retours de valeurs.</p>
  </header>

  <main>
    <section>
      <h2>Calcul de la somme</h2>
      <div id="resultat-fonctions"></div>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour à l’accueil</a></p>
  </footer>
</body>
</html>
```

### 3.3. Fichier `assets/js/js-fonctions.js`

```js
// assets/js/js-fonctions.js
// Fonctions classiques et fonctions fléchées

const zoneFonctions = document.getElementById("resultat-fonctions");

// Fonction classique
function addition(a, b) {
  return a + b;
}

// Fonction fléchée
const multiplication = (a, b) => {
  return a * b;
};

// Utilisation des fonctions
const x = 7;
const y = 5;

const resultatAddition = addition(x, y);
const resultatMultiplication = multiplication(x, y);

let contenu = "<p>Arguments : x = " + x + ", y = " + y + "</p>";
contenu += "<p>addition(x, y) = " + resultatAddition + "</p>";
contenu += "<p>multiplication(x, y) = " + resultatMultiplication + "</p>";

zoneFonctions.innerHTML = contenu;
```

### 3.4. Explications – grandes lignes

* La fonction `addition` est déclarée de manière classique : `function addition(a, b)`.
* La fonction `multiplication` illustre la **syntaxe fléchée** ES6 : `const multiplication = (a, b) => { ... }`.
* Les fonctions prennent des **paramètres** et retournent des **valeurs** avec `return`.

### 3.5. Instructions / notions utilisées

* Déclaration de fonction classique : `function nom(...) { ... }`.
* Fonction fléchée : `const f = (...) => { ... }`.
* Paramètres, valeurs de retour.
* Injection du résultat dans le DOM.

---

## 4. Manipulation du DOM et événements – `js-dom.html` + `assets/js/js-dom.js`

### 4.1. Objectif pédagogique

* Sélectionner des éléments : `getElementById`, `querySelector`, `querySelectorAll`.
* Modifier du contenu (`textContent`, `innerHTML`), les attributs et les classes.
* Réagir aux événements (`click`, `input`).

### 4.2. Fichier `js-dom.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>DOM et événements en JavaScript</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <script src="assets/js/js-dom.js" defer></script>
</head>
<body>
  <header>
    <h1>Manipulation du DOM</h1>
    <p>Sélection d’éléments, modification et événements.</p>
  </header>

  <main>
    <section>
      <h2>Modifier le contenu</h2>
      <p id="texte-a-modifier">Texte initial.</p>
      <button id="btn-modifier">Modifier le texte</button>
    </section>

    <section>
      <h2>Création d’éléments</h2>
      <button id="btn-ajouter">Ajouter un élément à la liste</button>
      <ul id="liste-elements"></ul>
    </section>

    <section>
      <h2>Réagir à la saisie utilisateur</h2>
      <label for="champ-nom">Votre nom :</label>
      <input type="text" id="champ-nom" placeholder="Saisissez votre nom">
      <p id="message-nom"></p>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour à l’accueil</a></p>
  </footer>
</body>
</html>
```

### 4.3. Fichier `assets/js/js-dom.js`

```js
// assets/js/js-dom.js
// Manipulation du DOM et gestion d'événements

// Sélection des éléments
const paragraphe = document.getElementById("texte-a-modifier");
const boutonModifier = document.getElementById("btn-modifier");

const boutonAjouter = document.getElementById("btn-ajouter");
const listeElements = document.getElementById("liste-elements");

const champNom = document.getElementById("champ-nom");
const messageNom = document.getElementById("message-nom");

// ----- Modification de texte au clic -----

boutonModifier.addEventListener("click", () => {
  paragraphe.textContent = "Le texte a été modifié par JavaScript.";
});

// ----- Création dynamique d'éléments -----

let compteurElements = 0;

boutonAjouter.addEventListener("click", () => {
  compteurElements++;

  const nouvelElement = document.createElement("li");
  nouvelElement.textContent = "Élément créé n°" + compteurElements;

  listeElements.appendChild(nouvelElement);
});

// ----- Réaction à la saisie utilisateur -----

champNom.addEventListener("input", () => {
  const nomSaisi = champNom.value;

  if (nomSaisi.trim() === "") {
    messageNom.textContent = "";
  } else {
    messageNom.textContent = "Bonjour, " + nomSaisi + " !";
  }
});
```

### 4.4. Explications – grandes lignes

* `addEventListener("click", ...)` et `addEventListener("input", ...)` permettent de réagir aux actions de l’utilisateur.
* `document.createElement("li")` et `appendChild` permettent de créer et insérer de nouveaux éléments dans la page.
* `textContent` est utilisé pour modifier le texte sans interpréter de HTML.

### 4.5. Instructions / notions utilisées

* Sélection DOM : `getElementById`.
* Création et insertion d’éléments : `createElement`, `appendChild`.
* Événements : `addEventListener` avec `click` et `input`.
* Gestion de la saisie utilisateur (`value`, `trim`).

---

## 5. Requêtes HTTP avec fetch et asynchrone – `js-fetch.html` + `assets/js/js-fetch.js`

### 5.1. Objectif pédagogique

* Découvrir le modèle asynchrone en JavaScript.
* Utiliser `fetch` pour envoyer une requête HTTP.
* Gérer les promesses avec `then` ou avec `async/await`.
* Afficher des données récupérées dans le DOM.

> Pour vos démonstrations, vous pouvez utiliser une API publique de test, par exemple `https://jsonplaceholder.typicode.com/users`.
> L’exemple ci-dessous l’utilise.

### 5.2. Fichier `js-fetch.html`

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Requêtes HTTP avec fetch</title>
  <link rel="stylesheet" href="assets/css/base.css">
  <script src="assets/js/js-fetch.js" defer></script>
</head>
<body>
  <header>
    <h1>Requêtes HTTP et asynchrone</h1>
    <p>Exemple avec l'API JSONPlaceholder.</p>
  </header>

  <main>
    <section>
      <h2>Liste des utilisateurs (API de test)</h2>
      <button id="btn-charger">Charger les utilisateurs</button>
      <div id="zone-erreur"></div>
      <ul id="liste-utilisateurs"></ul>
    </section>
  </main>

  <footer>
    <p><a href="index.html">Retour à l’accueil</a></p>
  </footer>
</body>
</html>
```

### 5.3. Fichier `assets/js/js-fetch.js`

```js
// assets/js/js-fetch.js
// Requêtes HTTP avec fetch et async/await

const boutonCharger = document.getElementById("btn-charger");
const listeUtilisateurs = document.getElementById("liste-utilisateurs");
const zoneErreur = document.getElementById("zone-erreur");

// Fonction asynchrone pour récupérer des données
async function chargerUtilisateurs() {
  // Réinitialisation de l'affichage
  listeUtilisateurs.innerHTML = "";
  zoneErreur.textContent = "";

  try {
    const reponse = await fetch("https://jsonplaceholder.typicode.com/users");

    if (!reponse.ok) {
      throw new Error("Erreur HTTP : " + reponse.status);
    }

    const utilisateurs = await reponse.json();

    // Affichage des utilisateurs dans la liste
    utilisateurs.forEach((utilisateur) => {
      const li = document.createElement("li");
      li.textContent = utilisateur.name + " – " + utilisateur.email;
      listeUtilisateurs.appendChild(li);
    });
  } catch (erreur) {
    zoneErreur.textContent = "Impossible de charger les données : " + erreur.message;
  }
}

// Lancement au clic sur le bouton
boutonCharger.addEventListener("click", () => {
  chargerUtilisateurs();
});
```

### 5.4. Explications – grandes lignes

* `async function chargerUtilisateurs()` : permet d’utiliser `await` à l’intérieur de la fonction.
* `await fetch(...)` : envoie une requête HTTP et attend la réponse de manière asynchrone.
* `response.ok` et `response.status` permettent de gérer les erreurs HTTP.
* `response.json()` transforme la réponse JSON en objet JavaScript.
* `try { ... } catch (erreur) { ... }` permet de gérer proprement les erreurs (réseau, HTTP, etc.).

### 5.5. Instructions / notions utilisées

* `fetch(url)` : envoi d’une requête HTTP GET.
* Promesse + `async/await`.
* Gestion d’erreur avec `try/catch`.
* Boucle implicite avec `forEach` sur un tableau d’objets.
* Insertion dans le DOM d’une liste dynamique.
