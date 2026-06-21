# /commit

> Commande pour sauvegarder l'état du workspace dans un commit Git.

---

## Mission

Quand je lance `/commit`, exécute la séquence suivante :

### Étape 1 : Vérifier l'état du dépôt

- Lance `git status` pour voir les fichiers modifiés, ajoutés ou supprimés
- Lance `git diff --stat` pour avoir un aperçu des changements

### Étape 2 : Initialiser le dépôt si nécessaire

Si Git n'est pas encore initialisé dans le workspace (`git status` retourne une erreur) :
1. Lance `git init`
2. Vérifie que `.gitignore` est présent à la racine
3. Informe-moi que le dépôt vient d'être initialisé

### Étape 3 : Proposer un message de commit

Analyse les changements détectés et propose un message de commit clair et en français, au format :

```
type: description courte

- détail 1
- détail 2
```

Types disponibles : `ajout`, `modif`, `fix`, `docs`, `config`, `suppression`

Exemple : `ajout: structure livrables et gestion des secrets`

Demande-moi de valider ou de modifier le message avant de continuer.

### Étape 4 : Effectuer le commit

Une fois le message validé :
1. `git add .` — stage tous les fichiers (le .gitignore exclut déjà les secrets)
2. `git commit -m "[message validé]"`
3. Affiche la confirmation avec le hash du commit

### Étape 5 : Proposer un push (si remote configuré)

- Si un remote `origin` est configuré, propose de pousser avec `git push`
- Si aucun remote n'est configuré, signale-le et propose d'en ajouter un

---

## Règles importantes

- Ne jamais commiter `.env` ou tout fichier listé dans `.gitignore`
- Si `.gitignore` est absent, le signaler avant tout `git add`
- Toujours demander validation du message avant de commiter
- En cas d'erreur Git, expliquer le problème et proposer une solution
- Répondre en français
