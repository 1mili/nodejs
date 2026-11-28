# COMMANDES.md

| Commande | Rôle |
|---|---|
| `node --version` / `npm --version` / `git --version` | Vérifier les versions installées de Node.js, npm et Git |
| `git config --global user.name "Prénom Nom"` | Définir le nom affiché dans les commits |
| `git config --global user.email "email@exemple.com"` | Définir l'e-mail des commits (celui du compte GitHub) |
| `git config --global --list` | Afficher la configuration Git pour vérifier |
| `mkdir nodejs && cd nodejs` | Créer le dossier du projet et s'y placer |
| `npm init -y` | Générer un `package.json` par défaut |
| `npm install express` | Installer Express (crée `node_modules` et `package-lock.json`) |
| `npm start` | Lancer le serveur (`node server.js`) sur http://localhost:3000 |
| `git init` | Initialiser un dépôt Git local |
| `git status` | Voir les fichiers suivis / non suivis (vérifier que `node_modules` est ignoré) |
| `git add .` | Ajouter tous les fichiers à l'index |
| `git commit -m "init"` | Créer le premier commit |
| `git branch -M main` | Renommer la branche courante en `main` |
| `git remote add origin <url>` | Lier le dépôt local au dépôt GitHub distant |
| `git remote -v` | Vérifier l'URL du dépôt distant |
| `git push -u origin main` | Pousser `main` vers GitHub et mémoriser le suivi |
| `mkdir -p .github/workflows` | Créer le dossier des workflows GitHub Actions |
| `git add .github/workflows/cicd.yml` | Ajouter le fichier du workflow |
| `git commit -m "ci: add job-1"` | Commit du premier job |
| `git push` | Envoyer les commits sur GitHub (déclenche le pipeline) |
| `git commit -m "ci: add job-2, job-3 and job-4"` | Commit du pipeline complet |
| `git commit -m "test: break job-3"` | Commit qui casse volontairement job-3 (`lss`) |
| `git commit -m "fix"` | Commit qui corrige job-3 (`ls`) |
- docker pull : récupère l'image depuis Docker Hub
