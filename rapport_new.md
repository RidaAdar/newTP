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

![Clonage du dépôt Git depuis GitHub](Images/capture-config_log.png)

> Création d’un dépôt local et envoi vers le dépôt distant en les associant :


```bash
cd docker_tp
# Se déplacer dans le dossier du projet

git init
# Initialise un dépôt Git local (le dossier devient un projet versionné)

git add .
# Ajoute tous les fichiers du dossier au suivi Git

git commit -m "first commit"
# Crée un premier commit avec un message

git branch -M main
# (Facultatif) Renomme la branche actuelle en 'main' pour suivre la convention GitHub

git remote add origin https://github.com/TON-UTILISATEUR/ton-repo.git
# Associe le dépôt local à un dépôt distant sur GitHub

git push -u origin main
# Envoie la branche 'main' sur GitHub et établit la liaison de suivi entre local et distant
```


* **1.2 Configuration de Git :**
 
Avant toute manipulation, la configuration de l’environnement Git a été vérifiée et ajustée pour s'assurer que les informations de l'utilisateur sont bien définies.
 
```bash
git config --global user.name "forbiddeone"
git config --global user.email "votremail@example.com"
```
Puis, la configuration a été vérifiée avec :

```bash
git config --list
```
**Remarque :** Commande d'importation des photos dans le dossier Images

```bash
cp /mnt/c/Users/tarek/OneDrive/Images/Screenshots/Cpature_config.png /home/forbiddeone/newTP/Images
``` 
 ![Affichage de la configuration Git](Images/capture-config_log.png)

* **1.3. Initialisation du nouveau dépôt distant**

Après avoir cloné le projet, un nouveau dépôt GitHub a été créé. Le lien distant a été mis à jour comme suit :

```bash
git remote remove origin
git remote add origin https://github.com/RidaAdar/newTP.git
```

![Changement de dépôt distant](Images/capture_remote.png)

## Tâche 2 : Configuration avancée du fichier `.gitignore`
 
* **2.1 Création et optimisation du fichier `.gitignore` :**
 
Un fichier `.gitignore` a été créé et configuré pour ignorer les fichiers et dossiers inutiles au suivi de version, en particulier ceux liés à Docker et à l’environnement local.
 
> Voici les principales entrées ajoutées :

 ```gitignore

 # Python bytecode
 __pycache__/
 *.py[cod]
 *.pyo
 
 # Fichiers de logs
 *.log
 
 # Fichiers temporaires
 *.tmp
 *.swp
 
 # Dossiers de build
 build/
 dist/
 
 # Caches
 .cache/
 *.egg-info/
 .eggs/
 pip-wheel-metadata/
 
 # Environnements virtuels
 .env
 .venv/
 venv/
 env/
 
 # Fichiers secrets
 *.key
 *.pem
 
 # Docker
 .docker/
 docker-compose.override.yml
 Dockerfile~
 *.tar
 *.tar.gz
 
 # Streamlit
 .streamlit/config.toml
 
 # IDEs / éditeurs
 .vscode/
 .idea/
 
 # Système (Windows / Mac)
 .DS_Store
 Thumbs.db
 ```
> Mise à jour du fichier .gitignore
```bash
nano .gitignore
# ou
code .gitignore
```

* **2.2 Vérification des fichiers ignorés :**
 
La commande suivante a été utilisée pour vérifier que les fichiers définis dans `.gitignore` ne sont plus suivis par Git :
 
```bash
git status
```

![git status montrant que les fichiers sont ignorés](Images/capture_status.png)
 
 > **Commentaires :**
 
   - Les fichiers comme `.log`, `.pyc`, ou les dossiers comme `.venv/`, `build/`, `.vscode/` sont correctement exclus.

   - Cela permet de garder un historique propre et de ne pas polluer le dépôt avec des fichiers générés automatiquement.

 
## Tâche 3 : Mise en place d’un workflow de développement collaboratif
  
* **3.1 Création de branches thématiques :**
 
Pour organiser le développement collaboratif, plusieurs branches ont été créées, chacune associée à une fonctionnalité ou une correction spécifique :
 
- `feature/generate_dashboard`

- `feature/new_graph`

- `bugfix/division-error`
 
La commande utilisée pour créer une branche thématique est :
 
```bash
git checkout -b feature/generate_dashboard
```

![Création d'une branche locale avec git checkout -b](Images/capture_chekout-branch.png)

 
* **3.2 Développement et commits :**
 
Sur chaque branche, les modifications sont suivies de commits explicites, en utilisant une sémantique standard :
 
```bash
git commit -m "feat: ajout du dashboard interactif"
```
 
**Convention de nommage des messages de commit**
 
- `feat:` → ajout d'une nouvelle fonctionnalité

- `fix:` → correction d’un bug

- `BREAKING CHANGE:` → changement majeur pouvant casser la compatibilité

- `perf:` → amélioration des performances sans changement fonctionnel

📸 **Capture d'écran 7 (Commit structuré sur la branche `feature/new_graph`)**  
👉 ![Commit structuré sur la branche feature/new_graph](Images/capture_commit.png)

* **3.3 Pull Requests et Revue de code**
 
Une fois le développement terminé, une Pull Request (PR) est créée depuis GitHub pour proposer l’intégration des changements dans la branche `main`.
 
📸 **Capture d'écran 8 (Création d’une Pull Request sur GitHub)**  

👉 ![Création d’une Pull Request sur GitHub](Images/capture_pullrequest.png)
 
Les coéquipiers sont invités à commenter, relire, et approuver les modifications. En cas de conflit, GitHub alerte, et une résolution manuelle peut être nécessaire avant merge.
 
> **Commentaires :**
 
  - Le système de PR permet un contrôle qualité collaboratif avant d’intégrer une fonctionnalité.

  - Chaque branche reste isolée, ce qui évite les effets de bord sur `main`.
   
![Discussion et validation d’une Pull Request](Images/capture_approve_pull.png)

## Tâche 4 : Utilisation et gestion des tags Git
 
---
 
* **4.1 Création de tags pour marquer les versions**
 
Une fois une version stable atteinte (après l’intégration d’une fonctionnalité complète ou d’une correction importante), un **tag annoté** est créé pour figer cette version dans l’historique Git :
 
```bash
git tag -a v1.0.0 -m "Version 1.0.0 - Première release stable avec Dockerfile fonctionnel"
```
![Création d’un tag Git annoté](Images/capture_tag.png)
 
Puis, le tag est poussé sur le dépôt distant :
 
```bash
git push origin --tags
```
![Push du tag vers GitHub](Images/capture_pushtag.png)


* **4.2 Vérification et listing des tags**
 
Tous les tags créés peuvent être listés avec la commande :
 
```bash
git tag -l
```

> **Commentaires :**
 
  - L'utilisation de tags permet de **marquer des versions stables** du projet.

  - Cela facilite la navigation dans l’historique et permet de **lier une version à un livrable précis** (comme une image Docker).

  - Associé à GitHub Actions, un tag peut déclencher automatiquement un build.

 -----
 forbiddeone@Ltranger:~/newTP$ git reset --hard HEAD~1 
HEAD is now at 90723ea  feat: Ajout new_model3

* **4.3 Récupération et exécution d’une image Docker versionnée (via GHCR)**
 
Une fois l’image poussée sur **GitHub Container Registry (GHCR)**, on peut la récupérer avec :
 
```bash
 docker pull ghcr.io/ridaadar/newtp:sha-7b6a4ad
```
![Pull et exécution de l’image Docker GHCR](Images/capture_buildim.png)

Et l’exécuter en local :
 
```bash
docker run -p 8502:8501 ghcr.io/ridaadar/newtp:sha-7b6a4ad
```
![Pull et exécution de l’image Docker GHCR](Images/capture_pull_image.png)

  **Remarque :**
 
- GHCR facilite le **partage des images Docker versionnées**.

- Couplé à **GitHub Actions**, ce mécanisme permet de **publier automatiquement une image Docker à chaque release** via un tag Git.

 
>  **Tâche 4 complétée** : les tags Git sont créés, poussés et utilisés pour piloter la génération d’images Docker versionnées.

> Option 1: You want to keep those changes permanently
```bash
git add .
git commit -m "save changes before rebase"
git rebase -i HEAD~3
```
> You want to temporarily hide your changes (and bring them back later)
```bash 
git stash
git rebase -i HEAD~3
git stash pop  # bring your changes back after rebase
```
## Tâche 5 : Expérimentation avec des commandes Git avancées
 
---
 
* **5.1 Rebase interactif**
 
Sur une branche de fonctionnalité, un rebase interactif a été utilisé pour **réorganiser les commits**, fusionner certains entre eux, et **renommer les messages** si nécessaire :
 
```bash
git rebase -i HEAD~3
```
![Rebase interactif sur la branche feature/clean-history](Images/capture_chery_pick.png)
 
> **Commentaires :**
 
  - Cela permet d’**améliorer la lisibilité de l’historique Git**.

  - Les commits sont mieux organisés, et les messages plus explicites.

  - Très utile **avant une Pull Request** pour ne pas polluer `main` avec des commits inutiles ou trop fragmentés.


* **5.2 Commande `cherry-pick`**
 
Un commit utile d’une autre branche a été récupéré dans la branche courante grâce à :
 
```bash
git cherry-pick 5ef497c
```

![Cherry-pick d’un correctif depuis une autre branche](Images/capture_log-list.png)
 
> **Cas d’usage :**
 
  - Un bug a été corrigé dans la branche `bugfix/typo`, mais cette correction est aussi nécessaire sur `feature/dashboard`.

  - Plutôt que de refaire le commit, on le **"rejoue"** grâce à `cherry-pick`.

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
 ![stash et récupération de modifications](Images/capture_stash.png)

 
* **5.4 Visualisation de l’historique des branches**
 
L’arborescence des commits et des branches a été visualisée avec :
 
```bash
git log --graph --oneline --all
```
 

![Historique visuel avec git log --graph](Images/capture_log-list.png)
 
 
De plus, l’extension Git Graph de VS Code a été utilisée pour un affichage graphique :
 
![Topologie des branches avec Git Graph VS Code](img/git-graph-vscode.png)

 
 > **Commentaires :**

  - Ces outils permettent de mieux **comprendre la structure du projet**, surtout avec plusieurs branches actives.

  - Très utiles pour les **revues**, les **merges**, et les **validations**.

 
## Tâche 8 : Documentation et suivi du projet sur GitHub
 
---
 
* **8.1 Utilisation des Issues**
 
Des **issues** ont été créées sur GitHub afin de décomposer les tâches à effectuer et **assigner les responsabilités** à chaque membre de l’équipe.
 )
 
> **Commentaires :**
 
  - Chaque issue représente une tâche spécifique (ex : ajout d’un modèle, correction d’un bug, création du `.gitignore`, etc.).

  - Les issues permettent de **suivre l’état d’avancement** du projet en équipe.

  - Elles servent également à **documenter les bugs** rencontrés ou les améliorations à venir.
 
---
 
* **8.2 Organisation avec le Project Board**
 
Un **Project Board GitHub** (type Kanban) a été mis en place pour organiser le travail collaboratif.
 
 
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

 ## 5. Questions théoriques supplémentaires

---

### 🔹 Rebase vs Merge

- `git rebase` permet un historique **plus propre et linéaire**.
- `git merge` garde l’historique réel et est **plus sûr en collaboration**.
- **Quand utiliser `rebase` :**
  - Pour organiser ses commits en local, avant de pousser.
- **Quand utiliser `merge` :**
  - Pour intégrer des branches sur un dépôt partagé.
- **Risques avec `rebase` :**
  - Perte de commits si utilisé après un push.
- **Conseils :**
  - Ne jamais rebaser une branche déjà partagée.
  - Toujours tester ou stasher les changements avant un rebase.

---

### 🔹 Intérêt des tags & Semantic Versioning

- Les **tags** servent à marquer des **versions importantes et stables**.
- Ils facilitent :
  - Les déploiements
  - Le suivi de version
  - Les retours à un état stable

#### Semantic Versioning : `MAJOR.MINOR.PATCH`
- `MAJOR` → changements incompatibles
- `MINOR` → nouvelles fonctionnalités compatibles
- `PATCH` → corrections de bugs mineures

*Exemple :* `v2.1.3`

---

### 🔹 Mauvaise configuration du fichier `.gitignore`

- Peut entraîner :
  - L’ajout de fichiers inutiles (logs, binaires, caches…)
  - L’exposition de données sensibles (`.env`, clés…)
  - Un dépôt plus lourd et désorganisé

#### Pour corriger :

1. Modifier `.gitignore` pour y ajouter les fichiers à exclure
2. Supprimer les fichiers déjà suivis :

```bash
git rm --cached nom_du_fichier
git commit -m "Nettoyage fichiers ignorés"


 
 