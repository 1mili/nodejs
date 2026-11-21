# TP CI/CD avec GitHub Actions

Application Node.js (Express) + pipeline GitHub Actions de 4 jobs :
`job-1` → (`job-2` et `job-3` en parallèle) → `job-4`.

## Questions de synthèse

**1. Définissez workflow, job, step et runner.**
- **Workflow** : fichier YAML dans `.github/workflows/` qui décrit un pipeline automatisé (événements déclencheurs + jobs).
- **Job** : ensemble de steps exécutées sur une même machine. Par défaut, les jobs s'exécutent en parallèle.
- **Step** : une étape d'un job, soit une action existante (`uses`), soit une commande shell (`run`).
- **Runner** : machine virtuelle neuve fournie par GitHub (ici `ubuntu-latest`) qui exécute un job.

**2. Différence entre `uses` et `run` ?**
`uses` appelle une action réutilisable (ex. `actions/checkout@v4`), alors que `run` exécute directement une ou plusieurs commandes shell (ex. `ls`, `echo`).

**3. À quoi sert `needs` ? Que font les jobs qui n'en déclarent pas ?**
`needs` déclare qu'un job attend la réussite d'un ou plusieurs autres jobs avant de démarrer ; on construit ainsi un graphe de dépendances. Les jobs sans `needs` démarrent tous en parallèle, dès le début du workflow.

**4. Pourquoi déclencher le pipeline sur `pull_request` en plus de `push` ?**
Pour valider le code *avant* la fusion dans `main` : le statut du pipeline s'affiche dans la Pull Request, ce qui permet de détecter les erreurs en amont et de protéger la branche principale.

## Réponses aux autres questions du TP

- **CI / livraison continue / déploiement continu** : la CI intègre et teste automatiquement chaque changement ; la livraison continue produit en plus un livrable prêt à être déployé (déploiement validé manuellement) ; le déploiement continu déploie automatiquement en production dès que les tests passent.
- **`node_modules` vs `package-lock.json`** : `node_modules` est volumineux et régénérable via `npm install` ; `package-lock.json` fige les versions exactes pour des installations reproductibles.
- **Sans `actions/checkout`** : `ls` ne verrait pas les fichiers du projet, car le runner est une machine vide qui ne contient pas le code.
- **Checkout dans chaque job** : chaque job tourne sur un runner neuf et isolé, donc le code n'est pas partagé entre jobs.
- **Exécution #3** : `job-2` ne dépend que de `job-1` (réussi), donc il s'exécute ; `job-4` dépend de `job-3` (en échec), donc il est ignoré (skipped).
# nodejs
