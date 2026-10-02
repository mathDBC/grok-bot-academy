# Architecture

## Rôles

| Bot | Rôle | Écrit dans le profil ? |
|---|---|---|
| Bot Profil | Diagnostic de départ, niveau par domaine, historique, validation des progrès | Oui (seul) |
| Mathbot | Mathématiques | Non, envoie un compte rendu |
| Tuxbot | Linux (pratique en bac à sable) | Non, envoie un compte rendu |
| Secbot | Cybersécurité (défensif et pédagogique) | Non, envoie un compte rendu |
| Langbot | Langues (repère CECRL A1 à C2) | Non, envoie un compte rendu |

## Données partagées

- `profil.json` : données structurées (niveau et preuves par domaine, historique).
- `profil.md` : résumé lisible, lu par les profs avant chaque séance.

Le format de départ est dans `shared/`. Il est volontairement simple : ajoute des champs
(sous-compétences, dates de révision, objectifs) selon tes besoins.

## Compte rendu type (prof vers Bot Profil)

```
Date :
Domaine / langue :
Thèmes vus :
Réussites :
Erreurs récurrentes :
Difficultés :
Exercice de vérification posé :
Résultat réel (réussi ou raté, avec l'erreur exacte) :
Décision (validé / à revoir) :
Niveau estimé :
Prochaine étape :
```

Transmission : le fichier `comptes-rendus/AAAA-MM-JJ-<bot>-<sujet>.md` est la référence ; la messagerie entre agents sert à prévenir le Bot Profil (voir `shared/comptes-rendus/exemple-compte-rendu.md`).

## Droits sur le dossier partagé

- Bot Profil : écrit `profil.md` et `profil.json`, lit `comptes-rendus/`.
- Profs : lisent `profil.md` et `profil.json`, créent de nouveaux fichiers dans `comptes-rendus/` (aucun autre droit d'écriture).

## Preuves et niveaux

Échelle 0 à 5 (langues : CECRL). Un niveau est « déclaré », « estimé » ou « validé ». Une preuve : `{"date", "source", "point", "resultat", "decision", "erreur"}`. Le niveau monte d'un cran après deux comptes rendus « validé » sur des séances différentes. Le Bot Profil note le fichier traité dans l'historique pour ne pas le traiter deux fois.

## Modèles de bots

Le dossier `bots/` contient un modèle partageable par bot : `PROMPT.md` (copie du fichier de `prompts/`), deux skills (rôle et démarrage) et un `README.md` d'installation. Noms d'import : « Grok Bot Academy - Bot Profil », « - Mathbot », « - Tuxbot », « - Secbot », « - Langbot ».

## Builder Bot (optionnel)

Un 6e bot, hors boucle d'apprentissage, aide à créer son propre prof : il interviewe l'utilisateur puis génère un prompt et deux skills au même format, compatibles avec le Bot Profil (voir `bots/builder-bot/` et `examples/guitarbot/`). Le Bot Profil ajoute le nouveau domaine à la première réception d'un compte rendu.

## Mode dégradé

Chaque bot fonctionne même si l'équipe est incomplète : sans Bot Profil, le prof estime le niveau par quelques questions (noté « déclaré ») ; sans messagerie ou dossier partagé, le compte rendu est donné à l'apprenant ; sans un autre prof, la matière correspondante est simplement indisponible.

## Règles transverses

- **Validation par l'exercice** : un prof valide ou non l'apprentissage toujours par un exercice de vérification, sans solution donnée. Pas d'exercice réussi, pas de validation. Le compte rendu indique l'exercice, le résultat et la décision (validé / à revoir), et le bot Profil ne fait monter un niveau que sur cette base.

- Ne jamais inventer un niveau, un résultat ou une preuve.
- Les profs ne donnent pas la solution d'un exercice en cours : ils guident.
- Les séances suivent la même trame : objectif, explication courte, exercices, correction, point à retenir.
- Aucune clé d'API, mot de passe ou secret ne transite dans les prompts ou les comptes rendus.
- Données personnelles : le profil reste local à l'apprenant. Ne publie jamais un vrai profil.
