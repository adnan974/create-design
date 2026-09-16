# create-design

Un skill Claude Code qui transforme une idée d'app en app réellement codée, en te faisant valider des **images** à chaque étape.

Tu n'as jamais besoin de savoir designer. Tu regardes, tu dis ce qui ne te plaît pas, l'agent corrige.

---

## Installation (2 minutes)

1. Télécharge ce repo (bouton **Code → Download ZIP**, ou `git clone`).
2. Copie le dossier `.claude/skills/create-design` à la racine de **ton** projet.
3. Ouvre Claude Code dans ton projet et tape :

```
/create-design
```

C'est tout. L'agent démarre et te pose sa première question.

> Ton projet doit être un dépôt Git (`git init` si ce n'est pas déjà fait) : le skill enregistre chaque validation avec un commit.

---

## ⚠️ Le conseil le plus important : fais `/clear` avant chaque grosse étape

Le skill **sauvegarde tout son avancement** dans un fichier (`tmp/etat.md`) et dans tes commits. Il n'a donc **aucun besoin** de se souvenir de la conversation.

Avant de lancer une nouvelle étape, tape :

```
/clear
/create-design
```

L'agent relit son fichier d'état, t'annonce où vous en êtes, et repart.

**Pourquoi c'est important :** une conversation trop longue fait perdre en qualité et en précision. Repartir propre à chaque étape donne de bien meilleurs résultats, et ça ne te coûte rien.

**Quand le faire :** après chaque « c'est validé, on passe à la suite ». Si tu hésites, fais-le — tu ne peux rien perdre.

---

## Comment ça se passe : 5 étapes

À chaque étape, l'agent s'arrête et attend ta réponse. Il n'avance jamais tout seul.

| # | Étape | Ce qu'on te demande | Ce que tu obtiens |
|---|-------|---------------------|-------------------|
| 1 | **Le brief** | Répondre à ~7 questions simples (pour qui, sur quel écran, à quoi ça ne doit surtout pas ressembler…) | Une page qui résume ton projet |
| 2 | **Les écrans** | Dire si la liste des écrans est complète | Le plan de tous les écrans et de leurs enchaînements |
| 3 | **Le style** | Envoyer des captures ou des noms d'apps dont tu aimes le look, puis **choisir** parmi 2-3 versions | Le style de ton app, choisi sur images |
| 4 | **Tous les écrans** | Regarder et dire ce qui ne va pas | Tous les écrans dessinés dans ce style |
| 5 | **Le code** | Valider les captures finales | L'app codée, conforme aux images |

Le code de ton app ne bouge qu'à l'étape 5. Avant, tout se décide sur des images — c'est là que ça coûte le moins cher de changer d'avis.

---

## Les 3 choses que tu auras à faire

**1. Répondre à des questions.** Jamais de question piège : l'agent propose toujours une réponse, tu confirmes ou tu corriges.

**2. Envoyer des inspirations** (étape 3). Une capture d'écran, un lien, ou juste un nom d'app (« comme Notion »). Autant que tu veux, ou aucune.

**3. Dire ce qui ne va pas.** Avec tes mots, pas des mots de designer :

> ✅ « le titre écrase le reste », « je ne trouve pas le bouton », « ça manque de contraste »
>
> ❌ pas besoin de dire « augmente le padding à 16px »

Tu peux aussi demander : **« qu'est-ce que tu vois qui ne va pas ? »** — l'agent regarde et te propose des remarques, tu gardes celles que tu veux.

---

## Reprendre plus tard

Ferme tout, reviens dans trois jours, tape `/create-design` : l'agent relit son état et te dit où vous en étiez.

Tu peux aussi sauter directement à une étape :

```
/create-design habillage
```

Étapes disponibles : `brief`, `structure`, `habillage`, `3b`, `extension`, `4b`, `implementation`
(`3b` et `4b` sont les phases de retouche du style et des écrans.)

---

## Questions fréquentes

**J'ai déjà une app / des maquettes.**
Dis-le à l'étape 2 : l'agent part de l'existant au lieu d'inventer.

**Je n'ai aucune inspiration à donner.**
Réponds « aucune ». L'agent proposera trois styles à partir de ton brief.

**L'agent avance sans me demander mon avis.**
Ça ne devrait pas arriver. Dis-lui « tu ne m'as pas demandé mon avis » et fais `/clear` avant de relancer.

**Ça part dans une mauvaise direction.**
Tout est commité étape par étape : reviens au commit précédent et relance l'étape.

**Combien de temps ?**
Compte une bonne session par étape. Les étapes 3 et 4 sont les plus longues, c'est là que tu regardes et que tu choisis.

---

## Licence

MIT. Le fichier `reference/plancher-visuel.md` est adapté d'`impeccable` v4.2.2 (Apache 2.0).
