# Builder Bot

Bot optionnel (le 6e) de [Grok Bot Academy](https://github.com/mathDBC/grok-bot-academy) : il interviewe l'utilisateur puis génère un nouveau professeur (prompt + skills de rôle et de démarrage) compatible avec le Bot Profil.

## Nom d'import
« Grok Bot Academy - Builder Bot »

## Contenu de ce dossier
- `PROMPT.md` : les instructions du bot, avec le modèle de professeur (identique à `../../prompts/05-builder-bot.md`).
- `skills/builder-bot-role/SKILL.md` : le rôle et la méthode.
- `skills/builder-bot-demarrage/SKILL.md` : le premier accueil.

## Installation
1. Crée un agent « Grok Bot Academy - Builder Bot » et colle `PROMPT.md` comme instructions.
2. Ajoute les deux skills (`skills/*/SKILL.md`).
3. Optionnel : donne-lui l'écriture dans un dossier `profs-personnalises/` pour qu'il y crée les fichiers. Il n'a besoin d'aucun accès au profil des apprenants.
4. Écris-lui « Bonjour » : il t'explique l'Academy et lance l'interview.
5. Relis le professeur généré, teste-le, puis importe-le comme les autres (même dossier partagé, écriture uniquement dans `comptes-rendus/`). Le Bot Profil ajoute le nouveau domaine à la première réception d'un compte rendu.

## Mode dégradé
Sans accès aux fichiers, le bot livre les trois fichiers en blocs de code. Sans Bot Profil, le professeur généré fonctionne grâce à son propre mode dégradé.

## Exemple
Voir [`../../examples/guitarbot/`](../../examples/guitarbot/) : un professeur de guitare généré en simulation.

## Rappels
Aucune clé d'API ni secret dans les fichiers générés. Le Builder Bot ne publie ni n'envoie rien : c'est à toi de relire et de partager.
