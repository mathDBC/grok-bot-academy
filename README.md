# Grok Bot Academy : une petite boucle agentique pour apprendre

Grok Bot Academy est un prototype de tutorat par agents IA. Un **bot Profil** mesure ton niveau dans
chaque domaine, et des **bots profs** t'enseignent. Après chaque séance, chaque prof envoie
un compte rendu au bot Profil, qui met le profil à jour. Les profs relisent ce profil pour
adapter la séance suivante.

C'est un prototype, pas un produit fini. Essaie-le, casse-le, améliore-le.

## La boucle

```mermaid
flowchart LR
    U[Apprenant] -->|diagnostic de départ| P[Bot Profil]
    P -->|écrit| F[(profil.md / profil.json)]
    F -->|lecture seule| M[Mathbot]
    F -->|lecture seule| T[Tuxbot]
    F -->|lecture seule| S[Secbot]
    F -->|lecture seule| L[Langbot]
    U <-->|séances| M
    U <-->|séances| T
    U <-->|séances| S
    U <-->|séances| L
    M -->|compte rendu| P
    T -->|compte rendu| P
    S -->|compte rendu| P
    L -->|compte rendu| P
```

1. **Première interaction** : le bot Profil pose des questions, un domaine à la fois, et attribue un niveau de départ.
2. **Séance** : le prof lit le profil, propose un objectif, une explication courte, des exercices, une correction, un point à retenir.
3. **Vérification par un exercice** : chaque séance se termine par un exercice sans aide. Son résultat valide ou non l'apprentissage ; jamais de validation sur une simple explication.
4. **Compte rendu** : le prof envoie au bot Profil un résumé court (thèmes vus, exercice et résultat, décision validé / à revoir, erreurs récurrentes, difficultés, niveau estimé, prochaine étape).
5. **Mise à jour** : le bot Profil valide les changements de niveau et réécrit le profil. Lui seul écrit dans le profil.

## Contenu du dépôt

- `ARCHITECTURE.md` : rôles, règles et choix de conception.
- `prompts/` : les prompts des 5 bots (Profil, Mathbot, Tuxbot, Secbot, Langbot), génériques, plus celui du Builder Bot.
- `bots/` : un modèle partageable par bot (`PROMPT.md`, skills rôle et démarrage, `README.md` d'installation), dont le **Builder Bot** (optionnel) qui génère ton propre prof.
- `examples/guitarbot/` : un prof de guitare généré en simulation par le Builder Bot.
- `shared/` : format du profil partagé (`profil.example.json`, `profil.example.md`) et dossier `comptes-rendus/` avec un exemple de compte rendu.
- `CONTRIBUTING.md` : comment proposer une amélioration.

## Le monter chez toi

Le concept est indépendant de la plateforme : il suffit de pouvoir faire tourner plusieurs
agents LLM qui partagent un dossier et peuvent s'envoyer des messages.

1. Crée 5 agents nommés « Grok Bot Academy - Bot Profil », « - Mathbot », « - Tuxbot », « - Secbot » et « - Langbot », en suivant le `README.md` de chaque dossier de `bots/` (prompt + 2 skills).
2. Mets un dossier partagé lisible par tous (par exemple `academy/`), avec une copie de `shared/` (renomme `profil.example.*` en `profil.md` et `profil.json`).
3. Donne au bot Profil seul le droit d'écrire dans `profil.md` et `profil.json` ; les profs peuvent seulement créer des fichiers dans `comptes-rendus/`.
4. Permets aux profs d'envoyer un message au bot Profil (outil de messagerie entre agents, file de messages, webhook, ou simple fichier déposé dans `comptes-rendus/`).
5. Lance le diagnostic avec le bot Profil, puis une séance avec un prof.

Les prompts sont écrits pour des agents qui peuvent s'écrire entre eux. Si ta plateforme ne le
permet pas, remplace l'envoi du compte rendu par l'écriture d'un fichier dans `comptes-rendus/` (nom : `AAAA-MM-JJ-<bot>-<sujet>.md`) que le bot Profil relit. Mode dégradé : si un bot ou la messagerie manque, les autres continuent et le compte rendu est donné à l'apprenant.

## Créer ton propre professeur

Le **Builder Bot** (optionnel) t'interviewe (matière, public, niveau, langue, ton, exercices de validation), puis génère un prompt et deux skills de professeur compatibles avec le Bot Profil. Voir `bots/builder-bot/` et l'exemple `examples/guitarbot/`.

## Choix importants

- **Un seul écrivain** pour le profil, pour éviter les contradictions.
- **Validation par l'exercice** : un niveau ne monte que sur un exercice de vérification réussi.
- **Aucune invention** : un niveau ou un résultat n'existe que s'il vient d'une réponse ou d'un compte rendu réel.
- **Modèles gratuits d'abord** : le concept est pensé pour tourner sur des quotas gratuits.
- **Cybersécurité défensive** : le prof de cybersécurité n'enseigne la pratique offensive que sur des environnements légaux (labs, CTF, machines de test). Jamais de scan ou d'attaque de systèmes tiers.
- **Bac à sable** pour les exercices de commande (Linux), jamais sur la machine de l'apprenant.

## Idées d'amélioration

- Échelle de niveaux plus fine et sous-compétences par domaine.
- Révisions espacées : le bot Profil planifie les rappels.
- Nouveaux profs (code, finance, sciences) : la boucle est la même.
- Évaluation automatique de la qualité des corrections.
- Interface web légère par-dessus le profil partagé.

## Licence

MIT. Voir `LICENSE`.
