# 📝 Le compte-rendu de réunion en 30 secondes

**Personne ne veut faire le CR ? Plus besoin de volontaire.**
Copiez la réunion Slack, collez-la dans votre IA, relisez, publiez.

Ce dépôt contient un **skill** : une fiche d'instructions qui apprend à une IA (Claude, ChatGPT, Mistral Le Chat, Gemini, Codex…) à rédiger les comptes rendus des réunions de l'équipe de traduction francophone de WordPress, **au format habituel de l'équipe**, prêts à publier sur [fr.wordpress.org/team](https://fr.wordpress.org/team/).

> Projet communautaire, non officiel : il n'est ni produit ni approuvé par la WordPress Foundation, ni par l'équipe Polyglots.

---

## ✨ Ce que ça fait

Vous collez ceci (le désordre habituel de Slack) :

```text
Claire Fontaine  [12 h 28]
alors on m'a soumis une demande pendant cette journée concernant "loader"
[12 h 29]https://translate.wordpress.org/projects/wp-plugins/pagefluent/ pour du contexte
Sophie Garnier  [12 h 30]
Chargement ?
Lucas Bernard  [12 h 39]
"Indicateur de chargement" ?
Thomas Girard  [12 h 40]
J'aime bien le mot indicateur
…
```

Vous obtenez cela :

```markdown
### Comment traduire « loader » ?

Propositions :
- « Chargement », proposé par Sophie.
- « Indicateur de chargement », proposé par Lucas, préféré par Thomas, Claire et Hugo.
- …

📌 Pas de décision : sujet reporté à la prochaine réunion.
```

En détail, l'IA :

- 🧹 **nettoie** le copier-coller : messages hors ordre, aperçus de liens, emojis, plaisanteries, messages postés après la fin ;
- 🗂️ **range** les échanges dans le gabarit de l'équipe : ordre du jour, participants, statistiques, questions abordées ;
- ⚖️ **résume** les débats : qui propose quoi, avec quels arguments ;
- 📌 **note** les décisions… et seulement les vraies : elle n'invente jamais de décision ;
- 🏷️ **marque** ce qu'elle ne sait pas avec `[À VÉRIFIER : …]` (numéro de réunion, pseudo, date) au lieu de deviner.

---

## ⚠️ Avant tout : une relecture humaine, toujours

L'IA prépare un **brouillon**. Elle peut se tromper : prêter un avis à la mauvaise personne, rater une nuance, écrire un pseudo qui renvoie vers le profil de quelqu'un d'autre.

Une personne **présente à la réunion** relit donc le CR en entier avant de le publier. Ça prend cinq minutes, pas une heure. Chaque réponse de l'IA commence par ce rappel et se termine par une liste de contrôle, à suivre point par point :

- [ ] chaque pseudo ouvert sur `https://profiles.wordpress.org/<pseudo>/` ;
- [ ] personne d'oublié dans les participants ;
- [ ] chaque avis attribué à la bonne personne ;
- [ ] aucune décision 📌 inventée ;
- [ ] chiffres, dates et liens justes ;
- [ ] tous les `[À VÉRIFIER]` résolus.

---

## 🚀 Démarrer : choisissez votre chemin

### Chemin 1 : sans rien installer (recommandé pour essayer)

Ça marche avec **n'importe quelle IA** : Claude.ai, ChatGPT, Le Chat, Gemini…

**Étape 1.** Copiez les instructions dans votre presse-papiers.

Sur Mac ou Linux, dans le Terminal :

```bash
curl -s https://raw.githubusercontent.com/reuhno/polyglots-fr-compte-rendu/main/SKILL.md | pbcopy
```

Sur Windows, dans PowerShell :

```powershell
irm https://raw.githubusercontent.com/reuhno/polyglots-fr-compte-rendu/main/SKILL.md | Set-Clipboard
```

Sans terminal : ouvrez [SKILL.md en version brute](https://raw.githubusercontent.com/reuhno/polyglots-fr-compte-rendu/main/SKILL.md), puis tout sélectionner et copier.

**Étape 2.** Ouvrez une **nouvelle conversation** et collez les instructions.

**Étape 3.** Dans le même message, ou juste après, collez la réunion Slack et ajoutez par exemple :

> 101e réunion, lundi 5 octobre 2026, canal #traductions. Fais-moi le CR.

**Étape 4.** Relisez avec la liste de contrôle, puis publiez (voir [Publier sur fr.wordpress.org](#-publier-sur-frwordpressorg)).

### Chemin 2 : Claude Code

Installez le skill une fois pour toutes :

```bash
git clone https://github.com/reuhno/polyglots-fr-compte-rendu.git ~/.claude/skills/cr-reunion-wp-fr
```

Ensuite, dans Claude Code, tapez `/cr-reunion-wp-fr` et collez la réunion. Claude le propose aussi tout seul quand vous collez une réunion en demandant un CR.

### Chemin 3 : Codex

```bash
git clone https://github.com/reuhno/polyglots-fr-compte-rendu.git ~/.agents/skills/cr-reunion-wp-fr
```

Puis, dans Codex, appelez `$cr-reunion-wp-fr` et collez la réunion. Ce chemin est celui de la [documentation d'OpenAI sur les skills](https://learn.chatgpt.com/docs/build-skills), consultée le 7 octobre 2026.

### Chemin 4 : un assistant permanent dans votre IA habituelle

Pour ne pas recoller les instructions à chaque fois, créez un assistant dédié et collez le contenu de `SKILL.md` dans ses instructions :

| Outil | Où le créer |
|---|---|
| Claude.ai | un **Projet** (instructions du projet) |
| ChatGPT | un **GPT personnalisé** |
| Mistral Le Chat | un **Agent** |
| Gemini | un **Gem** |

Si l'outil accepte des fichiers joints, ajoutez aussi votre table des participants (voir plus bas). Ces menus changent souvent : si vous ne les trouvez pas, le chemin 1 marche toujours.

### Mettre à jour (chemins 2 et 3)

```bash
git -C ~/.claude/skills/cr-reunion-wp-fr pull
```

Pour Codex, remplacez `~/.claude/skills` par `~/.agents/skills`.

---

## 📋 Bien copier la réunion depuis Slack

1. Ouvrez le canal (#traductions ou #documentation) à l'heure de la réunion.
2. Sélectionnez **de la première à la dernière ligne**, du premier « Hello » au message de clôture.
3. Copiez, puis collez dans la conversation avec l'IA.

💡 **Astuce pour les réunions** : répondez dans le canal plutôt qu'en fil de discussion. Les réponses en fil arrivent dans le désordre au copier-coller. Le skill sait les remettre en ordre, mais c'est plus fiable sans.

---

## 👥 Les bons pseudos WordPress.org

Slack ne donne que les noms d'affichage, pas les pseudos WordPress.org. Le skill les prend dans une **table des participants** :

- `participants.md` est un **exemple fictif**, qui montre le format ;
- la vraie table de l'équipe se garde dans `participants.local.md`, que git ignore et que le skill lit en priorité.

Pour la créer, avec le chemin 2 :

```bash
cp ~/.claude/skills/cr-reunion-wp-fr/participants.md ~/.claude/skills/cr-reunion-wp-fr/participants.local.md
```

Remplacez ensuite les lignes d'exemple par les vrais noms et pseudos. Avec les chemins 1 et 4, collez la table (ou joignez le fichier) avec la réunion.

Sans table, rien de grave : l'IA écrit `@[À VÉRIFIER]` et vous complétez à la relecture.

---

## 🧠 Quelle IA choisir ?

Un modèle **de bon niveau** : Claude Sonnet ou Opus, GPT-5, Mistral Large, Gemini Pro.

Les petits modèles (Claude Haiku, versions « mini » ou « small ») suivent mal les règles. Lors des tests, l'un d'eux a oublié un participant, a mal rangé des sujets et a prêté à quelqu'un des propos qu'il n'avait pas tenus.

---

## 🌐 Publier sur fr.wordpress.org

Deux formats au choix :

**Version Markdown (par défaut)**
1. Créez un nouvel article et saisissez le titre donné par l'IA dans le champ « titre ».
2. Collez le texte dans l'éditeur : il se transforme en titres, listes et paragraphes.
3. Vérifiez les niveaux de titre, les lignes 📌 et le séparateur.

Cette conversion n'a pas encore été testée sur fr.wordpress.org.

**Version blocs**, fidèle à la composition de l'équipe (lignes 📌 sur fond bleu pâle, colonnes « pour / contre ») :
1. Demandez à l'IA « version blocs ».
2. Dans l'éditeur : menu ⋮ → **Éditeur de code**, collez le HTML.
3. Revenez à l'**Éditeur visuel** : tout est en place, inutile d'insérer la composition avant.

Le collage a été testé le 7 octobre 2026 dans WordPress Playground (WordPress 7.1) : aucun bloc signalé invalide.

Dans les deux cas, choisissez la catégorie « Réunions de l'équipe de traduction » et les étiquettes `compte-rendu` et `traductions`. Pour l'équipe Documentation, prenez les étiquettes `compte-rendu` et `documentation`.

---

## 🧪 Essayer sans réunion sous la main

Le dossier `exemples/` contient une vraie réunion, anonymisée : noms, pseudos et liens Slack fictifs.

1. Collez `exemples/2026-10-05-entree.txt` en précisant : « 101e réunion, lundi 5 octobre 2026, canal #traductions ».
2. Comparez le résultat avec `exemples/2026-10-05-cr-attendu.md`.

Les formulations peuvent différer, c'est normal. Ce qui compte :
- aucun oubli : participants, sujets ;
- aucune invention : décision, pseudo, chiffre ;
- des pseudos WordPress.org, pas Slack ;
- les messages postés après la clôture seulement listés dans la relecture ;
- une ligne 📌 sur chaque sujet à trancher, aucune sur un simple point d'information.

---

## 📁 Ce qu'il y a dans le dépôt

| Fichier | Rôle |
|---|---|
| `SKILL.md` | Les instructions complètes : c'est le seul fichier indispensable. |
| `participants.md` | Exemple fictif de table des pseudos (la vraie va dans `participants.local.md`). |
| `modeles/traduction.md`, `modeles/documentation.md` | Les squelettes de CR des deux équipes. |
| `modeles/composition-officielle.html` et `.json` | La composition « CR réunion traduction » de fr.wordpress.org/team, trame de la version blocs (le `.json` s'importe dans WordPress : Modèles → Importer depuis JSON). |
| `exemples/` | Une réunion anonymisée et le CR attendu, pour tester. |

---

## 🤝 Contribuer

Un CR raté, une règle à ajuster, un outil d'IA à ajouter au guide ? Ouvrez une [issue](https://github.com/reuhno/polyglots-fr-compte-rendu/issues) en joignant, si possible, le copier-coller (anonymisé) et ce que l'IA a produit.

## Licence

GPL-2.0-or-later, comme WordPress. Texte complet dans le fichier [LICENSE](LICENSE).
