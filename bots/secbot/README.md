# Secbot

Modèle de bot public de [Grok Bot Academy](https://github.com/mathDBC/grok-bot-academy).

## Nom d'import
« Grok Bot Academy - Secbot »

## Contenu de ce dossier
- `PROMPT.md` : les instructions du bot (identique à `../../prompts/03-secbot.md`).
- `skills/secbot-role/SKILL.md` : le rôle et la méthode du bot.
- `skills/secbot-demarrage/SKILL.md` : la première conversation avec un nouvel apprenant.

## Installation
1. Crée un agent et nomme-le « Grok Bot Academy - Secbot ».
2. Colle le contenu de `PROMPT.md` comme instructions de l'agent.
3. Ajoute les deux skills (`skills/*/SKILL.md`) à l'agent, via la fonction d'import de skills de ta plateforme. Sinon, colle leur contenu à la suite des instructions.
4. Crée un dossier partagé `academy/` accessible aux 5 bots, avec une copie de `../../shared/` (`profil.md`, `profil.json`, `comptes-rendus/`).
   - Droits : lecture de `profil.md` et `profil.json`, écriture uniquement dans `comptes-rendus/` (création de nouveaux fichiers).
   - Cadre éthique : enseignement défensif ; pratique offensive uniquement sur labs, CTF et machines de test légales. Ne retire pas cette section du prompt.
5. Messagerie : place les 5 bots dans un même canal de groupe, ou active la messagerie entre agents, pour que les profs envoient leurs comptes rendus au Bot Profil.
6. Teste : écris « Bonjour » au bot ; il doit se présenter, expliquer la boucle et poser ses questions de départ une par une.

## Mode dégradé
- Bot Profil absent ou dossier partagé introuvable : le bot demande le niveau à l'apprenant et le note comme « déclaré ».
- Messagerie indisponible : le compte rendu est donné à l'apprenant (ou déposé dans `comptes-rendus/`) pour être transmis au Bot Profil.
- Un autre bot absent : les autres continuent, seule la matière concernée est indisponible.

## Rappels
Aucune clé d'API, mot de passe ou secret dans les prompts, skills ou comptes rendus. Ne publie jamais un vrai profil d'apprenant.
