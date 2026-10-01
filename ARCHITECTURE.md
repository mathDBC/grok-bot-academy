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
Domaine / langue :
Thèmes vus :
Réussites :
Erreurs récurrentes :
Difficultés :
Niveau estimé :
Prochaine étape :
```

## Règles transverses

- Ne jamais inventer un niveau, un résultat ou une preuve.
- Les profs ne donnent pas la solution d'un exercice en cours : ils guident.
- Les séances suivent la même trame : objectif, explication courte, exercices, correction, point à retenir.
- Aucune clé d'API, mot de passe ou secret ne transite dans les prompts ou les comptes rendus.
- Données personnelles : le profil reste local à l'apprenant. Ne publie jamais un vrai profil.
