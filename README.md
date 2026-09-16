# create-design

Un skill Claude Code qui transforme une idée d'app en app réellement codée, en vous faisant valider des **images** à chaque étape.

Vous n'avez jamais besoin de savoir designer. Vous regardez, vous dites ce qui ne vous plaît pas, l'agent corrige.

---

## Installation (2 minutes)

1. Téléchargez ce repo (bouton **Code → Download ZIP**, ou `git clone`).
2. Copiez le dossier `.claude/skills/create-design` à la racine de **votre** projet.
3. Ouvrez Claude Code dans votre projet et tapez :

```
/create-design
```

C'est tout. L'agent démarre et vous pose sa première question.

> Votre projet doit être un dépôt Git (`git init` si ce n'est pas déjà fait) : le skill enregistre chaque validation avec un commit.

---

## ⚠️ Le conseil le plus important : faites `/clear` avant chaque grosse étape

Le skill **sauvegarde tout son avancement** dans un fichier (`tmp/etat.md`) et dans vos commits. Il n'a donc **aucun besoin** de se souvenir de la conversation.

Avant de lancer une nouvelle étape, tapez :

```
/clear
/create-design
```

L'agent relit son fichier d'état, vous annonce où vous en êtes, et repart.

**Pourquoi c'est important :** une conversation trop longue fait perdre en qualité et en précision. Repartir propre à chaque étape donne de bien meilleurs résultats, et ça ne vous coûte rien.

**Quand le faire :** après chaque « c'est validé, on passe à la suite ». Si vous hésitez, faites-le — vous ne pouvez rien perdre.

### Le déroulé complet, étape par étape

Voici exactement ce que vous tapez, du début à la fin. Entre chaque bloc, vous discutez avec l'agent jusqu'à ce qu'il vous dise que l'étape est validée.

```
# 1. Le brief — on démarre
/create-design brief
```
*…vous répondez aux questions, l'agent écrit le brief, vous le validez.*

```
# 2. Les écrans — on repart propre
/clear
/create-design structure
```
*…vous validez la liste des écrans et leurs enchaînements.*

```
# 3. Le style — on repart propre
/clear
/create-design habillage
```
*…vous envoyez vos inspirations, l'agent vous montre 2-3 versions, vous choisissez.*

```
# 3b. Retouche du style — on repart propre
/clear
/create-design 3b
```
*…vous dites ce qui ne va pas sur les images, jusqu'à ce que ça vous plaise.*

```
# 4. Tous les écrans — on repart propre
/clear
/create-design extension
```

```
# 4b. Retouche des écrans — on repart propre
/clear
/create-design 4b
```

```
# 5. Le code — on repart propre
/clear
/create-design implementation
```

Si vous ne vous souvenez plus où vous en êtes, tapez `/create-design` **sans rien après** : l'agent lit son fichier d'état et vous le dit.

---

## Comment ça se passe : 5 étapes

À chaque étape, l'agent s'arrête et attend votre réponse. Il n'avance jamais tout seul.

| # | Étape | Ce qu'on vous demande | Ce que vous obtenez |
|---|-------|-----------------------|---------------------|
| 1 | **Le brief** | Répondre à ~7 questions simples (pour qui, sur quel écran, à quoi ça ne doit surtout pas ressembler…) | Une page qui résume votre projet |
| 2 | **Les écrans** | Dire si la liste des écrans est complète | Le plan de tous les écrans et de leurs enchaînements |
| 3 | **Le style** | Envoyer des captures ou des noms d'apps dont vous aimez le look, puis **choisir** parmi 2-3 versions | Le style de votre app, choisi sur images |
| 4 | **Tous les écrans** | Regarder et dire ce qui ne va pas | Tous les écrans dessinés dans ce style |
| 5 | **Le code** | Valider les captures finales | L'app codée, conforme aux images |

Le code de votre app ne bouge qu'à l'étape 5. Avant, tout se décide sur des images — c'est là que ça coûte le moins cher de changer d'avis.

---

## Les 3 choses que vous aurez à faire

**1. Répondre à des questions.** Jamais de question piège : l'agent propose toujours une réponse, vous confirmez ou vous corrigez.

**2. Envoyer des inspirations** (étape 3). Une capture d'écran, un lien, ou juste un nom d'app (« comme Notion »). Autant que vous voulez, ou aucune.

**3. Dire ce qui ne va pas.** Avec vos mots, pas des mots de designer :

> ✅ « le titre écrase le reste », « je ne trouve pas le bouton », « ça manque de contraste »
>
> ❌ pas besoin de dire « augmente le padding à 16px »

Vous pouvez aussi demander : **« qu'est-ce que tu vois qui ne va pas ? »** — l'agent regarde et vous propose des remarques, vous gardez celles que vous voulez.

---

## Reprendre plus tard

Fermez tout, revenez dans trois jours :

```
/clear
/create-design
```

L'agent relit son état et vous dit où vous en étiez. Vous n'avez rien à lui réexpliquer.

Pour sauter directement à une étape précise, ajoutez son nom — voir le déroulé complet plus haut. Noms disponibles : `brief`, `structure`, `habillage`, `3b`, `extension`, `4b`, `implementation`.

---

## Questions fréquentes

**J'ai déjà une app / des maquettes.**
Dites-le à l'étape 2 : l'agent part de l'existant au lieu d'inventer.

**Je n'ai aucune inspiration à donner.**
Répondez « aucune ». L'agent proposera trois styles à partir de votre brief.

**L'agent avance sans me demander mon avis.**
Ça ne devrait pas arriver. Dites-lui « tu ne m'as pas demandé mon avis » et faites `/clear` avant de relancer.

**Ça part dans une mauvaise direction.**
Tout est commité étape par étape : revenez au commit précédent et relancez l'étape.

**Combien de temps ?**
Comptez une bonne session par étape. Les étapes 3 et 4 sont les plus longues, c'est là que vous regardez et que vous choisissez.

---

## Licence

MIT. Le fichier `reference/plancher-visuel.md` est adapté d'`impeccable` v4.2.2 (Apache 2.0).
