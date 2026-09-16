# Plancher visuel

Lu par chaque agent qui dessine, en plus du brief, des fiches et de son
inspiration. Adapté d'`impeccable` v4.2.2 (Apache 2.0).

## Préséance

**L'inspiration de l'utilisateur gagne.** Si elle appelle une couleur, une
époque, une matière ou une police que ce fichier décourage, c'est l'inspiration
qui l'emporte, et ce n'est pas un écart à signaler. Ce plancher ne choisit pas
la direction ; il empêche de tomber dans celle que personne n'a choisie.

## Ce qui se mesure

Sur le rendu, pas sur l'intention. À vérifier avant de rendre.

- **Contraste** : texte courant et placeholder ≥ 4,5:1, grand texte ≥ 3:1.
- **Texte secondaire sur fond coloré** : teinté depuis cette teinte, jamais gris.
- **Ombres** : un décalage *et* un flou. Un halo coloré sans décalage est une
  décoration, pas une élévation.
- **Espacement** : groupes serrés, séparations généreuses, plus d'espace
  au-dessus d'un titre qu'en dessous.
- **Type** : des pas de taille et de graisse évidents. Le texte réel — les
  vraies strings françaises, plus longues que l'anglais — à chaque taille, et
  ce qui déborde est corrigé, pas rogné.
- **Cibles tactiles** : 48 dp minimum, 8 dp entre deux. Les libellés tiennent à
  `font_scale 1.3`.
- **États** : pressé, désactivé, en cours, erreur, vide. Avec du contenu réel.
- **Les surfaces qu'on ne dessine pas** : sélection de texte, caret, ripple,
  anneau de focus, barre de statut, chiffres tabulaires. Elles arrivent avec des
  défauts système qui n'appartiennent à aucune identité — thème-les depuis la
  palette.
- **Le sombre est un thème, pas une inversion.** Dessiné, pas dérivé.

## La couleur est une stratégie

Une stratégie se choisit avant les couleurs, sinon on empile des teintes.

- **Sobre** : des neutres et un seul accent, qui reste rare.
- **Engagée** : une couleur saturée qui tient 30 à 60 % de la surface.
- **Palette complète** : trois ou quatre rôles nommés, chacun avec son emploi.
- **Immergée** : la surface elle-même est la couleur, il n'y a pas de fond neutre.

Sur un fond neutre, l'accent principal occupe environ un dixième de l'écran :
sa rareté est le sujet. Une stratégie s'annonce et se tient sur tout l'écran ;
en changer d'un écran à l'autre est ce qui fait qu'une app a l'air assemblée.

## Ce qu'on ne dessine pas

Ce sont les défauts de la catégorie. L'inspiration peut en racheter n'importe
lequel ; y aller quand l'axe est libre veut dire qu'on n'a pas décidé.

- Des cartes de même taille (icône + titre + texte) comme structure d'écran.
  Une carte dans une carte est toujours fausse.
- Un surtitre au-dessus d'un titre. Celui-là ne se rachète pas : le titre porte
  son propre poids.
- Des numéros de section (01 / 02 / 03) quand la séquence n'informe personne.
- Du texte en dégradé. L'emphase vient de la graisse ou de la taille.
- Le verre dépoli et le flou comme décoration plutôt que comme effet précis.
- Une bordure gauche colorée de plus d'1 px sur une carte, une ligne de liste,
  une alerte.
- Une ombre dure sans flou hors d'un monde réellement néobrutaliste.
- Des sparklines, des anneaux de progression, des rectangles arrondis ombrés qui
  tiennent lieu de contenu.
- Le monospace en costume de « technique », hors code, données ou mesure.
- **Un glyphe Unicode ou un emoji à la place d'une icône.** Les icônes sont
  dessinées, d'une vraie bibliothèque, à graisse et à trait constants.
- Le clair ou le sombre choisi par catégorie. Il se choisit sur la scène
  d'usage : qui, où, sous quelle lumière.

## Ce qui sort tout seul quand rien ne l'en empêche

Les interfaces générées se regroupent sur trois looks, quelle que soit la
matière : fond crème chaud + serif d'affichage contrasté + accent terracotta ou
rouge signal ; presque-noir + un accent néon + bords lumineux ; filets
éditoriaux + serif italique + petites étiquettes mono trackées. Tous les trois
sont légitimes si l'inspiration les demande. Sans inspiration, y atterrir veut
dire qu'on n'a pas cherché.

Même chose pour les polices sur-représentées : Fraunces, Playfair Display,
Cormorant, Lora, Crimson, Newsreader, Syne, Space Grotesk, Space Mono, IBM Plex,
Inter en display, DM Sans, DM Serif, Outfit, Plus Jakarta Sans, Instrument Sans.
En nommer une demande une raison qu'aucune autre police ne satisferait —
« le sujet l'appelle » n'en est jamais une.

Un brief épingle un monde, pas la version la plus attendue de ce monde. Un
sujet livresque, chaleureux ou destiné aux enfants ne justifie ni le fond
crème ni le serif d'affichage : la gamme matérielle entière reste ouverte à
l'exécution. L'échec n'arrive pas au moment de choisir la direction, il arrive
au moment de la rendre, quand on atterrit sur le rendu le plus attendu du
monde qu'on venait d'épingler.

Test : si on pouvait deviner ton parti pris à partir de la seule catégorie de
l'app, ou de la catégorie plus son évitement le plus évident, recommence.

## Avant de rendre

Ce qu'on vérifie sur le rendu avant de le montrer. Chaque case se répond par
oui ou par non en regardant l'écran ; ce qui n'est pas vérifiable en le
regardant n'a pas sa place ici. Rien de neuf : chaque ligne pointe une règle
déjà écrite plus haut.

- [ ] Contraste mesuré, dans les deux thèmes.
- [ ] Le texte réel en français à chaque taille, et rien ne déborde.
- [ ] Cibles tactiles à 48 dp, 8 dp entre deux.
- [ ] Les libellés tiennent à `font_scale 1.3`.
- [ ] Chaque état dessiné, avec du contenu réel.
- [ ] Les surfaces système thémées depuis la palette.
- [ ] Aucune icône en emoji ni en glyphe Unicode.
- [ ] Le sombre dessiné, pas dérivé du clair.
- [ ] La même stratégie de couleur d'un écran à l'autre.
- [ ] Rien de la liste des refus que l'inspiration ne rachète.
- [ ] États et accessibilité passés à [`etats-et-acces.md`](etats-et-acces.md).
