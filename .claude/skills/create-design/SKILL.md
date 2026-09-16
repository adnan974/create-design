---
description: Méthode design en cinq étapes, du brief à l'app implémentée, avec des agents. Brief → Structure → Habillage → Extension → Implémentation, l'habillage et l'extension suivis de leur affinage.
disable-model-invocation: true
argument-hint: "[brief|structure|habillage|3b|extension|4b|implementation]"
---

# Méthode design en cinq étapes

On décide sur peu d'écrans, on applique sur tous, on implémente une fois. Le design coûte cher là où il y a des choix ; partout ailleurs il est mécanique.

**Point d'entrée** : `$ARGUMENTS` nomme une étape (`brief`, `structure`, `habillage`, `3b`, `extension`, `4b`, `implementation`) : exécuter cette étape seule, en supposant les précédentes faites. Sans argument, lire `tmp/etat.md` pour connaître l'étape en cours et l'annoncer à l'utilisateur avant de commencer. Si `tmp/etat.md` est introuvable, on démarre à l'étape 1, Le Brief : l'agent n'en cherche pas la confirmation et ne propose pas d'entrer ailleurs. `affinage` sans numéro désigne l'affinage de l'étape en cours dans `tmp/etat.md`.

**Étapes et affinages** : cinq étapes numérotées. Les deux qui produisent des images — l'habillage, l'extension — portent chacune son affinage, `3b` et `4b` : la même boucle, sur ce que l'étape vient de produire. La structure a la sienne aussi, dans l'étape et sans numéro, parce qu'elle ne se juge pas sur des images. Une étape et son affinage font une paire : rien ne s'annonce entre les deux, la fin d'étape se dit au bout de l'affinage.

**Arrêt utilisateur** : chaque étape contient des points marqués ⏸ où l'agent s'arrête, pose sa question ou présente ses images, et attend la réponse. L'agent ne devine jamais ce que l'utilisateur doit dire là : pas d'inspiration inventée, pas de gagnante choisie à sa place, pas de variante validée par défaut. Une étape ne se termine que sur un ⏸ validé par l'utilisateur. À chaque ⏸, l'agent parle à quelqu'un qui n'a pas lu cette méthode : la question d'abord, en trois phrases au plus, avec la forme de réponse attendue et un exemple ; ce que l'agent a fait avant tient en une ligne, après la question.

**Langage** : face à l'utilisateur — à un ⏸ comme dans le compte rendu d'une étape — aucun mot de métier ni de méthode n'apparaît seul. `token`, `artefact`, `canvas`, `kit UI`, `composant`, `wireframe`, `flow`, `identifiant`, `proposition`, `cadre` sont interdits tels quels ; on dit « les couleurs et les tailles de l'app », « la page où tu regardes les écrans », « la planche », « la boîte à outils des éléments qui reviennent », « un bouton, une carte, un champ », « le plan des écrans », « le dessin de l'écran », « un parcours », « le numéro de l'écran », « une version ». Le nom technique peut suivre une fois entre parenthèses, jamais remplacer la formulation courante. Un lien se présente par ce qu'on va y voir, pas par le nom de l'outil qui l'a produit.

**Fin d'étape** : une étape ne se referme jamais en silence, et jamais sans annoncer la suivante. Quand la sortie est atteinte et commitée, l'agent dit à l'utilisateur, en trois phrases au plus et sans mot de la méthode : ce qui vient d'être décidé, ce que la suite va lui demander de faire (regarder des images, envoyer des inspirations, dire ce qui ne va pas), et ce qu'elle produira. Puis ⏸ : il demande s'il continue maintenant, s'arrête si l'utilisateur ne répond pas oui. Enchaîner sur l'étape suivante sans cette annonce, ou s'arrêter sur un « c'est commité » sans dire ce qui vient après, est un manquement au même titre qu'un ⏸ sauté.

L'annonce tient en trois temps — c'est fait / voilà la suite / ce que j'attends de toi — dans des mots que quelqu'un qui n'a pas lu cette méthode comprend :

> C'est bon : la liste des écrans et leurs enchaînements sont arrêtés. La suite, c'est le style — je vais te demander des captures ou des noms d'apps dont tu aimes le look, puis je te montrerai deux ou trois versions du même écran pour que tu choisisses. On y va ?

Même chose au début d'une session : avant la première question, une phrase qui situe où on en est et ce qu'on va faire. L'utilisateur n'a jamais à savoir qu'il existe six étapes ni comment elles s'appellent ; c'est l'agent qui sait toujours quelle est la suivante et qui la propose. À la toute fin, l'étape 6 s'annonce comme la dernière : il n'y a pas de suite à proposer, l'agent dit ce qui remplace la méthode.

**Fichier d'état** : `tmp/etat.md`, tenu à jour à chaque commit. Il contient l'étape en cours, le chemin du dossier `tmp/wireframe/` qui tient les `.md` du plan des écrans, l'URL de l'artefact de référence, les chemins du brief, de la décision et du kit, et pour l'étape en cours la liste des écrans validés, en cours, restants. C'est la seule chose qu'un contexte vide a besoin de lire pour reprendre.

## 1. Le Brief

Cette étape est entièrement écrite : on définit le besoin, on pose les contraintes, on répond aux questions. Aucun écran, aucune liste d'écrans, aucun dessin, aucun mot de style — ni ici ni dans la tête de l'agent.

**Livrable** : un brief de dix lignes écrit dans le dossier `tmp/` du dépôt et commité (pour qui, ce que le produit fait, ce qu'il ne doit pas être, format de référence, styles écartés, thème de référence, taille de texte minimale, contraintes techniques). Le brief décrit le problème, jamais la solution : des contraintes dures, zéro adjectif de style.

**Le format de référence** : une seule taille d'écran, celle sur laquelle on décide, écrite dans le brief avec ses dimensions. Tout en découle — la largeur du cadre des dessins à l'étape 2, la taille des planches à l'étape 3, celle des captures à l'étape 5 — et des agents lancés en parallèle qui ne l'ont pas reçue la choisissent chacun de leur côté : les propositions ne se comparent plus, et personne ne voit pourquoi. L'agent demande, en ces termes ou presque : « Sur quel écran tu regardes cette app en premier — un téléphone tenu à la verticale, une tablette, un ordinateur ? » Puis il traduit la réponse en dimensions et les fait valider dans la relecture. Une seconde taille se décide après l'étape 3b, jamais avant.

**Les styles écartés** : ce dont l'utilisateur ne veut pas, dans les mêmes formes qu'une inspiration à l'étape 3 — une app nommée, une capture, un monde concret. La question se pose une fois, et avec des propositions : l'utilisateur n'a pas à chercher dans le vide, il écarte. L'agent avance trois ou quatre styles que le brief rend plausibles, chacun en une ligne et en mots d'écran, puis demande, en ces termes ou presque :

> Est-ce qu'il y en a un là-dedans dont tu ne veux surtout pas ?
> 1. très dense, beaucoup d'informations par écran, comme une appli bancaire ;
> 2. très arrondi et coloré, comme un jeu ;
> 3. très dépouillé, presque du texte seul.
> Tu peux en écarter plusieurs, m'en donner un autre, ou aucun.

Aucun est une réponse : on n'insiste pas et l'agent n'invente pas un refus. Ce qui est écarté entre au brief tel quel et repart, à l'étape 3, dans le brief de chaque sous-agent à côté de son inspiration, où il ferme l'espace des propositions du côté où il est le plus large. Un style écarté ne se discute plus ensuite : il revient ici ou nulle part.

**Aucune question nue** : chaque question arrive avec la réponse que l'agent propose — tirée du dépôt, du format déjà répondu, ou de l'usage courant — et l'utilisateur confirme ou corrige. « Rien en dessous de 13 ? », pas « quelle taille de texte minimale ? ». Une question nue fait chercher l'utilisateur à la place de l'agent : il répond mal, ou il ne répond pas.

**Ce qu'on ne demande pas** : où s'arrête le travail. La méthode va jusqu'à l'app implémentée — c'est son objet, pas une option, et ça ne se met pas au vote. Ce que l'agent annonce, c'est l'ordre des choses, en une phrase : « on décide sur des images ; le code de l'app ne bouge qu'à la fin, une fois que tu auras validé les écrans. » Puis il passe à la suite.

⏸ L'agent rédige le brief à partir de ce qu'il sait et pose à l'utilisateur les questions restantes, une par ligne vide du brief. Une question par tour quand elles sont peu nombreuses, groupées et numérotées sinon ; jamais de réponse inventée à la place de l'utilisateur. Chaque ligne du livrable est couverte, par une question ou par une proposition acceptée. Avant de clore ce ⏸, l'agent vérifie qu'il a posé les sept :

1. pour qui, et ce que fait le produit ;
2. ce que le produit ne doit pas faire — le périmètre, pas le style ;
3. le format de référence ;
4. le thème livré — clair, sombre, ou les deux ;
5. la taille de texte minimale ;
6. les contraintes techniques ;
7. **à quoi l'app ne doit surtout pas ressembler.**

La septième est celle qui saute, parce que c'est la seule dont la réponse n'est nulle part dans le dépôt. L'agent la pose quand même, avec ses propositions, même s'il croit connaître le goût de l'utilisateur.

⏸ L'agent relit le brief à l'utilisateur en clair et demande ce qui manque ou ce qui est faux. L'utilisateur tranche, puis valide. Une contrainte qui apparaît plus tard revient ici : le brief est le seul endroit où elle vit.

**Sortie** : un brief sans aucune question ouverte, validé mot à mot par l'utilisateur, commité. Puis fin d'étape.

## 2. La Structure

Cette étape range l'information : quels écrans existent, dans quel ordre on les traverse, dans quels états ils se trouvent, lesquels sont les plus chargés d'enseignement. Toujours aucun style : pas de couleur, pas de typo, pas d'ambiance.

**Le plan des écrans** : un fichier `.md` par parcours, `tmp/wireframe/<parcours>.md`, et rien d'autre — pas d'autre format, pas d'image à côté, pas de dossier ailleurs. Un fichier tient les écrans-états de son parcours (repos, vide, erreur, limite) ; un écran-état y est une fiche suivie du dessin de son écran, les deux dans le même `.md`. Une fiche porte un identifiant stable, sa route dans le code, l'état qu'elle décrit, d'où on y arrive et vers quoi elle mène, puis son contenu : les zones de l'écran dans l'ordre où on les lit, du haut vers le bas, chacune en une ligne — ce qu'elle est (titre, texte, bouton, champ, liste, image), son vrai libellé, et ce qu'elle déclenche. Une liste de noms d'écrans n'est pas un plan : une fiche sans son contenu zone par zone n'est pas finie. Rien d'autre n'y entre : pas de couleur, pas de typo, pas de mesure, aucune image — la fiche dit quoi, dans quel ordre et vers où, jamais à quoi ça ressemble. Un à trois écrans marqués « clé » : ensemble, ils montrent le plus de variété de l'app. Le plan est la seule liste des écrans et vit après le projet.

**Le dessin de l'écran** : chaque fiche se termine par le dessin de son écran en caractères, dans un bloc de code ; une fiche sans son dessin n'est pas finie. Il se regarde comme l'écran se regarde — un cadre de largeur fixe, la même pour tout le plan, les zones à leur place et dans l'ordre de la fiche, une zone par bloc, son vrai libellé écrit dedans, les hauteurs relatives tenues (une barre est fine, une liste prend ce qu'elle prend, un bouton pleine largeur touche les deux bords). Ce qui se répète se montre deux ou trois fois puis `...`. Ce qui déborde se coupe au cadre. Le dessin ne porte que la structure : traits, cadres, libellés — jamais une couleur, une police, une ombre, une mesure, et jamais un glyphe ou un emoji en guise d'icône, qui s'écrit `[icone: envoyer]`. Le dessin et la fiche disent la même chose sous les mêmes libellés : une zone dans l'un est une ligne dans l'autre, et une divergence se corrige des deux côtés.

```
+------------------------------+
| <-  Envoyer au Kindle        |   barre
+------------------------------+
|  +------------------------+  |
|  | [icone: fichier]       |  |
|  | rapport-2026.epub      |  |   carte du fichier choisi
|  | 2,4 Mo                 |  |
|  +------------------------+  |
|                              |
|  Adresse Kindle              |
|  +------------------------+  |
|  | mon-adresse@kindle.com    |  |   champ
|  +------------------------+  |
|                              |
|  Envois recents              |
|  - rapport-2025.epub         |
|  - notes.md                  |
|  - ...                       |
|                              |
+------------------------------+
| +--------------------------+ |
| |         Envoyer          | |   bouton pleine largeur
| +--------------------------+ |
+------------------------------+
```

**Écrans existants** : si l'utilisateur apporte une app déjà dessinée ou déjà codée (captures, maquettes, code), l'agent n'invente rien — il remplit les mêmes fiches et redessine les mêmes écrans d'après ce qu'il voit, vue par vue, état par état, puis isole un à trois écrans clés selon la même règle de variété. Le plan a la même forme dans les deux cas ; seule sa source change, le brief ou l'existant.

⏸ Obligatoire : l'agent relit le plan à l'utilisateur en clair — les écrans avec leurs états, et les écrans clés qu'il propose — et demande « Est-ce que cette liste est complète et ces écrans clés sont les bons ? ». L'étape ne peut pas se terminer sans cette réponse. L'utilisateur ajoute, retire, corrige ; l'agent reprend le plan et redemande, jusqu'au oui. Le fichier est là pour être ouvert, mais l'utilisateur n'a pas à le lire pour répondre.

**Affinage de la structure**, même boucle qu'à l'étape 3b mais sur les écrans et leur enchaînement, jamais sur le style :
1. ⏸ L'utilisateur dit ce qui ne va pas, pas ce qu'il faut faire (« il manque l'écran quand la liste est vide », « ces deux écrans n'en font qu'un », « le bouton d'envoi n'est pas là où je le cherche »). Il peut aussi demander à l'agent ce qu'il voit qui ne va pas : l'agent relit le plan et répond avec des remarques du même genre, que l'utilisateur garde ou écarte. Cinq remarques par tour au plus.
2. L'agent répond par écrit, sans redessiner, en mots d'écran (ce qu'il contient, dans quel ordre, à quelle place, dans quel état), jamais en termes techniques : ce qui cause le problème, puis deux ou trois manières de le régler en une ligne chacune. C'est une discussion : l'utilisateur réagit, précise ou demande autre chose avant de valider.
3. ⏸ L'utilisateur valide ce qui est corrigé, discute, ou refuse tout et l'agent repropose. Un seul agent reprend le plan, fiche et dessin dans le même mouvement : un écran corrigé garde son identifiant, un écran nouveau en prend un nouveau, un écran supprimé libère le sien et ne le rend à personne.
4. ⏸ L'utilisateur valide sur le plan relu en clair. Commit dans le même mouvement, avec `tmp/etat.md` mis à jour dedans.

Une remarque de couleur, de typo ou d'ambiance ne se règle pas ici : l'agent la note dans le brief pour l'étape 3 et le dit. La boucle tourne jusqu'à ce que l'utilisateur dise que la liste des écrans est bonne et que les écrans clés sont les bons.

**Sortie** : chaque écran-état a sa fiche, son dessin, un identifiant, une route ; les parcours sont écrits ; un à trois écrans clés sont désignés et confirmés par l'utilisateur. Tout commité. Puis fin d'étape.

## 3. Habillage

**Inspirations** : ce que l'utilisateur aime, dans la forme qu'il veut, en nombre libre, zéro compris. Une inspiration est une image, un dossier d'images, une URL ou un nom d'app. Formes valables :
- une capture d'écran ou un dossier de captures, posés dans `tmp/` ;
- une URL, que l'agent capture lui-même (`chromium --headless --screenshot=inspiration.png --window-size=1280,1600 {url}`) sans la regarder ; s'il ne peut pas capturer, il le dit et l'utilisateur envoie une capture ;
- un produit nommé ou un monde concret (« Things », « un ticket de caisse »).

Les inspirations sont commitées avant tout lancement. L'utilisateur n'a rien à expliquer : c'est le sous-agent qui analyse la sienne.

**L'orchestrateur ne regarde pas les inspirations** : il les récupère, les commite, et passe un chemin. Rien d'autre n'entre dans le brief d'un sous-agent — pas une palette, pas un nom de police, pas une densité, pas une ambiance, pas une phrase qui résume l'image. Une analyse écrite une fois en haut se retrouve dans toutes les propositions : elles convergent, et le choix sur images de la fin d'étape ne compare plus rien. L'analyse est le travail du sous-agent, et c'est la moitié de ce qu'on lui demande. Un orchestrateur qui a vu une image malgré tout ne la résume pas pour autant : le chemin, et rien de plus.

⏸ L'agent demande, en ces termes ou presque : « Envoie-moi des captures, des liens ou des noms d'apps dont tu aimes le style. Autant que tu veux, ou aucun. »

**Livrable** : une proposition par inspiration, un sous-agent par proposition en parallèle, un artefact chacune, jamais deux mains sur le même, toutes sur les mêmes écrans clés dans le thème de référence. Chaque sous-agent reçoit le brief, les fiches des écrans clés, sa seule inspiration, le plancher visuel ([`reference/plancher-visuel.md`](reference/plancher-visuel.md)) ainsi que les états et l'accessibilité ([`reference/etats-et-acces.md`](reference/etats-et-acces.md)) ; il agit en designer front expert : avant de dessiner, il analyse l'inspiration en détail (palette, typographie et hiérarchie des textes, espacements et densité, formes des composants, ce qui fait le caractère du style), en tire le style sans copier la page, et écrit dans l'artefact ce qu'il en a retenu. Sans inspiration, trois propositions à partir du brief et de la structure seuls. Chaque proposition vient avec son kit minimal : un fichier de tokens (couleurs, type, espacements, rayons) et les seuls composants que ses écrans utilisent, dans leurs états. Le kit est un fichier, pas une planche ni une documentation : on juge sur les écrans à taille réelle. Un composant que les écrans clés n'utilisent pas n'existe pas encore. L'orchestrateur ne dessine pas.

⏸ L'agent présente les liens des propositions. L'utilisateur choisit la gagnante sur les images. On élimine, on ne retouche pas.

**Sortie** : une décision d'une page écrite dans `tmp/` et commitée (gagnante, perdantes, ce que la gagnante retient des inspirations). L'artefact de la gagnante devient l'artefact de référence et son kit devient le kit ; l'affinage continue dessus, sans redessiner. La décision contient l'URL de l'artefact de référence et le chemin de son kit : c'est là qu'un nouveau contexte les retrouve. Perdantes archivées avec leur kit. L'affinage enchaîne sans annonce de fin d'étape.

## 3b. Affinage

**Livrable** : les écrans clés validés dans chaque thème livré, et le kit fermé qui en découle (tokens, échelle de type, composants réellement utilisés, icônes). Sources dans le dépôt, commit à chaque validation.

**La boucle**, pilotée par l'utilisateur à chaque tour :
1. ⏸ L'utilisateur regarde un écran clé et dit ce qui ne va pas, pas ce qu'il faut faire (« le titre écrase le texte », « pas assez de contraste »). Il peut aussi demander à l'agent ce qu'il voit qui ne va pas : l'agent regarde l'image et répond avec des remarques du même genre, que l'utilisateur garde ou écarte. Cinq remarques par tour au plus.
2. L'agent répond par écrit, sans dessiner, en mots de design (contraste, taille, espace, hiérarchie, alignement, couleur), jamais en termes techniques (token, composant, classe, valeur) : ce qui cause le problème, puis deux ou trois variantes en une ligne chacune. C'est une discussion : l'utilisateur réagit, précise ou demande autre chose avant de valider. En interne, l'agent cherche d'abord si un réglage existant du kit peut bouger. Une remarque qui porte sur un état, un contraste ou le thème sombre se tranche sur les états et l'accessibilité ([`reference/etats-et-acces.md`](reference/etats-et-acces.md)), qui ne se négocie pas : l'inspiration rachète un parti pris visuel, jamais un seuil.
3. ⏸ L'utilisateur valide les variantes à rendre, discute, ou refuse tout et l'agent repropose. Seules les validées sont rendues, par un seul agent, dans l'artefact de référence, comme cadres côte à côte à côté de l'écran concerné, nommées par ce qu'elles changent. Pas de nouvel artefact pour une variante.
4. ⏸ L'utilisateur choisit sur les images. Une variante est une modification du kit : la choisir met le kit à jour, remplace l'écran de référence par la gagnante, retire les cadres perdants du canvas en archivant leur source dans `tmp/`, commit dans le même message.

Quand l'utilisateur sait déjà ce qu'il veut, pas de variante : l'agent applique. Quand la session s'allonge ou que le contexte est vidé, repartir de `tmp/etat.md` et des sources, avec l'ordre de converger sans nouvelle variante.

⏸ Un écran est validé quand l'utilisateur le dit, sur l'image. L'étape se termine quand il l'a dit pour chaque écran clé dans chaque thème.

**Sortie** : plus aucune variante sur le canvas, un seul artefact de référence, perdantes archivées, kit fermé et cohérent, tout commité. Puis fin d'étape.

## 4. Extension

**Livrable** : chaque écran restant rendu avec le kit, dans chaque thème, sous l'identifiant de sa fiche. On applique la proposition choisie, on n'en invente plus.

**Ce que lit un agent avant de dessiner**, dans cet ordre : les écrans clés validés dans l'artefact de référence, qu'il *regarde* comme des images avant d'ouvrir le moindre fichier ; le kit fermé, sa seule source de couleurs, de tailles, d'espaces et de composants ; la décision de l'étape 3, qui dit ce que la gagnante retient de son inspiration ; les fiches et les dessins de son flow dans `tmp/wireframe/`, qui disent quoi mettre, dans quel ordre et vers où ; le brief, pour les contraintes dures ; le plancher visuel ([`reference/plancher-visuel.md`](reference/plancher-visuel.md)), qu'il vérifie sur son rendu ; les états et l'accessibilité ([`reference/etats-et-acces.md`](reference/etats-et-acces.md)), qu'il vérifie de même, dans chaque thème. L'URL de l'artefact de référence et les chemins viennent de `tmp/etat.md`, pas de la mémoire de l'orchestrateur, et l'orchestrateur les passe dans le brief de chaque agent. Un agent qui n'a pas regardé les écrans de référence redessine une proposition au lieu de l'étendre : c'est le défaut ordinaire de cette étape, et un écran qui ne ressemble pas aux écrans clés revient à son agent.

**Ce qu'écrit un agent** : la part propre à son écran, jamais le système de design. Le bloc de style est le même dans toutes les planches : il vit dans un fichier, un script le recolle. Un agent qui le retape sort les deux tiers de ses tokens en style déjà écrit ailleurs, et fait diverger les planches. Une planche par écran, un fichier par planche, nommé par l'identifiant de la fiche — deux flows ne touchent jamais le même fichier, donc le parallèle n'entre pas en collision et personne ne publie contre personne.

**Ce qu'un agent n'ouvre pas** : les planches des autres écrans, ni le rendu complet de la maquette. Il regarde les écrans de référence comme des images — c'est cinq fois moins cher que leur source, et c'est ce qui fait ressembler son écran aux leurs.

**Lancement** : un sous-agent par flow, en parallèle, kit fermé. Un agent à qui manque un composant s'arrête et le signale. L'orchestrateur ouvre le kit entre deux lots, ajoute, referme. Si les agents doivent écrire dans le kit, ils passent en séquentiel. Une seule publication par lot, jamais par écran : l'artefact est un rendu, on le refait quand le lot est fini, et il reste unique du début à la fin. Pour relire l'ensemble, la planche contact montre tous les écrans en une image.

⏸ Un composant manquant est présenté à l'utilisateur avant d'entrer au kit.

## 4b. Affinage de l'extension

Même boucle qu'à l'étape 3b, mêmes ⏸, avec une différence : une variante validée qui touche un composant re-rend tous les écrans qui l'utilisent, et l'utilisateur les revoit avant commit. Une remarque qui revient sur plusieurs écrans est un défaut du kit, corrigé une fois. Plus de quelques composants ajoutés ici signifie que les écrans clés étaient mal choisis : le noter.

**Sortie** : chaque fiche a son écran dans chaque thème, validé par l'utilisateur, kit fermé et cohérent avec tous les écrans, tout commité. Puis fin d'étape.

## 5. Implémentation

**Livrable** : l'app sur la proposition choisie. Cette étape transpose, elle ne dessine rien. Chaque écran du code répond à un écran de la maquette sous le même identifiant.

**Séquence**, trois agents au plus :
1. **Fondations**, un agent : tokens, polices, icônes, et la preuve que la chaîne de capture fonctionne.
2. **Kit**, un agent : les composants de l'étape 3b, chaque état, chaque thème, exposés dans une galerie de l'app.
3. **Écrans**, par flow, kit fermé : même règle d'arrêt qu'à l'étape 4. La consigne vit dans un fichier de commande écrit une fois : kit fermé, lire les fichiers, s'arrêter s'il manque un composant, ne rendre que les captures.

Chaque écran produit une capture par thème nommée par son identifiant, posée à côté de la maquette du même nom. L'orchestrateur ne regarde que ces paires. Avant l'échantillon, chaque écran livré se vérifie dans chaque thème contre les états et l'accessibilité ([`reference/etats-et-acces.md`](reference/etats-et-acces.md)).

⏸ Avant le commit final, l'agent présente à l'utilisateur un échantillon de paires capture / maquette dans chaque thème. L'utilisateur valide ou renvoie des écrans.

**Après le merge** : l'app qui tourne devient la référence avec sa galerie ; la maquette est gelée et datée, une retouche se fait dans l'app. Une fonctionnalité nouvelle commence par une fiche (identifiant, route) et se compose avec le kit ; le canvas ne revient que pour un composant nouveau.

**Sortie** : chaque identifiant a sa capture dans chaque thème, vérifié par une liste de fichiers. Échantillon validé par l'utilisateur. Tests et lint verts une fois, à la fin. Un commit. Maquette datée, structure disant comment on ajoute un écran. Fin d'étape une dernière fois : l'agent dit à l'utilisateur que la maquette est gelée et comment se passe désormais une retouche ou un écran nouveau.

## Sept règles, à toutes les étapes

- **Une source, dans le dépôt** : l'artefact est un rendu, les sources sont versionnées dès la première publication.
- **Un identifiant, de la fiche à la capture** : fiche, artboard, capture portent le même numéro.
- **Une main par artefact** : un seul agent écrit dans un artefact à la fois ; les variantes vivent comme cadres dans l'artefact de référence, pas dans de nouveaux artefacts.
- **Commit à chaque validation** : « X est la référence » se termine par un commit, avec `tmp/etat.md` mis à jour dedans.
- **Critère de fin écrit** : un écran est fini quand l'utilisateur l'a validé sur l'image et que c'est noté dans `tmp/etat.md` ; « jusqu'à ce que ça convienne » n'en est pas un.
- **L'agent lit, l'utilisateur ne paraphrase pas** : aucun nombre ni classe dans un brief d'agent ; un diff et une capture par agent.
- **Jamais de fin muette** : une étape se termine en annonçant la suivante en clair — ce qui est fait, ce qui vient, ce que l'utilisateur aura à faire — puis en demandant s'il continue.

## Ce qui s'adapte

- Un seul thème livré : « chaque thème » se lit « le thème ».
- App existante : l'étape 2 remplit les fiches d'après l'existant au lieu de les écrire d'après le brief, tout le reste est identique.
- Outil de dessin libre (canvas, Figma, HTML) : la méthode ne demande que des artboards nommés par identifiant et des sources commitées.
- La chaîne de capture dépend de la stack : c'est le seul outillage à prouver avant l'étape 5.
