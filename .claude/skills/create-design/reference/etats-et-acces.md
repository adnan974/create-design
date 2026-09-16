# États et accès

Lu par chaque agent qui dessine un écran et par celui qui l'implémente, en
plus du plancher visuel. Le plancher pose le sol commun ; ce fichier prolonge
ses seuils là où ils s'arrêtent, sans les redire. Seuils tirés de WCAG 2.2 et
de Material Design 3.

## Contraste, ce que le plancher ne mesure pas

- **Le non-texte se mesure aussi.** Une icône qui porte du sens, la bordure
  d'un contrôle, un indicateur d'état : 3:1 contre ce qui les entoure. Une
  icône qui ne tient pas ce seuil doit être purement décorative — et une
  icône décorative ne porte alors aucune information que le texte ne dise.
- **Le 3:1 ne déborde jamais sur le texte courant.** Sur une surface sombre,
  le corps de texte reste à 4,5:1 ; le 3:1 ne vaut que pour le grand texte et
  le non-texte. C'est l'erreur classique du sombre : on adoucit le blanc
  jusqu'à ce que ce soit reposant, et on passe sous le seuil.
- **Chaque thème se mesure seul.** Un ratio validé en clair ne dit rien du
  sombre. Deux thèmes, deux mesures, sur le rendu.

## Quand les états se cumulent

- **La priorité est fixe** : désactivé > en cours > actif > focus > survol >
  repos. Un bouton désactivé et survolé se dessine désactivé — on applique le
  plus haut, on ne mélange pas.
- **Le désactivé se lit encore.** Il s'obtient par l'opacité, autour de
  `0.5`, et retire l'interaction, pas la lisibilité : viser 3:1 sur le
  libellé même désactivé. En dessous, l'utilisateur ne sait plus ce qu'il ne
  peut pas faire, ce qui est pire que de ne pas pouvoir le faire.

## Le focus

- **Un anneau de 2 px avec 2 px de retrait**, thémé depuis la palette comme
  les autres surfaces que le plancher liste.
- **Visible dans les deux thèmes.** Sur fond sombre, l'anneau du thème clair
  disparaît : il se redessine, il ne se dérive pas.
- **Il ne se supprime jamais sans remplacement.** Retirer l'anneau système
  oblige à en fournir un autre, au moins aussi visible.
- **Il ne se laisse pas masquer.** Ni par une barre collante, ni par le
  clavier qui monte : un champ en bas d'écran qui reçoit le focus reste
  entièrement visible, anneau compris.

## Le sombre, ce qui casse quand on l'oublie

- **Pas de noir pur en fond** : viser `#121212` à `#1e1e1e`. Le noir absolu
  fait vibrer le texte et écrase toute élévation.
- **Pas de blanc pur en corps de texte** : `#e0e0e0` à `#f0f0f0`.
- **Les ombres ne se voient pas sur fond sombre.** C'est le point raté à tous
  les coups. L'élévation y passe par une bordure ou par une surface plus
  claire : Material 3 empile un voile tonal croissant sur les niveaux
  d'élévation, de l'ordre de +5 % en bas à +14 % en haut. C'est cette
  mécanique-là qu'on transpose. Un écran sombre dessiné en réutilisant les
  ombres du clair est un écran plat.

## Quatre exigences d'accessibilité récentes qui touchent cette app

- **Le focus n'est jamais masqué.** Même règle que plus haut ; c'est celle
  qui se casse le plus vite sur un écran qui défile ou qui ouvre un clavier.
- **Toute action qui demande de glisser a une alternative à un seul appui.**
  Balayer une ligne d'envoi pour la supprimer se double d'un bouton ou d'une
  entrée de menu qui fait la même chose.
- **Ce qui a déjà été saisi ne se redemande pas.** Dans un parcours à étapes,
  ce qui a été donné à l'étape précédente revient pré-rempli ou rappelé,
  jamais à ressaisir.
- **Un champ d'identification accepte le collage et les gestionnaires de mots
  de passe.** L'adresse Kindle se colle, elle ne se retape pas. Bloquer le
  collage « pour éviter les fautes » produit exactement les fautes.

## Ce que ça demande au code

- Tout élément interactif porte un libellé, un rôle et un état
  d'accessibilité. Un indice seulement quand l'action ne se devine pas depuis
  le libellé.
- Jamais d'emoji dans un libellé lu à voix haute : il se prononce, et mal.
- Les changements d'état qui comptent — envoi en cours, envoi réussi, échec —
  sont annoncés, pas seulement affichés.
- Le mouvement réduit se demande au système et se respecte.

## Un état n'est pas une variante, c'est un écran

Le plancher demande de les dessiner ; voici ce qu'ils doivent dire.

- **Une erreur dit quoi faire ensuite**, pas seulement ce qui a échoué.
  « Envoi impossible » n'est pas un message ; « adresse refusée, vérifie
  qu'elle se termine par @kindle.com » en est un.
- **Un état vide dit pourquoi il est vide et par où commencer.** Un premier
  lancement et une liste filtrée à zéro ne se ressemblent pas.
- **La couleur seule ne signale jamais rien.** Un état porte toujours un
  libellé ou une forme en plus de sa couleur.
