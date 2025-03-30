# Rapport

> **Groupe :** 

  - ***Rida ADARDOUR*** 

  - ***Tarek OMARI***

  - ***Pierre Chrislin DORIVAL***

# TP Git & Docker – Rapport
 
### Enoncé :  


Le projet consistait à améliorer l'organisation et la gestion du dépôt existant docker_tp. Après l’avoir cloné et relié à un nouveau dépôt distant, j’ai :

- Configuré un fichier .gitignore adapté,

- Utilisé des branches Git pour le développement,

- Marqué des versions stables avec des tags,

- Employé des commandes avancées comme rebase et cherry-pick,

- Intégré des outils collaboratifs Git,

- Automatisé des processus Docker via GitHub Actions.


## Tâche 1 : Préparation de l'environnement et vérification du dépôt
 
- **1.1. Clonage du dépôt :**
 
Le dépôt GitHub fourni (`docker_tp`) a été cloné en local à l’aide de la commande suivante :
 
```bash
git clone https://github.com/RidaAdar/docker_tp.git
```

![Clonage du dépôt Git depuis GitHub]()

* **1.2 Configuration de Git :**
 
Avant toute manipulation, la configuration de l’environnement Git a été vérifiée et ajustée pour s'assurer que les informations de l'utilisateur sont bien définies.
 
```bash
git config --global user.name "VotreNom"
git config --global user.email "votremail@example.com"
```
Puis, la configuration a été vérifiée avec :

```bash
git config --list
```

📸 **Capture d'écran 2 (Affichage de la configuration Git)**  

![Affichage de la configuration Git](git-config-list.png)


* **1.3. Initialisation du nouveau dépôt distant**

Après avoir cloné le projet, un nouveau dépôt GitHub a été créé. Le lien distant a été mis à jour comme suit :

```bash
git remote remove origin
git remote add origin https://github.com/<username>/<new-repo>.git
```
📸 **Capture d'écran 3 (Changement de dépôt distant avec `git remote`)**  
👉 ![Changement de dépôt distant](git-remote.png)

## Tâche 2 : Configuration avancée du fichier `.gitignore`
 
* **2.1 Création et optimisation du fichier `.gitignore` :**
 
Un fichier `.gitignore` a été créé et configuré pour ignorer les fichiers et dossiers inutiles au suivi de version, en particulier ceux liés à Docker et à l’environnement local.
 
> Voici les principales entrées ajoutées :


📸 **Capture d'écran 4 (Édition du fichier .gitignore dans l'éditeur)**  
👉 ![Édition du fichier .gitignore](screen-gitignore.png)

* **2.2 Vérification des fichiers ignorés :**
 
La commande suivante a été utilisée pour vérifier que les fichiers définis dans `.gitignore` ne sont plus suivis par Git :
 
```bash
git status
```
📸 **Capture d'écran 5 (`git status` montrant que les fichiers sont ignorés)**  
👉 ![git status montrant que les fichiers sont ignorés](git_status.png)
 
💬 **Commentaires :**

- ✅ Les fichiers temporaires et d’environnement (`.log`, `.pyc`, `.venv/`, `build/`, etc.) sont bien ignorés grâce au `.gitignore`.
- 🖼️ Les fichiers `.png` sont des **captures d’écran prévues pour le rapport** : ils ne sont pas ignorés et seront commités volontairement.
- 📌 Le statut affiché est donc **normal et maîtrisé**.

 
# Tâche 3 : Mise en place d’un workflow de développement collaboratif
## 3.1 Mise en place d’un ruleset de protection sur la branche `master`

La protection de la branche `master` est essentielle pour garantir la stabilité du projet. Voici les étapes effectuées pour configurer un ruleset dans GitHub :

---

### ✅ Étape 1 : Création du ruleset

📸 **Capture d'écran 1 – Création du ruleset `rule1`**  
👉 ![Création du ruleset](cap1.png)

- Un ruleset nommé `rule1` a été créé via le bouton **"New ruleset"** dans l'onglet `Rulesets`.
- Ce ruleset regroupera l’ensemble des règles de protection applicables à une ou plusieurs branches.

---

### 🎯 Étape 2 : Ciblage de la branche `master`

📸 **Capture d'écran 2 – Ciblage de la branche `master` dans les paramètres du ruleset**  
👉 ![Ciblage de la branche master](cap2.png)

- Dans la section **Targets**, la branche `master` a été spécifiée comme cible.
- Cela signifie que toutes les règles définies s’appliqueront uniquement à cette branche.

---

### 🔐 Étape 3 : Activation des restrictions de merge

📸 **Capture d'écran 3 – Activation de la protection via Pull Request obligatoire**  
👉 ![Pull Request obligatoire](cap3.png)

- L’option **"Require a pull request before merging"** a été cochée.
- Cela **empêche tout push direct** sur `master` : les changements doivent passer par une **Pull Request**.
- De plus, **au moins 1 approbation est exigée** pour fusionner la PR.

---

💬 **Commentaires :**

- Cette configuration assure que **chaque contribution est relue et validée** avant d’être intégrée à la branche principale.
- Cela permet de maintenir un code propre, sécurisé, et validé collectivement.
- Utile dans tout workflow collaboratif en équipe.

  

## 3.2 Création et utilisation des branches thématiques

Pour organiser le développement collaboratif, plusieurs branches ont été créées, chacune correspondant à une fonctionnalité ou une correction spécifique :

- `feature/generate_dashboard`
- `feature/new_graph`
- `feature/new_model`
- `bugfix/division-error`

La commande utilisée pour créer une branche thématique est :

```bash
git checkout -b feature/new_model
```

📸 **Capture d'écran – Aller dans la branche feature/new_modeldéja créé"
👉  
![Switcher vers la branche](cap4.png)



📸 **Capture d'écran – Ouverture du fichier `model1.py` dans VS Code**  
👉  
![Ouverture du fichier model1.py](cap5_prime.png)

---

## ➕ Étape 4– Ajout des modifications dans l’index Git

### 💻 Commande utilisée :
```bash
git add app/src/model1.py
```
📸 **Capture d'écran – Ajout du fichier modifié au staging area**  
👉  
![Ajout au staging area](cap5.png)

---

## 📝 Étape 5 – Commit avec un message sémantique

### 💻 Commande utilisée :
```bash
git commit -m "feat: ajout d'un nouveau modele model1()"
```
📸 **Capture d'écran – Commit structuré avec `feat:`**  
👉  
![Commit structuré avec feat](cap5.png)

---

📸 **Capture d'écran – git pull — Synchroniser sa branche avec le dépôt distant**
👉  
![git pull](cap6.png)



## 🚀 Étape 6 – Envoi de la branche sur le dépôt distant

### 💻 Commande utilisée :
```bash
git push -u origin feature/new_model
```
📸 **Capture d'écran – Push de la branche vers GitHub**  
👉  
![Push branche vers GitHub](cap7.png)

---

## 🏷️ Convention de nommage des messages de commit

| Préfixe         | Description                                                             |
|------------------|-------------------------------------------------------------------------|
| `feat:`          | ➕ Ajout d'une **nouvelle fonctionnalité**                              |
| `fix:`           | 🐛 Correction d’un **bug**                                              |
| `BREAKING CHANGE:` | 💥 Changement **majeur** cassant la compatibilité                   |
| `perf:`          | 🚀 Amélioration des **performances** sans changement fonctionnel        |

```bash
git commit -m "fix: correction division par zéro dans la fonction main"
```
## 3.3 - Intégration via Pull Requests

## 📌 Étapes de revue et fusion d'une Pull Request sur GitHub

### 🟡 Étape 7 : Détection de changements sur la branche
📸 **Capture d'écran 1 (Compare & pull request)**  
👉 ![Compare & pull request](cap8.png)

> GitHub détecte que la branche `feature/new_model` a des changements récents. Un bouton "Compare & pull request" est proposé pour initier une PR vers `main`.

---

### 📝 Étape 8 : Création de la Pull Request
📸 **Capture d'écran 2 (Création de la PR et état initial)**  
👉 ![Création PR](cap9.png)
> L'auteur décrit les modifications apportées.  
> Des checks automatiques sont en cours (CI Docker) et une revue humaine est requise.  
> L’option "Merge pull request" est bloquée tant que ces conditions ne sont pas remplies.

---

### ✅ Étape 9 : Revue par un coéquipier
📸 **Capture d'écran 3 (Review de la Pull Request)**  
👉 ![Review PR](cap10.png)
> Le coéquipier Tarek valide la PR avec un message d'approbation. Il peut cliquer sur "Approve" et soumettre la revue.

---

### ✅ Étape 10: Vérification automatique des checks
📸 **Capture d'écran 4 (Checks et validation automatique)**  
👉 ![Checks ok](cap11.png)
👉 ![Checks ok](cap12.png)
> Tous les tests sont passés (Docker CI), et il n’y a pas de conflits avec la branche principale.  
> Le bouton "Merge pull request" devient actif.

---

### 🟢 Étape 11: Fusion et clôture
📸 **Capture d'écran 5 (Fusion réussie)**  
👉 ![PR fusionnée](cap13.png)
> La PR est fusionnée avec succès dans la branche `main`. GitHub propose de supprimer la branche `feature/new_model` devenue obsolète.

---

## Tâche 4 : Utilisation et gestion des tags Git
 
---
 
* **4.1 Création de tags pour marquer les versions**
 
✅ **Étape 1 – Création d’un tag Git annoté**  
Une fois que le modèle `model1()` a été intégré à la branche `master` (issue de la PR `feature/new_model`), un nouveau tag `v1.1.0` a été créé :

### 💻 Commande utilisée :
```bash
git tag -a v1.1.0 -m "Version 1.1.0 - Deuxième version stable"
```
📸 **Capture d'écran 1 – Création du tag `v1.1.0`**  
👉  
![Création du tag v1.1.0](cap14.png)

☁️ **Étape 2 – Push du tag sur GitHub**  
Pour publier ce tag sur le dépôt distant et générer une nouvelle release GitHub :

### 💻 Commande utilisée :
```bash
git push origin v1.1.0
```
📸 **Capture d'écran 2 – Push du tag sur GitHub**  
👉  
![Push du tag v1.1.0 sur GitHub](cap15.png)

🚀 **Étape 3 – Visualisation sur GitHub**  
Le tag `v1.1.0` est désormais visible sur GitHub, avec les fichiers sources en pièce jointe :

📸 **Capture d'écran 3 – Release GitHub visible avec le tag `v1.1.0`**  
👉  
![Release GitHub tag v1.1.0](cap21.png)





* **4.2 Vérification et listing des tags**
 
🛠️ **Étape 4 – Vérification des tags existants**  
Pour lister tous les tags disponibles dans le projet :

### 💻 Commande utilisée :
```bash
git tag -l
```

📸 **Capture d'écran 4 – Liste des tags Git**  
👉  
![Liste des tags Git](cap16.png)

---

🔍 **Tags observés** :

- `v0.1`, `v0.2`, `v0.3` – Développement initial  
- `v1.0.0` – Première release stable  
- `v1.1.0` – Nouvelle fonctionnalité : ajout du modèle `model1()`

---

🧠 **Remarque pédagogique : Pourquoi utiliser un tag ?**

- ✅ Pour **marquer un point stable** dans l’évolution du projet.
- 🚀 Pour **déclencher des workflows CI/CD** (ex. : publication Docker via GitHub Actions).
- 📦 Pour **générer automatiquement une release GitHub** avec les fichiers sources (ZIP, TAR, etc.).

📌 **Pourquoi version `1.1.0` ?**

> On suit le **Semantic Versioning (SemVer)** :
> - `1` → version majeure (changements cassants)
> - `1` → version mineure (**ajout de fonctionnalité** sans rupture)
> - `0` → patch (corrections de bugs ou petits ajustements)

Ici, `model1()` est une **nouvelle fonctionnalité non cassante**, donc on incrémente la version **mineure**.




* **4.3 Récupération et exécution d’une image Docker versionnée (via GHCR)**
 
🚀 **Exécution de l’image Docker versionnée via GHCR**

🔽 **Étape 1 – Pull de l’image `v1.1.0` depuis GHCR**

### 💻 Commande utilisée :
```bash
docker pull ghcr.io/ridaadar/newtp:v1.1.0
```

📸 **Capture d'écran 5 – Téléchargement de l’image `v1.1.0` depuis GHCR**  
👉  
![Pull image v1.1.0](cap17.png)



💬 **Commentaire** :  
L’image versionnée `v1.1.0` est récupérée depuis **GitHub Container Registry (GHCR)**.  
Elle contient l'application **Streamlit** avec les dernières fonctionnalités intégrées.

---

🖼️ **Étape 2 – Vérification des images disponibles**

### 💻 Commande utilisée :
```bash
docker images
```

📸 **Capture d'écran 6 – Liste des images Docker disponibles en local**  
👉  
![Liste des images Docker](cap18.png)


💬 **Commentaire** :  
Les deux versions `v1.0.0` et `v1.1.0` sont présentes localement.  
Chaque image a une taille d’environ **1.35GB**, prêtes à être exécutées.

---

🧠 **Étape 3 – Exécution de l’image via `docker run`**

### 💻 Commande utilisée :
```bash
docker run --name streamlit_app -p 8501:8501 ghcr.io/ridaadar/newtp:v1.1.0
```

📸 **Capture – Lancement du conteneur et logs de démarrage**  
👉  
![Logs de démarrage Streamlit](cap19.png)

💬 **Commentaire** :  
Le conteneur `streamlit_app` est lancé sur le port **8501**.  
Les logs confirment le **chargement du dataset** et le démarrage de l’**analyse exploratoire (EDA)**.

---

🌐 **Étape 4 – Accès à l’application dans le navigateur**

📸 **Capture – Interface web de l’application Streamlit (EDA)**  
👉  
![Interface Streamlit EDA](cap20.png)

💬 **Commentaire** :  
L’application est accessible via [http://127.0.0.1:8501](http://127.0.0.1:8501).  
Elle propose :

- 📊 Une vue générale du jeu de données,  
- 📈 Des statistiques descriptives,  
- 🤖 L'entraînement et les prédictions basées sur le modèle `model1()` intégré en `v1.1.0`.

---

✅ **Conclusion** :  
Cette version `v1.1.0` de l'image Docker comprend le **nouveau modèle `model1()`** ajouté précédemment.  
Elle a été **taguée** puis **poussée** sur **GitHub Container Registry (GHCR)**, puis **testée avec succès en local**.  
Le tout est **validé** par l’affichage de l’interface complète de l’application Streamlit.




 
## Tâche 5 : Expérimentation avec des commandes Git avancées
 
---
 
* **5.1 Rebase interactif**
 
Sur une branche de fonctionnalité, un rebase interactif a été utilisé pour **réorganiser les commits**, fusionner certains entre eux, et **renommer les messages** si nécessaire :
 
```bash
git rebase -i HEAD~3
```
 
📸 **Capture d'écran 14 (Rebase interactif sur la branche `feature/clean-history`)**  

👉 ![Rebase interactif sur la branche feature/clean-history](img/git-rebase-interactif.png)
 
> **Commentaires :**
 
  - Cela permet d’**améliorer la lisibilité de l’historique Git**.

  - Les commits sont mieux organisés, et les messages plus explicites.

  - Très utile **avant une Pull Request** pour ne pas polluer `main` avec des commits inutiles ou trop fragmentés.


* **5.2 Commande `cherry-pick`**
 
## 🧪 Étape 1 – Création de commits sur une branche spécifique

Deux commits ont été réalisés sur la branche `feature/new_model` :

### 💻 Commandes utilisées :
```bash
git commit -m "feat: Introduire le bug1"
git commit -m "feat: creer le modele my_model()"
```
📸 **Capture 1 – Commit 1 : Introduire le bug1**  
👉  
![Commit Introduire le bug1](first-commit-before-cherry.png)

📸 **Capture 2 – Commit 2 : Créer le modèle `my_model()`**  
👉  
![Commit my_model](second-commit-before-cherry.png)

---

🔍 **Étape 2 – Affichage de l’historique `git log` avant le `cherry-pick`**

### 💻 Commande utilisée :
```bash
git log --oneline
```

📸 **Capture 3 – Historique de la branche `feature/new_model` avant `cherry-pick`**  
👉  
![Historique git log](git-log-2commits_before_cheery.png)

---

🍒 **Étape 3 – Cherry-pick du commit ciblé**  
Pour rejouer **uniquement** le commit de création du modèle sur la branche `master`, on utilise :

### 💻 Commande utilisée :
```bash
git cherry-pick 996ae0b
```

📸 **Capture 4 – Cherry-pick depuis `master`**  
👉  
![Cherry-pick depuis master](cherry1.png)

✅ **Résultat** :  
Le commit est copié dans la branche `master` avec un **nouvel identifiant** (SHA différent), mais **le même contenu** que sur `feature/new_model`.

---

🧾 **Étape 4 – Vérification avec `git log`**

### 💻 Commande utilisée :
```bash
git log --oneline
```

📸 **Capture 5 – Log après cherry-pick sur `master`**  
👉  

![Log après cherry-pick sur master](git_log_after_cherry.png)

---

💬 **Commentaires** :  
`git cherry-pick` permet d’intégrer un **commit précis** d’une autre branche dans l’historique actuel **sans faire de merge**.

✅ Très utile pour :
- **Récupérer un correctif** ou une **fonctionnalité isolée**,
- **Éviter de polluer** `master` avec tout l’historique de la branche source,
- **Garder un historique propre et ciblé** lors du travail multi-branches.

🧠 Outil stratégique en environnement collaboratif pour un contrôle fin sur l'intégration du code.


---
 
* **5.3 Commande `git stash`**
 
Pendant le développement, certaines modifications non terminées ont été mises de côté temporairement avec :
 
```bash
git stash
```
Et plus tard réappliquées avec :
 
```bash
git stash pop
```
 
📸 **Capture d'écran 16 (stash et récupération de modifications)**  

👉 ![stash et récupération de modifications](img/git-stash.png)

 
* **5.4 Visualisation de l’historique des branches**
 
L’arborescence des commits et des branches a été visualisée avec :
 
```bash
git log --graph --oneline --all
```
 
📸 **Capture d'écran 17 (Historique visuel avec `git log --graph`)**  

👉 ![Historique visuel avec git log --graph](img/git-graph-cli.png)
 
 
De plus, l’extension Git Graph de VS Code a été utilisée pour un affichage graphique :
 
📸 **Capture d'écran 18 (Topologie des branches avec Git Graph VS Code)**  

👉 ![Topologie des branches avec Git Graph VS Code](img/git-graph-vscode.png)

 
 > **Commentaires :**

  - Ces outils permettent de mieux **comprendre la structure du projet**, surtout avec plusieurs branches actives.

  - Très utiles pour les **revues**, les **merges**, et les **validations**.

 
## Tâche 8 : Documentation et suivi du projet sur GitHub
 
---
 
* **8.1 Utilisation des Issues**
 
Des **issues** ont été créées sur GitHub afin de décomposer les tâches à effectuer et **assigner les responsabilités** à chaque membre de l’équipe.
 
📸 **Capture d'écran 19 (Liste des issues créées sur GitHub)**  

👉 ![Liste des issues créées sur GitHub](img/issues-list.png)
 
> **Commentaires :**
 
  - Chaque issue représente une tâche spécifique (ex : ajout d’un modèle, correction d’un bug, création du `.gitignore`, etc.).

  - Les issues permettent de **suivre l’état d’avancement** du projet en équipe.

  - Elles servent également à **documenter les bugs** rencontrés ou les améliorations à venir.
 
---
 
* **8.2 Organisation avec le Project Board**
 
Un **Project Board GitHub** (type Kanban) a été mis en place pour organiser le travail collaboratif.
 
📸 **Capture d'écran 20 (Project Board avec colonnes Todo, In Progress, Done)**  

👉 ![Project Board GitHub](img/project-board.png)
 
 > **Commentaires :**
 
  - Les issues sont intégrées au tableau via des cartes que l’on déplace au fur et à mesure de leur avancement.

  - Le tableau comporte trois colonnes principales :  

  $\Longrightarrow$ **Todo** : tâches à faire  

  $\Longrightarrow$ **In Progress** : tâches en cours  

  $\Longrightarrow$ **Done** : tâches terminées

- Cela permet une **vision claire de l’avancement global du projet**, même à distance.
 
---
 
> **Tâche 8 complétée :**
 Les outils de suivi GitHub (Issues + Project Board) ont été utilisés efficacement pour structurer le travail d’équipe.

 

 
 