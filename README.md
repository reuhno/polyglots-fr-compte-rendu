# CR des réunions WordPress FR : skill de compte-rendu

## À quoi ça sert

Ce dossier contient un prompt (un « skill ») qui transforme le copier-coller brut d'une réunion Slack de l'équipe de traduction (ou de documentation) de WordPress francophone en compte-rendu au format habituel de l'équipe, prêt à publier sur https://fr.wordpress.org/team/.

L'IA nettoie le copier-coller (messages hors ordre, aperçus de liens, emojis, plaisanteries), classe les échanges par sujet, résume les débats, liste les propositions concurrentes et note les décisions. Ce qu'elle ne sait pas (numéro de réunion, pseudo WordPress.org, date de la prochaine réunion…) est marqué `[À VÉRIFIER : …]`.

**Relecture humaine obligatoire.** Une IA peut se tromper : attribuer un avis à la mauvaise personne, rater une nuance, écrire une décision qui n'a pas été prise, mettre un pseudo qui renvoie vers le profil de quelqu'un d'autre. Une personne de l'équipe qui a assisté à la réunion doit relire le CR en entier et vérifier chaque pseudo sur profiles.wordpress.org. Elle doit aussi résoudre chaque `[À VÉRIFIER]`, et c'est elle seule qui publie. Chaque réponse de l'IA commence par cet avertissement et se termine par une liste de contrôle « Relecture avant publication ».

## Copier la réunion depuis Slack

1. Ouvrir le canal (#traductions ou #documentation) à l'heure de la réunion.
2. Sélectionner **de la première à la dernière ligne** de la réunion : de la première phrase du jour (« Hello, c'est sur Slack ? ») jusqu'au message de clôture, et plus loin si des réponses tardives se rapportent à la réunion.
3. Copier-coller dans la conversation avec l'IA.
4. Éviter, si possible, les fils de discussion (réponses en fil) : leurs messages arrivent hors ordre. Si la réunion en contient, les copier quand même : le skill les remet dans l'ordre.
5. Indiquer le numéro de la réunion et, si le texte ne la contient pas, la date.

## Quel modèle d'IA ?

Prendre un modèle de bon niveau : Claude Sonnet ou Opus, GPT-5, Mistral Large, Gemini Pro. Les petits modèles (Claude Haiku, versions « mini » ou « small ») suivent mal les règles : lors des tests, l'un d'eux a oublié un participant, a mal placé des sujets dans le gabarit et a prêté à des participants des propos qu'ils n'avaient pas tenus. Quel que soit le modèle, la relecture humaine reste obligatoire.

## Installation selon l'outil

Pour tous les outils, la méthode de base fonctionne : coller le contenu de `SKILL.md` en tête de la conversation, puis le copier-coller de la réunion.

| Outil | Méthode |
|---|---|
| Claude.ai | Créer un Projet et coller `SKILL.md` dans les instructions du projet, ou importer le dossier compressé en zip comme Skill (Réglages, fonctionnalités, Skills) (à vérifier). |
| Claude Code | Copier le dossier dans `~/.claude/skills/cr-reunion-wp-fr/` (le fichier `SKILL.md` à la racine du dossier). |
| Codex | Dossier du skill dans `$HOME/.agents/skills/` (utilisateur) ou `.agents/skills/` dans le dépôt, d'après la documentation d'OpenAI (voir ci-dessous). Invocation : `$cr-reunion-wp-fr`. |
| Mistral Le Chat | Créer un Agent, copier le contenu de `SKILL.md` dans les instructions (à vérifier). |
| ChatGPT | Créer un GPT personnalisé et coller le contenu de `SKILL.md` dans les instructions (à vérifier). |
| Gemini | Créer un Gem et coller le contenu de `SKILL.md` dans les instructions (à vérifier). |

**Source vérifiée pour Codex** : la page https://developers.openai.com/codex/skills renvoie vers https://learn.chatgpt.com/docs/build-skills (consultée le 7 octobre 2026). Elle indique : « `$CWD/.agents/skills` et `$REPO_ROOT/.agents/skills` » pour un dépôt, « `$HOME/.agents/skills` » pour l'utilisateur et « `/etc/codex/skills` » pour l'administrateur ; un skill est un dossier avec un `SKILL.md` portant `name` et `description` ; appel explicite par `$nom-du-skill`. Le chemin `~/.codex/skills/` n'y figure pas.

Les chemins des autres outils (Claude.ai, Mistral, ChatGPT, Gemini) n'ont pas été vérifiés dans cette version : la méthode « coller `SKILL.md` en tête de conversation » reste la valeur sûre.

Les fichiers joints (`modeles/`, `participants.md`, `exemples/`) ne sont lus que si l'outil le permet ; sinon l'essentiel est dans `SKILL.md`. Dans un GPT, un Gem ou un Agent, joindre `participants.md` si l'outil accepte des fichiers de connaissance.

## Contenu du dossier

- `SKILL.md` : le prompt complet (rôle, nettoyage, règles de rédaction, gabarits traduction et documentation, option anonymisation, option « version blocs »).
- `modeles/traduction.md` et `modeles/documentation.md` : squelettes vides à remplir.
- `modeles/composition-officielle.html` : la composition « CR réunion traduction » de fr.wordpress.org/team (trame de la version blocs, § 13 de `SKILL.md`), telle que l'éditeur actuel la sérialise.
- `modeles/composition-officielle.json` : la même composition, exportée par l'équipe le 2026-10-07 (format d'export des compositions WordPress, importable dans un autre site par « Modèles », « Importer depuis JSON »).
- `participants.md` : table d'exemple, entièrement fictive, au format attendu : pseudos WordPress.org (et Slack quand ils sont connus). La vraie table de l'équipe va dans `participants.local.md` (même format), ignoré par git ; le skill la lit en priorité si elle est fournie. Les lignes avec « ? » sont à compléter par l'équipe. Elle sert à écrire les pseudos justes dans la liste des participants.
- `exemples/` : un cas pour tester. La conversation est réelle mais anonymisée : les noms, pseudos et liens Slack sont fictifs.

## Tester avec les exemples

Les noms, pseudos et liens Slack de l'exemple sont fictifs ; la conversation, elle, est réelle mais anonymisée.

1. Dans un outil installé comme ci-dessus, coller `exemples/2026-10-05-entree.txt` et préciser : « 101e réunion, lundi 5 octobre 2026, canal #traductions ».
2. Comparer la réponse à `exemples/2026-10-05-cr-attendu.md`. Vérifier surtout :
   - le CR ne contient pas le point « Choix de la personne responsable du compte-rendu » (il n'a pas eu lieu) ;
   - les pseudos sont ceux de WordPress.org ou `@[À VÉRIFIER]`, pas ceux de Slack ;
   - le sondage n'est pas présenté comme une décision, et ne donne pas de chiffres ;
   - les messages postés après la clôture ne sont pas intégrés comme des échanges ;
   - la prochaine réunion est marquée `[À VÉRIFIER]` ;
   - chaque sujet débattu se termine par une ligne 📌.
3. L'écart de formulation est normal ; ce sont les omissions et inventions qui comptent.

## Coller le CR dans WordPress

À confirmer sur fr.wordpress.org avec l'équipe avant la première publication :

- **Version Markdown** (par défaut) : dans l'éditeur visuel de WordPress, coller le texte ; l'éditeur de blocs convertit le Markdown en blocs (titres, listes, paragraphes). Le titre du post se saisit dans le champ « titre ». Vérifier les niveaux de titre, la ligne 📌 et le séparateur.
- **Version blocs** : demander « version blocs » à l'IA, puis, dans l'éditeur, ouvrir l'éditeur de code (menu « Options », « Éditeur de code »), coller le HTML, revenir à l'éditeur visuel. Ce HTML suit la composition « CR réunion traduction » de l'équipe, déjà remplie : inutile d'insérer la composition avant. Testé le 2026-10-07 dans WordPress Playground (WordPress 7.1) : aucun bloc signalé comme invalide, colonnes et lignes 📌 comprises.
- Dans les deux cas : catégorie et étiquettes de l'équipe (`compte-rendu`, `traduction`, `traductions` pour la traduction ; `compte-rendu`, `documentation` pour la documentation), puis relecture de tous les `[À VÉRIFIER]` avant de publier.
