---
name: "redaction-user-stories"
description: "Rédige des user stories / spécifications fonctionnelles détaillées selon la trame en 7 sections de l'utilisateur, à partir de ses documents produit, avec sources tracées et trous signalés sans rien inventer. À utiliser dès qu'on parle de user story, spec fonctionnelle, règles de gestion ou critères d'acceptation."
---

# Rédaction de user stories

Ce skill sert à produire des user stories qui respectent la trame de l'utilisateur, couvrent tout le périmètre des documents fournis et permettent de retrouver la source de chaque exigence. Il combine deux choses : la démarche de rédaction (ci-dessous) et la trame à reproduire à l'identique (plus bas).

Langue : français. Les libellés d'interface cités restent tels qu'ils apparaissent dans les sources.

## Principe directeur : ne jamais inventer

Une spec sert de contrat. Une règle métier inventée est plus dangereuse qu'une règle manquante, car elle sera développée puis testée comme si elle était validée. Donc :
- Chaque règle de gestion, comportement ou critère doit venir d'un document fourni (brief, maquette, interview, règle métier, échange avec l'utilisateur).
- Deux marqueurs distincts signalent ce qui n'est pas établi. Ils appellent deux réponses différentes, il ne faut donc pas les confondre :
  - `[À CLARIFIER]` : l'information **manque** ou est **ambiguë** dans les sources. Il reste une question à poser.
  - `[CONTRADICTION]` : on **dispose** de l'information, mais **deux sources (ou plus) disent des choses incompatibles** et aucune hiérarchie donnée par l'utilisateur ne tranche. Il reste un arbitrage à obtenir.
  Chaque marqueur est placé à l'endroit où il gêne et repris en section 7. On ne comble jamais par une hypothèse « raisonnable ».
- Un `[CONTRADICTION]` cite toujours les deux versions, chacune avec sa source, à l'endroit où il apparaît (par exemple sous la règle de gestion concernée). Ne jamais en garder une seule en silence.
- Si l'utilisateur a donné une hiérarchie entre les sources (par exemple « les maquettes l'emportent sur le brief »), il n'y a plus de contradiction à signaler : la story applique la version prioritaire et le dit explicitement dans la section 4 (« Alignement sur la maquette » ou équivalent). La divergence n'est plus reprise en section 7 : la story n'a pas à gérer la mise à jour des documents d'entrée. Ne pas appliquer une hiérarchie que l'utilisateur n'a pas donnée.
- **Ne pas sur-signaler.** Quand les sources fournies définissent un point (texte exact, emplacement, seuil, droit, comportement), il est écrit comme règle ferme, sans `[À CLARIFIER]` ni question. Ouvrir une question uniquement pour un point que les sources de la story laissent réellement indéfini et qui bloque un test : quand le brief est lacunaire, signaler tous ces trous, regroupés par thème ; quand les sources sont complètes, n'en signaler aucun ou, au plus, un cas limite réellement absent. Ne pas inventer de règle de confort (par exemple « le bouton Fermer ferme la fenêtre », « le message a un titre ») : ce qui va de soi n'est ni une règle ni une question.
- Une formulation ouverte ne vaut pas décision : « peut renseigner » ne dit pas que le champ est facultatif ou obligatoire, un brief qui ne parle pas de droit ne dit pas quel droit s'applique. Ces points restent `[À CLARIFIER]` tant qu'une source fournie ne les tranche pas ; ne pas les écrire comme règle ni comme déduction.
- Chaque règle de gestion porte sa source entre crochets en fin de ligne, par exemple `[Source : BRIEF-§2.1]` ou `[Source : MAQ-écran3]`. Si un registre de sources avec identifiants existe, utiliser ces identifiants ; sinon citer le nom du document et la section, le point ou l'écran.
- Les besoins utilisateur n'ont pas de rubrique propre : ils sont exprimés par les règles de gestion. Un besoin du périmètre qui n'apparaît dans aucune règle de gestion est donc un besoin non couvert.
- Une déduction n'est pas une source : si une règle est une conséquence logique de ce qui est écrit (par exemple « la colonne Actions n'est pas triable » déduit de « tri sur les quatre colonnes de données »), l'écrire, citer la source dont elle découle, et la lister dans la note de fin de réponse pour que l'utilisateur la valide. Toute déduction est listée, y compris celle qui sous-tend un critère (par exemple « sans date, pas d'alerte »). Si aucune, ne pas écrire « aucune déduction » sans avoir relu chaque RG et chaque critère.

## Démarche

1. **Cadrer la story demandée.** Identifier laquelle (titre, place dans l'initiative). Si le découpage vient du cadrage ou du user story mapping, le reprendre ; sinon, dire en une phrase le découpage retenu et pourquoi. La granularité (par fonctionnalité, par écran, par droit…) dépend du cas. Ce qui est laissé à une autre story va dans « Exclus ».
2. **Rassembler les sources.** Partir de ce qui existe : registre des sources, inventaire des besoins et liste des lacunes s'ils ont déjà été produits, sinon lire directement les documents. Ne pas reconstruire ce qui existe déjà.
   Le dossier `references/` de cette skill contient le contexte Core RH gestion documentaire (`03-contexte-corerh-documents.md`), le story mapping (`04-story-mapping.md`), les retours utilisateurs (`05-retours-utilisateurs.md`) et les règles de gestion avec leur statut (`06-regles-de-gestion.md`). Le lire dès que la story concerne la gestion documentaire Core RH, sans attendre que l'utilisateur le demande. Règles d'usage :
   - Statut **Définie** : règle ferme, citée par son identifiant (ex. `TAB-02`).
   - Statut **Hypothèse** : jamais une règle ferme. Si elle relève de la story, la poser avec `[À CLARIFIER]` et la mention « hypothèse » et la reprendre en section 7 ; si elle relève d'une autre story (ex. tri initial, pagination), ne la mentionner qu'en section 7, sans RG ni critère. Une décision ultérieure de l'utilisateur (compte rendu, DEC-n) la fait passer en règle ferme, avec la nouvelle source.
   - Statut **À arbitrer** : `[À CLARIFIER]` à l'endroit concerné.
   - Un retour utilisateur (RU-n) est un besoin, pas une règle. Les types de documents et sections de `03` sont des exemples fictifs.
   - **Périmètre des références.** Quand l'utilisateur fournit lui-même ses sources dans le message (brief, maquette, contexte), ce sont elles qui définissent la story : les références servent seulement à retrouver les identifiants, le contexte et le statut des règles que ces sources évoquent déjà. Elles ne permettent PAS d'ajouter une règle de gestion, un critère, une déduction ou une question sur un sujet que ces sources ne mentionnent pas (par exemple les versions, la pagination, les doublons de nom, le droit d'accès, les états de chargement, le tri). Quand l'utilisateur ne fournit aucune source (cas « rédige l'US n du mapping »), les références sont la source de la story.
   - Un point ouvert des références qui ne conditionne pas cette story n'est ni une question ni un point d'attention. Les références ne servent pas à chercher des trous supplémentaires. Les informations arrivent progressivement : à chaque nouveau document, mettre à jour les stories concernées et dire ce qui a changé.
3. **Repérer les trous et les contradictions avant d'écrire.** Pour chaque élément de la story, se demander si les sources le définissent assez pour être testé (voir les pistes ci-dessous) et si elles se contredisent. Si l'utilisateur est là et que les points ouverts sont nombreux ou bloquants, les lister en une fois, par ordre d'importance, en distinguant les manques (à clarifier) des contradictions (à arbitrer), et proposer soit de répondre point par point, soit de rédiger tout de suite avec les marqueurs. Si le brief est suffisant, rédiger directement.
4. **Rédiger** en suivant la trame ci-dessous, une règle de gestion par idée testable, chacune avec sa source.
5. **Contrôler** avec la liste de contrôle en fin de skill.
6. **Rendre** la story, puis une note courte pour l'utilisateur : les déductions à valider, les trous et contradictions majeurs, ce qui dépasse le périmètre. La livraison suit toujours le mode unique décrit ci-dessous.

En cas de contradiction entre deux sources, ne pas trancher en silence : appliquer la hiérarchie que l'utilisateur a donnée (par exemple les maquettes l'emportent sur le brief) et le dire dans la story ; à défaut, poser le marqueur `[CONTRADICTION]` avec les deux versions et leurs sources, et le reprendre en section 7.

### Mode de livraison (méthode unique)
Les user stories sont **toujours livrées directement dans la conversation**, en markdown, quel que soit leur nombre. Aucune exception :
- Ne jamais créer de fichier (.md, .docx, .pdf ou autre), ne jamais utiliser Write, SendUserFile, Artifact ni document pour livrer une story, et ne pas proposer de le faire, sauf si l'utilisateur le demande explicitement dans le message en cours.
- Plusieurs stories dans une même demande : les écrire toutes dans la réponse, l'une après l'autre, chacune avec sa trame complète en 7 sections, séparées par une ligne `---`.
- Mise à jour d'une story déjà rendue : réécrire la story complète et à jour dans la conversation (pas seulement le diff), puis dire en une phrase ce qui a changé.
- Le texte de la story doit rester utilisable tel quel (copier-coller) : pas de commentaire inséré à l'intérieur de la trame, les remarques vont dans la note finale.

### Pistes pour repérer les trous
Ce sont des questions à se poser, pas des règles à écrire : la réponse doit venir des sources.
- Tableau ou liste : contenu de chaque colonne, valeurs vides, tri (sens, ordre, départage), pagination, état vide, filtres.
- Formulaire ou saisie : champs obligatoires, formats, longueurs, valeurs par défaut, messages d'erreur, comportement à l'enregistrement et à l'annulation.
- Droits et profils : qui voit, qui modifie, droit unique ou séparé par action, comportement sans droit.
- États et cas limites : donnée absente, chargement, erreur, volume important.
- Libellés et messages : lesquels sont nouveaux (pour la section 5) et si leur formulation française exacte figure dans les sources.

## Titre de la story

Le titre est la seule référence de la story : le numéro de ticket sera généré plus tard, au moment de la création dans l'outil de gestion (Jira, Linear…). Une skill ultérieure reprendra le titre tel quel comme objet du ticket. Règles :
- **Aucun numéro dans le titre** : pas de « US 1 », « US [N°] » ni autre préfixe. Ne jamais en inventer un, ne jamais en demander un, et ne pas signaler son absence en section 7.
- Il nomme l'objet métier concerné par la story.
- Il tient sur une ligne, se comprend sans lire la story et distingue cette story des autres de la même initiative (il doit rester unique parmi elles).
- Il décrit ce que la story change dans le produit, pas le problème ni la solution technique.
- Une fois la story rendue, le titre reste stable : en cas de mise à jour, ne le changer que si le périmètre a changé, et le dire.

## Structure de la trame (à reproduire à l'identique)

La trame est figée : un lecteur (dev, QA, design) doit retrouver la même information au même endroit d'une story à l'autre. On ne renomme, ne supprime et ne réordonne donc jamais les sections.

```markdown
# [Titre]

## 1. Contexte et objectif
## 2. Comportement existant
## 3. Périmètre
## 4. Comportement attendu
## 5. Traductions
## 6. Critères d'acceptation
## 7. À clarifier / Points d'attention
```

Les sept sections sont toujours présentes. Si une section ne s'applique pas, on garde son titre et on écrit « Sans objet » avec la raison en quelques mots. Cela distingue « non applicable » de « oublié ».

### 1. Contexte et objectif
Pourquoi cette story existe : le contexte (module, initiative : MVP, V1…), le problème utilisateur ou métier et la valeur attendue. 2 à 5 lignes, sans décrire la solution : elle va en section 4.

### 2. Comportement existant
À compléter uniquement en cas d'évolution d'une fonctionnalité existante : décrire ce que fait le produit aujourd'hui, pour que l'écart avec la section 4 soit lisible. Si l'existant est un manque, le dire (« Le dossier salarié ne dispose actuellement d'aucun onglet dédié… »). Pour une nouvelle fonctionnalité sans existant : « Sans objet : nouvelle fonctionnalité ».

### 3. Périmètre
Trois rubriques, toujours dans cet ordre :
- **Profils et rôles concernés :** les profils.
- **Inclus (ce qu'on traite via cette user story) :** ce que la story couvre.
- **Exclus (ce qu'on ne traite pas via cette user story) :** ce qu'un lecteur pourrait raisonnablement croire inclus, avec un renvoi vers la story qui le traite si elle existe.

### 4. Comportement attendu
Deux rubriques, toujours dans cet ordre :
- **Description fonctionnelle :** le comportement du point de vue du produit (emplacement, états, enchaînements, messages), en prose courte ou en liste. Quand une hiérarchie de sources a tranché une divergence, l'indiquer ici (par exemple « Alignement sur la maquette : le brief indique X, la maquette indique Y ; les maquettes l'emportent sur le brief, la story suit donc la maquette »).
- **Règles de gestion :** numérotées `RG1`, `RG2`… pour que les critères d'acceptation puissent s'y référer. Une règle = une idée testable, formulée sans ambiguïté (valeurs, seuils, conditions explicites), qui exprime aussi le besoin utilisateur qu'elle sert. Chaque règle se termine par sa source. Une règle dont le contenu est contradictoire entre sources porte `[CONTRADICTION]` suivi des deux versions et de leurs sources.

### 5. Traductions
Cette section liste les **nouveaux libellés** que la story crée (nouveau bouton, onglet, colonne, champ, droit, message…) pour que l'utilisateur les traduise. Tableau :

```markdown
| Code RESX | FR | EN | DE | ES |
|---|---|---|---|---|
|  | [libellé en français] |  |  |  |
```

Règles :
- **Une ligne par nouveau libellé**, et seulement pour les libellés que la story crée : ne pas lister ceux qui existent déjà dans le produit. Si on ne sait pas si un libellé est nouveau ou existant, le lister et poser la question en section 7.
- **Colonne FR : renseignée** avec le libellé français **recopié tel qu'il est écrit dans les sources**, sans le reformuler ni l'améliorer. Si les sources ne donnent pas la formulation exacte (par exemple un message d'erreur dont le texte reste à définir, ou un champ que le brief décrit seulement comme concept), écrire uniquement `[À CLARIFIER]` dans la cellule FR : ne pas composer ni suggérer un libellé, même évident, et ne pas ajouter d'explication dans la cellule (elle va en section 7).
- **Colonnes Code RESX, EN, DE et ES : toujours vides.** L'utilisateur les renseigne lui-même. Ne jamais traduire, même quand la traduction paraît évidente, et ne jamais proposer de code RESX.
- Lister en section 7, sous « Point d'attention », que le code RESX et les traductions EN, DE et ES sont à renseigner, ainsi que chaque libellé FR resté `[À CLARIFIER]`.
- Si la story ne crée aucun libellé : « Sans objet : aucun nouveau libellé ».

### 6. Critères d'acceptation
Format : une **liste à puces plate**, sans numérotation ni sous-titres. Chaque bullet est une vérification à faire par un testeur et commence toujours par « Vérifier que… » (jamais « Vérifier le comportement… » : on écrit le résultat attendu ; pas de formulation Étant donné / lorsque / alors). Règles d'écriture :
- Un bullet = un comportement observable et vérifiable, sans interprétation. Le contexte (profil, droit, état de départ) est dit dans le bullet lui-même.
- Écrire côté résultat observable (« Vérifier que l'onglet « Documents » n'est pas affiché pour un gestionnaire ne disposant pas du droit »), pas en intention.
- Terminer chaque bullet par la ou les règles qu'il vérifie, ex. `(RG2)`. Toute règle de gestion doit être couverte par au moins un bullet ; tout bullet doit renvoyer à une règle ou à la description fonctionnelle.
- Ne pas introduire dans un bullet une règle absente de la section 4.
- Couvrir le cas nominal et le cas inverse (droit absent ou désactivé, donnée vide, profil non concerné) quand les sources permettent de les établir.
- Un bullet qui dépend d'un point ouvert porte le même marqueur que la règle dont il dépend (`[À CLARIFIER]` ou `[CONTRADICTION]`), avec le renvoi à la question de la section 7.
- Si la section 5 comporte des libellés, ajouter un bullet qui vérifie que les libellés affichés en français correspondent à ceux de la colonne FR de la section 5. Ne citer EN, DE et ES dans ce bullet que si l'utilisateur les a renseignées dans le tableau.

### 7. À clarifier / Points d'attention
Liste numérotée `Q1`, `Q2`… Chaque point commence par une étiquette de type :
- **Manque** (marqueur `[À CLARIFIER]`) : la question précise, où elle bloque (section ou RG concerné), la source qui est silencieuse ou ambiguë, et l'impact si elle reste sans réponse.
- **Contradiction** (marqueur `[CONTRADICTION]`) : les versions en présence, chacune avec sa source, la question « Laquelle de ces versions s'applique ? », où elle bloque (section ou RG concerné) et l'impact si elle reste sans arbitrage.

Les points non bloquants (dépendances envers d'autres stories, code RESX et traductions EN, DE, ES à renseigner en section 5, libellés FR à préciser, cohérence avec d'autres stories, document à corriger après application d'une hiérarchie de sources) vont aussi ici, sous la mention « Point d'attention ». Si rien à signaler : « Aucun point à clarifier identifié à ce stade. » Ne l'écrire qu'après avoir vérifié qu'aucune règle n'est restée sans source et qu'aucune contradiction n'a été tranchée en silence.

## Contrôle avant de rendre une story
- Le titre est un titre seul (une ligne, objet métier nommé), sans numéro ni préfixe, et les 7 sections sont présentes, dans l'ordre, avec les titres exacts.
- Chaque besoin du périmètre de la story apparaît dans au moins une RG, et chaque RG a une source et est couverte par un critère d'acceptation.
- Aucune information absente des sources n'est présentée comme un fait ; chaque manque porte `[À CLARIFIER]` à l'endroit où il gêne et figure en section 7 avec l'étiquette « Manque ».
- Chaque `[CONTRADICTION]` cite les deux versions avec leurs sources et figure en section 7 avec l'étiquette « Contradiction ». Aucune contradiction n'est tranchée sans hiérarchie donnée par l'utilisateur ; quand une hiérarchie a été appliquée, la section 4 le dit.
- Section 5 : une ligne par nouveau libellé, la colonne FR recopiée des sources (ou `[À CLARIFIER]`), les colonnes Code RESX, EN, DE et ES vides. Aucune traduction ni aucun code n'a été proposé.
- Les critères d'acceptation sont une liste plate de « Vérifier que… », vérifiables.
- La story est livrée dans la conversation, sans fichier créé (mode de livraison unique).

## Exemple (story réelle de l'utilisateur, adaptée à la trame ; les sources sont illustratives)

```markdown
# Ajouter l'onglet « Documents » au dossier salarié

## 1. Contexte et objectif
Dans le cadre de la gestion documentaire du module Core RH, ajouter un onglet « Documents » au dossier salarié afin de permettre aux gestionnaires habilités d'accéder à cet espace.

## 2. Comportement existant
Le dossier salarié ne dispose actuellement d'aucun onglet dédié à la gestion documentaire.

## 3. Périmètre
**Profils et rôles concernés :** Gestionnaires RH.
**Inclus (ce qu'on traite via cette user story) :** Création de l'onglet et du droit d'accès associé.
**Exclus (ce qu'on ne traite pas via cette user story) :** Affichage et gestion des documents (ajout, consultation, modification, suppression).

## 4. Comportement attendu
**Description fonctionnelle :**
Ajouter un onglet « Documents » immédiatement à droite de l'onglet « Dossier collaborateur ».

**Règles de gestion :**
- RG1 : Un nouveau droit « Accès aux documents du salarié » est créé dans Administration > Droits. [Source : BRIEF-§3]
- RG2 : L'onglet « Documents » est visible et accessible uniquement aux gestionnaires pour lesquels ce droit est activé : un gestionnaire RH habilité accède ainsi aux documents du salarié depuis son dossier. [Source : BRIEF-§3, MAQ-écran1]

## 5. Traductions
| Code RESX | FR | EN | DE | ES |
|---|---|---|---|---|
|  | Documents |  |  |  |
|  | Accès aux documents du salarié |  |  |  |

## 6. Critères d'acceptation
- Vérifier que le nouvel onglet « Documents » est positionné immédiatement à droite de l'onglet « Dossier collaborateur » dans le dossier salarié (description fonctionnelle).
- Vérifier que le droit « Accès aux documents du salarié » est disponible dans Administration > Droits (RG1).
- Vérifier que l'onglet « Documents » est visible et accessible pour un gestionnaire disposant du droit activé (RG2).
- Vérifier que l'onglet « Documents » n'est pas affiché pour un gestionnaire ne disposant pas du droit ou pour lequel celui-ci est désactivé (RG2).
- Vérifier que les libellés français de l'onglet et du droit d'accès correspondent à ceux de la colonne FR de la section 5 (RG1, RG2).

## 7. À clarifier / Points d'attention
- Point d'attention : code RESX et traductions EN, DE et ES à renseigner en section 5 pour les deux libellés.
```