# 1. Mettre un projet existant sous Git

On part du principe que vous avez déjà un dossier de projet, par exemple :

```bash
~/projets/chat-solidaire/
```

## 1.1. Initialiser le dépôt

Dans le dossier du projet :

```bash
cd ~/projets/chat-solidaire
git init
```

`git init` crée le sous-répertoire `.git` et transforme le dossier en dépôt Git. ([Git][1])

Depuis Git 2.28+, vous pouvez aussi définir la branche initiale directement :

```bash
git init -b main
```

ou configurer globalement :

```bash
git config --global init.defaultBranch main
```

## 1.2. Configurer votre identité (global)

Une fois pour toutes sur la machine :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "vous@example.com"
git config --global color.ui auto
```

`git config` écrit ces valeurs dans `~/.gitconfig`. ([Git][2])

Vérifier :

```bash
git config --list
```

## 1.3. Premier commit

1. Vérifier l’état :

```bash
git status
```

2. Ajouter tous les fichiers du site :

```bash
git add .
```

3. Créer le premier commit :

```bash
git commit -m "Initialisation du site statique"
```

`git add` place les fichiers dans la staging area, `git commit` enregistre un snapshot complet. ([Git][3])

---

# 2. Concepts clés et workflow de base

## 2.1. Les trois zones Git

* **Working directory** : vos fichiers dans le système de fichiers.
* **Staging area (index)** : ce qui sera inclus dans le prochain commit (`git add`).
* **Repository (`.git`)** : l’historique de commits.

Cycle typique :

1. Modifier un fichier (`index.html`, `assets/css/styles.css`, etc.).
2. Vérifier l’état : `git status`.
3. Préparer les fichiers : `git add ...`.
4. Commiter : `git commit -m "Message"`.

## 2.2. Commandes essentielles

* `git status` : état des fichiers (suivis / non suivis / modifiés).
* `git log` : historique des commits.
* `git log --oneline --graph --decorate` : vue condensée avec branches et HEAD. ([DataCamp][4])
* `git diff` : différences non indexées.
* `git diff --staged` : différences prêtes à être commitées.

### Exemple de petit workflow

```bash
# Vous modifiez index.html
git status
git diff index.html            # Voir ce qui a changé

git add index.html
git status                     # index.html est en "staged"

git commit -m "Mise à jour de la section adoption"
git log --oneline --graph --decorate
```

---

# 3. Branching : branches Git et styles de branching

## 3.1. Qu’est-ce qu’une branche ?

Une **branche** est un pointeur léger vers un commit. `HEAD` pointe vers la branche courante, qui avance à chaque nouveau commit. ([Git][5])

Avantages :

* Tester des idées sans casser la version stable.
* Développer des fonctionnalités en parallèle.

## 3.2. Commandes de base

* Lister les branches :

```bash
git branch
```

* Créer une branche :

```bash
git branch feature/header-responsive
```

* Changer de branche :

```bash
git switch feature/header-responsive
# ou, plus ancien :
git checkout feature/header-responsive
```

* Créer et basculer en même temps :

```bash
git switch -c feature/header-responsive
```

`git branch` crée/liste les branches, `git switch` et `git checkout` changent de branche. ([Git][6])

## 3.3. Fusionner une branche (merge)

Vous travaillez sur `feature/header-responsive`, puis souhaitez intégrer dans `main` :

```bash
# Se placer sur la branche de destination
git switch main

# Fusionner la branche de fonctionnalité
git merge feature/header-responsive
```

En cas de conflits :

1. `git status` pour voir les fichiers en conflit.
2. Résoudre à la main dans les fichiers.
3. `git add` des fichiers résolus.
4. `git commit` pour finaliser le merge.

## 3.4. Styles de branching (models)

### 3.4.1. Feature Branching (recommandé pour vos projets)

* Branche principale : `main` (version stable).
* Pour chaque fonctionnalité ou lot de travail : créer `feature/...`.
* Une fois la fonctionnalité validée : merge dans `main`.

Par exemple :

```bash
git switch -c feature/api-chats
# dev, commits...
git switch main
git merge feature/api-chats
```

### 3.4.2. GitHub Flow (version formalisée)

* `main` correspond à la version déployable sur GitHub Pages.
* Pour chaque changement :

  * création de branche (`feature/contact-form`),
  * push de la branche sur GitHub,
  * Pull Request, revue, merge sur `main`,
  * déploiement automatique de GitHub Pages depuis `main`.

### 3.4.3. Git Flow (pour projets plus lourds)

* Branches : `main`, `develop`, `feature/*`, `release/*`, `hotfix/*`.
* Plus adapté aux applications avec gros cycles de release.
* Pour un site statique de cours, GitHub Flow / feature branching suffit largement.

## 3.5. Branching avancé : `rebase`, `cherry-pick`, `reset`, `reflog`

### 3.5.1. `git rebase`

Permet de “rejouer” les commits d’une branche au-dessus d’une autre, pour garder une histoire plus linéaire. À réserver aux utilisateurs à l’aise.

### 3.5.2. `git cherry-pick`

Appliquer un commit précis d’une autre branche à la branche courante :

```bash
git cherry-pick <sha-du-commit>
```

### 3.5.3. `git reset`

* `git reset --soft HEAD~1` : revenir en arrière d’un commit, garder les modifications dans la staging area.
* `git reset --mixed HEAD~1` : revenir en arrière, garder les modifications dans le working directory mais les sortir de la staging area.
* `git reset --hard HEAD~1` : tout effacer (commit + modifications), à manier avec une grande prudence.

### 3.5.4. `git reflog`

Historique des mouvements de `HEAD` :

```bash
git reflog
```

Permet de retrouver un commit “perdu” après un `reset` erroné, par exemple. ([Git][7])

---

# 4. Dépôt distant GitHub : création et synchronisation

## 4.1. Créer le dépôt GitHub

1. Se connecter à GitHub.
2. “New repository”.
3. Nom : `chat-solidaire` (par exemple).
4. Ne pas initialiser avec README ou autre (puisque vous avez déjà un dépôt local).

## 4.2. Ajouter le remote `origin`

Dans votre dépôt local :

```bash
git remote add origin https://github.com/VOTRE_COMPTE/chat-solidaire.git
# ou en SSH :
# git remote add origin git@github.com:VOTRE_COMPTE/chat-solidaire.git
```

`git remote add` ajoute un alias (`origin`) pointant vers l’URL du dépôt distant. ([Git][8])

Vérifier :

```bash
git remote -v
```

## 4.3. Premier push

Si votre branche principale s’appelle `main` :

```bash
git push -u origin main
```

`-u` enregistre `origin/main` comme branche de suivi pour `main`. Après cela, un simple `git push` suffira.

---

# 5. Versioning et tags pour les versions du site

## 5.1. Sémantique de version (SemVer)

* `MAJOR.MINOR.PATCH`
* Exemple : `1.0.0`, `1.0.1`, `1.1.0`.

## 5.2. Créer et pousser des tags

Créer un tag annoté :

```bash
git tag -a v1.0.0 -m "Première version publique du site"
```

Lister les tags :

```bash
git tag
```

Pousser tags et branche :

```bash
git push origin main
git push origin --tags
```

Les tags sont gérés par la commande `git tag`. ([Git][7])

---

# 6. Déployer le site sur GitHub Pages (depuis `main`)

Il s’agit du cœur de la partie “déploiement GitHub” pour un site statique.

## 6.1. Pré-requis

* Votre projet contient un fichier `index.html` à la racine (ou dans `/docs`). ([GitHub Docs][9])
* Votre dépôt est poussé sur GitHub (`main` à jour).
* Le dépôt est public (ou compte GitHub payant si dépôt privé). ([CollectionBuilder][10])

## 6.2. Configurer GitHub Pages (depuis une branche)

D’après la documentation GitHub Pages : ([GitHub Docs][11])

1. Sur GitHub, allez sur la page du dépôt.
2. Cliquer sur l’onglet **Settings**.
3. Dans le menu latéral, section **Code and automation**, cliquer sur **Pages**.
4. Dans “Build and deployment” > “Source”, choisir **Deploy from a branch**.
5. Dans “Branch”, sélectionner :

   * `main`
   * dossier `/root` (ou `/` selon l’interface).
6. Sauvegarder.

GitHub va alors construire et publier le site ; l’URL sera du type :

```text
https://VOTRE_COMPTE.github.io/chat-solidaire/
```

## 6.3. Workflow de mise à jour

Une fois GitHub Pages configuré, chaque :

```bash
git commit ...
git push origin main
```

déclenche une mise à jour automatique du site. ([GitHub Docs][12])

Résumé du cycle :

1. Modifier les fichiers (`index.html`, `assets/...`).
2. Tester en local dans le navigateur.
3. `git add`, `git commit`, `git push origin main`.
4. Attendre quelques secondes / dizaines de secondes.
5. Rafraîchir l’URL GitHub Pages.

---

# 7. TP Git + GitHub Pages (noté sur 20, optionnel pour vos étudiants)

Voici un squelette de TP que vous pouvez utiliser avec n’importe quel projet HTML/CSS/JS (par exemple votre site de chats), mais qui reste indépendant du contenu.

## 7.1. Objectifs

* Mettre un projet web existant sous Git.
* Créer au moins une branche de fonctionnalité.
* Utiliser un dépôt distant GitHub.
* Déployer sur GitHub Pages.

## 7.2. Consignes (exemple)

1. **Initialisation (4 pts)**

   * Initialiser un dépôt Git dans le dossier du projet.
   * Faire un premier commit propre avec un message clair.
   * Vérifier l’historique (`git log`).

2. **Branching fonctionnel (4 pts)**

   * Créer une branche `feature/nav` et y apporter une modification visible.
   * Fusionner cette branche dans `main` (merge propre, conflits résolus si besoin).
   * Supprimer la branche locale après fusion si souhaité.

3. **Dépôt distant GitHub (4 pts)**

   * Créer un dépôt GitHub `nom-projet`.
   * Ajouter le remote `origin`.
   * Pousser la branche `main` et vérifier la présence du code sur GitHub.

4. **Tags et versioning (4 pts)**

   * Créer un tag `v1.0.0` correspondant à la première version déployable.
   * Pousser le tag sur GitHub.

5. **Déploiement GitHub Pages (4 pts)**

   * Configurer GitHub Pages sur la branche `main`.
   * Vérifier que le site est accessible à l’URL fournie par GitHub.
   * Capturer l’URL et la fournir dans le rendu.
