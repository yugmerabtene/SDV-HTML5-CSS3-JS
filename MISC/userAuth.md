* Inscription
* Connexion
* Vérification du mot de passe hashé
* Sessions
* Redirection vers page protégée
* Déconnexion

Le tout **sans POO**, uniquement des **fonctions**.

---

# 1. `fonctions.php` — Toutes les fonctions

```php
<?php

// ---------------------------------------
// Connexion PDO à la base de données
// ---------------------------------------
function getDB() {
    $host = "localhost";
    $dbname = "gestion_users";
    $username = "root";
    $password = "";

    try {
        return new PDO(
            "mysql:host=$host;dbname=$dbname;charset=utf8",
            $username,
            $password,
            [
                PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
                PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
                PDO::ATTR_EMULATE_PREPARES => false
            ]
        );
    } catch (PDOException $e) {
        die("Erreur de connexion BDD : " . $e->getMessage());
    }
}



// ---------------------------------------
// Vérifie si un email existe déjà
// ---------------------------------------
function emailExiste($pdo, $email) {
    $stmt = $pdo->prepare("SELECT id FROM users WHERE email = ?");
    $stmt->execute([$email]);
    return $stmt->rowCount() > 0;
}



// ---------------------------------------
// Inscrire un utilisateur
// ---------------------------------------
function creerUtilisateur($pdo, $nom, $email, $passwordHash) {
    $stmt = $pdo->prepare("INSERT INTO users (nom, email, password) VALUES (?, ?, ?)");
    return $stmt->execute([$nom, $email, $passwordHash]);
}



// ---------------------------------------
// Récupérer un utilisateur par email
// ---------------------------------------
function getUserByEmail($pdo, $email) {
    $stmt = $pdo->prepare("SELECT * FROM users WHERE email = ?");
    $stmt->execute([$email]);
    return $stmt->fetch();
}



// ---------------------------------------
// Vérifier si un utilisateur est connecté
// ---------------------------------------
function isLogged() {
    return isset($_SESSION['user_id']);
}



// ---------------------------------------
// Bloquer une page si non connecté
// ---------------------------------------
function requireLogin() {
    if (!isLogged()) {
        header("Location: login.php");
        exit;
    }
}

?>
```

---

# 2. Table SQL à créer dans MySQL

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nom VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

# 3. `index.html` — Accueil

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Accueil</title>
</head>
<body>

<h2>Bienvenue</h2>

<a href="register.php">S'inscrire</a><br>
<a href="login.php">Se connecter</a>

</body>
</html>
```

---

# 4. `register.php` — Inscription

```php
<?php
session_start();
require "fonctions.php";

$pdo = getDB();

if ($_SERVER['REQUEST_METHOD'] === 'POST') {

    $nom = trim($_POST['nom']);
    $email = trim($_POST['email']);
    $password = trim($_POST['password']);

    if ($nom === "" || $email === "" || $password === "") {
        die("Tous les champs sont obligatoires.");
    }

    if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        die("Email invalide.");
    }

    if (emailExiste($pdo, $email)) {
        die("Cet email existe déjà.");
    }

    $passwordHash = password_hash($password, PASSWORD_DEFAULT);

    if (creerUtilisateur($pdo, $nom, $email, $passwordHash)) {
        echo "Inscription réussie. <a href='login.php'>Se connecter</a>";
    } else {
        echo "Erreur lors de l'inscription.";
    }
}
?>

<!DOCTYPE html>
<html>
<body>
<h2>Inscription</h2>

<form method="POST">
    Nom :<br>
    <input type="text" name="nom" required><br><br>
    
    Email :<br>
    <input type="email" name="email" required><br><br>
    
    Mot de passe :<br>
    <input type="password" name="password" required><br><br>
    
    <button type="submit">S'inscrire</button>
</form>
</body>
</html>
```

---

# 5. `login.php` — Connexion

```php
<?php
session_start();
require "fonctions.php";

$pdo = getDB();

if ($_SERVER['REQUEST_METHOD'] === 'POST') {

    $email = trim($_POST['email']);
    $password = trim($_POST['password']);

    if ($email === "" || $password === "") {
        die("Veuillez remplir tous les champs.");
    }

    $user = getUserByEmail($pdo, $email);

    if (!$user) {
        die("Email ou mot de passe incorrect.");
    }

    if (!password_verify($password, $user['password'])) {
        die("Email ou mot de passe incorrect.");
    }

    $_SESSION['user_id'] = $user['id'];
    $_SESSION['user_nom'] = $user['nom'];

    header("Location: tableau.php");
    exit;
}
?>

<!DOCTYPE html>
<html>
<body>

<h2>Connexion</h2>

<form method="POST">
    Email :<br>
    <input type="email" name="email" required><br><br>

    Mot de passe :<br>
    <input type="password" name="password" required><br><br>

    <button type="submit">Se connecter</button>
</form>

</body>
</html>
```

---

# 6. `tableau.php` — Page protégée

```php
<?php
session_start();
require "fonctions.php";
requireLogin();
?>

<!DOCTYPE html>
<html>
<body>

<h2>Tableau de bord</h2>

Bonjour <?php echo htmlspecialchars($_SESSION['user_nom']); ?>

<br><br>
<a href="logout.php">Se déconnecter</a>

</body>
</html>
```

---

# 7. `logout.php` — Déconnexion

```php
<?php
session_start();
session_destroy();
header("Location: login.php");
exit;
```

---

# EXPLICATION DÉTAILLÉE DE CHAQUE ÉLÉMENT

## 1. `getDB()`

* Établit une connexion sécurisée PDO.
* Active le mode exception.
* Désactive l'émulation (plus sûr).
* Renvoie un objet `$pdo`.

## 2. `emailExiste()`

* Vérifie si un email existe déjà dans la table.
* Protection contre l’injection SQL.

## 3. `creerUtilisateur()`

* Insère un utilisateur avec un mot de passe hashé.
* Utilise une requête préparée.

## 4. `getUserByEmail()`

* Permet de récupérer l’utilisateur pour le login.

## 5. `requireLogin()`

* Bloque l’accès à une page si l’utilisateur n’est pas connecté.
* Redirige vers `login.php`.

## 6. Inscription (`register.php`)

* Récupère les données `POST`.
* Nettoie (`trim`).
* Vérifie si les champs sont remplis.
* Vérifie email valide.
* Vérifie doublon.
* Hash du mot de passe.
* Insertion BDD.

## 7. Connexion (`login.php`)

* Vérifie que l’email existe.
* Vérifie le mot de passe avec `password_verify()`.
* Stocke l'ID utilisateur dans `$_SESSION`.
* Redirige vers tableau.

## 8. `tableau.php`

* Page protégée.
* Affiche le nom de l'utilisateur connecté.

## 9. Déconnexion

* Supprime toutes les variables de session.
* Redirige vers login.
