** Calculatrice : 

* **3 fonctions PHP** :

  * `addition()`
  * `soustraction()`
  * `multiplication()`
* **Un formulaire simple**
* Un **select** qui permet de choisir l’opération
* Le script appelle **automatiquement la bonne fonction selon l’opération choisie**

Version claire, simple, parfaitement structurée.

---

# Code complet : calculatrice avec fonctions + sélection d’opération

```php
<?php
// ---------- Fonctions ----------
function addition($a, $b) {
    return $a + $b;
}

function soustraction($a, $b) {
    return $a - $b;
}

function multiplication($a, $b) {
    return $a * $b;
}

// ---------- Variables ----------
$nombre1 = "";
$nombre2 = "";
$operation = "";
$resultat = "";

// ---------- Logique lors du POST ----------
if ($_SERVER['REQUEST_METHOD'] === 'POST') {

    $nombre1 = $_POST['nombre1'];
    $nombre2 = $_POST['nombre2'];
    $operation = $_POST['operation'];

    // Appel de la bonne fonction selon l’opération choisie
    if ($operation === "addition") {
        $resultat = addition($nombre1, $nombre2);
    } 
    elseif ($operation === "soustraction") {
        $resultat = soustraction($nombre1, $nombre2);
    }
    elseif ($operation === "multiplication") {
        $resultat = multiplication($nombre1, $nombre2);
    }

    // Affichage du résultat
    echo "<h2>Résultat : $resultat</h2>";
}
?>

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculatrice avancée</title>
</head>
<body>

<h1>Calculatrice (Fonctions)</h1>

<form action="" method="post">

    <label for="nombre1">Nombre 1 :</label>
    <input type="number" id="nombre1" name="nombre1" required>
    <br><br>

    <label for="nombre2">Nombre 2 :</label>
    <input type="number" id="nombre2" name="nombre2" required>
    <br><br>

    <label for="operation">Opération :</label>
    <select id="operation" name="operation" required>
        <option value="addition">Addition</option>
        <option value="soustraction">Soustraction</option>
        <option value="multiplication">Multiplication</option>
    </select>
    <br><br>

    <button type="submit">Calculer</button>

</form>

</body>
</html>
```

---

# Explication du fonctionnement

### 1. Les fonctions

```php
function addition($a, $b) { return $a + $b; }
function soustraction($a, $b) { return $a - $b; }
function multiplication($a, $b) { return $a * $b; }
```

Elles font juste le calcul.

---

### 2. Le switch logique

On regarde l’opération choisie :

```php
if ($operation === "addition") { ... }
elseif ($operation === "soustraction") { ... }
elseif ($operation === "multiplication") { ... }
```

Et on appelle la fonction correspondante.



# Version avec switch / case

```php
<?php
// ---------- Fonctions ----------
function addition($a, $b) {
    return $a + $b;
}

function soustraction($a, $b) {
    return $a - $b;
}

function multiplication($a, $b) {
    return $a * $b;
}

// ---------- Variables ----------
$nombre1 = "";
$nombre2 = "";
$operation = "";
$resultat = "";

// ---------- Logique lors du POST ----------
if ($_SERVER['REQUEST_METHOD'] === 'POST') {

    $nombre1 = $_POST['nombre1'];
    $nombre2 = $_POST['nombre2'];
    $operation = $_POST['operation'];

    // Sélection via switch/case
    switch ($operation) {
        case "addition":
            $resultat = addition($nombre1, $nombre2);
            break;

        case "soustraction":
            $resultat = soustraction($nombre1, $nombre2);
            break;

        case "multiplication":
            $resultat = multiplication($nombre1, $nombre2);
            break;

        default:
            $resultat = "Opération inconnue.";
            break;
    }

    // Affichage du résultat
    echo "<h2>Résultat : $resultat</h2>";
}
?>

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculatrice switch-case</title>
</head>
<body>

<h1>Calculatrice (Switch Case)</h1>

<form action="" method="post">

    <label for="nombre1">Nombre 1 :</label>
    <input type="number" id="nombre1" name="nombre1" required>
    <br><br>

    <label for="nombre2">Nombre 2 :</label>
    <input type="number" id="nombre2" name="nombre2" required>
    <br><br>

    <label for="operation">Opération :</label>
    <select id="operation" name="operation" required>
        <option value="addition">Addition</option>
        <option value="soustraction">Soustraction</option>
        <option value="multiplication">Multiplication</option>
    </select>
    <br><br>

    <button type="submit">Calculer</button>

</form>

</body>
</html>
```

---

# Différences avec la version précédente

Au lieu de :

```php
if (...) { ... }
elseif (...) { ... }
```

On a :

```php
switch ($operation) {
    case "addition": ...
    case "soustraction": ...
    case "multiplication": ...
}
```


