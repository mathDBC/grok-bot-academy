# Modèles de bots

Chaque dossier est un modèle de bot partageable : `PROMPT.md`, deux skills (rôle et démarrage) et un `README.md` d'installation.

| Bot | Nom d'import | Dossier |
|---|---|---|
| Bot Profil | « Grok Bot Academy - Bot Profil » | [`bot-profil/`](bot-profil/) |
| Mathbot | « Grok Bot Academy - Mathbot » | [`mathbot/`](mathbot/) |
| Tuxbot | « Grok Bot Academy - Tuxbot » | [`tuxbot/`](tuxbot/) |
| Secbot | « Grok Bot Academy - Secbot » | [`secbot/`](secbot/) |
| Langbot | « Grok Bot Academy - Langbot » | [`langbot/`](langbot/) |
| Builder Bot (optionnel) | « Grok Bot Academy - Builder Bot » | [`builder-bot/`](builder-bot/) |

## Installation de l'équipe
1. Importe d'abord le Bot Profil, puis les profs que tu veux (ils fonctionnent aussi seuls, en mode dégradé).
2. Crée le dossier partagé `academy/` à partir de `../shared/`.
3. Droits : le Bot Profil seul écrit `profil.md` et `profil.json` ; les profs lisent ces fichiers et n'écrivent que dans `comptes-rendus/` (nouveaux fichiers).
4. Relie les bots (canal de groupe, messagerie entre agents, ou simplement le dossier `comptes-rendus/`).
5. Lance le diagnostic avec le Bot Profil.

## Créer ton propre professeur
Le **Builder Bot** (optionnel) interviewe l'utilisateur puis génère un nouveau prof (prompt + skills) compatible avec le Bot Profil. Voir `builder-bot/` et l'exemple `../examples/guitarbot/`.

`PROMPT.md` est une copie de `../prompts/` ; en cas de modification, mets les deux (et le skill de rôle) à jour.
