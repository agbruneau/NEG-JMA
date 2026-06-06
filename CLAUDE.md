# CLAUDE.md — dépôt `Jacques`

Ressource d'étude biblique et de préparation de prédication sur l'épître de **Jacques**,
pour l'**Église Baptiste de Charlesbourg** (Québec ; pasteur Simon Ouellette). Le matériel
soutient une exposition suivie (*lectio continua*) en **12 semaines** : la série
« **La foi qui agit** » (la foi authentique se prouve par ses fruits). `README.md` donne la
vue d'ensemble destinée au public ; ce fichier ne couvre que ce qui n'est pas dérivable du dépôt.

## Cadre théologique — non négociable

Tout le contenu doit être **conforme à la théologie de John MacArthur** (Master's Seminary),
cadre baptiste réformé. Les recherches sont produites avec le skill **`sermon-JMA`** (lentille
MacArthur **unique**) ; le skill `oia-reformee` sert de grille de référence doctrinale.

- **Sotériologie** : monergisme (TULIP), *sola fide* + double imputation, persévérance des
  saints, **Lordship Salvation** (foi et repentance indissociables ; pas de croyant
  non-disciple). Aucun glissement *easy-believism* / Free Grace / régénération décisionnelle.
- **Jacques 2.14-26** (sommet doctrinal) : « la foi seule sauve, mais la foi qui sauve n'est
  jamais seule ». Tenir Paul et Jacques par les **deux sens de *dikaioō*** (forensique chez
  Paul, démonstratif/vindicatif chez Jacques). Les œuvres **démontrent** la foi ; **jamais** de
  justification *par* les œuvres (réfuter NPP, sacramentalisme) ni d'antinomisme.
- **Cessationnisme strict** : Jacques 5.14-15 (au sein de la péricope 5.13-20, semaine 12) =
  relèvement du croyant *spirituellement* faible
  et épuisé (*astheneō* / *kamnō*) ; l'onction = soin pastoral ordinaire (*aleiphō*, huile, non
  *chriō* rituel), **ni** guérison charismatique **ni** extrême-onction sacramentelle.
- **Eschatologie** : dispensationalisme prémillénariste prétribulationniste ; distinction
  Israël/Église ; promesses faites à Israël **non** spiritualisées ; retour du Seigneur futur,
  littéral et imminent (Jacques 5.7-9).
  - *Nuance de posture.* Les recherches générées via `sermon-JMA` adoptent une **lentille
    MacArthur unique, sans contrepoids** (aucune alternative amillénariste, même minoritaire).
    Le `README.md` et l'ancienne ligne « trancher pour MacArthur » mentionnaient encore la
    lecture covenantale/amillénariste de la 1689 comme « témoin minoritaire » subordonné. En
    cas de divergence, **trancher pour MacArthur**.
- **Ne jamais inventer de citation de MacArthur** ni de référence non vérifiable. Paraphraser
  ses positions documentées (MacArthur NT Commentary, *La Bible d'étude MacArthur*, gty.org,
  *Biblical Doctrine* de MacArthur et Mayhue).

## Structure du dépôt

```
README.md
CLAUDE.md
Recherches/
  NN - Titre de la prédication (Jacques c.v-v)/     12 dossiers, un par semaine de prédication
    Recherche-MacArthur-Jacques-<réf>.md             source rédigée (prose continue)
    Recherche-MacArthur-Jacques-<réf>.pdf            export paginé, imprimable
    index.html                                       rendu web (gabarit visuel)
Syntheses-Globales/
  index.html              site de présentation de l'épître (gabarit visuel de référence)
  LogoEBC.avif            logo de l'Église Baptiste de Charlesbourg
  Série Global.md / .pdf  plan de la série (12 semaines : titres, idées maîtresses, arc, notes)
  Recherche Global.md / .pdf   recherche couvrant Jacques 1.1 à 5.20 (prédication d'introduction)
  Intro - *.md            introductions de référence (MacArthur, Chercheur biblique, NBS)
```

- Dossiers nommés `NN - <titre de la prédication> (Jacques c.v-v)` (ex.
  `05 - La foi qui agit (Jacques 2.14-26)`), `NN` = semaine 1 à 12 du plan de `Série Global.md`.
- `<réf>` = chapitre et versets en tirets (ex. `2-14-26`), sans point.

## Produire ou réviser une recherche

Chaque dossier garde **trois fichiers cohérents** : `.md` (source) → `.pdf` (export) +
`index.html` (rendu web).

1. **`.md` + `.pdf`** : produits par le skill **`sermon-JMA`**. Sept sections : Contexte du
   passage · Arrière-plan historique et culturel · Étude des mots-clés (tableau :
   translittération, sens littéral, champ sémantique, traductions comparées S21 / NEG79 /
   Darby / LSG / KJF) · Apports des commentateurs (**prose MacArthur**) · Renvois et passages
   parallèles · Thèmes théologiques (« Dans le texte » + « Pour votre assemblée ») · Pistes de
   réflexion. Le skill écrit un JSON puis lance `generate-pdf.py` (reportlab) qui rend le `.pdf`
   et le `.md` jumeau. Byline du dépôt : `date · AGB · EBC`.
2. **`index.html`** : page web autonome qui **réutilise tel quel le système visuel de
   `Syntheses-Globales/index.html`** (palette noir + orange, polices serif, hero / nav /
   sections / footer, animations « reveal », logo en relatif `../../Syntheses-Globales/LogoEBC.avif`).
   Hero à **titre thématique** (= titre de la prédication) + sur-titre « Recherche · Jacques
   c.v-v ». Le contenu est **fidèle au `.md`**, transposé dans les composants : tableau
   `.mots`, renvois `.renvoi` (avec pastille de type), thèmes `.theme` à deux volets, questions
   numérotées `.questions`. Footer : EBC + pasteur Simon Ouellette + crédit AGB + mention NEG.

## Règles d'édition

- **Corrections chirurgicales** : ne toucher que ce qu'exige la demande ; conserver le style,
  la densité académique, la structure, le grec translittéré, les références.
- **Parité doctrinale `.md` ↔ `.html`** : toute correction de prose doctrinale s'applique aux
  **deux** fichiers (le `.html` porte des entités `&nbsp;` et des balises `<i>…</i>`). Les
  écarts **structurels** sont voulus (le `.html` transpose la prose en puces, intertitres,
  chapeau `.lead` + corps) ; ne pas forcer une parité littérale qui casserait le gabarit.
- Après toute modification du `.md` ou de l'`.html`, **régénérer le `.pdf`** correspondant.
- Citations bibliques : **NEG 1979**. Grec/hébreu translittéré + glose ; substrats NA28 / BHS.
- **Aucun tiret cadratin (—)**. Français canadien **correctement accentué** (après une
  génération par sous-agent, vérifier la densité d'accents : ~25-33 caractères accentués par Ko
  pour une prose dense ; un ratio < 15 signale des accents manquants à régénérer).

## Gotchas d'environnement

- `rm` / `Remove-Item` sont **refusés par les permissions** : supprimer un fichier via
  `python -c "import os; os.remove(r'...')"`.
- `generate-pdf.py` (fourni par le skill `sermon-JMA`, **non versionné dans ce dépôt**) exige
  `reportlab` (`pip install reportlab`).
- `.gitignore` exclut `ruvector.db` (outillage local), les copies Windows `* - Copie*` et `.claude/`.

## Crédits

Église Baptiste de Charlesbourg (Charlesbourg, Québec) ; pasteur Simon Ouellette. Recherches et
série signées **AGB · EBC**. Traduction de référence : Nouvelle Édition de Genève 1979 (NEG) ;
textes originaux NA28 / BHS. *Soli Deo Gloria.*
