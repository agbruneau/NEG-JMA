# PRD : Production des Recherches et des Séries pour tout le Nouveau Testament

**2026-06-14** · **AGB** · **EBC** · dépôt *Biblique* (Église Baptiste de Charlesbourg)

> Document d'exigences (PRD) fondé sur le dossier `48 - Galates/00 - Introduction` comme cas
> de référence et sur `59 - Jacques` comme livre entièrement réalisé (gabarit d'or). Il définit,
> de manière vérifiable et reproductible, comment produire **toutes les recherches** (skill
> `/sermon-JMA`) et **toutes les séries** (skill `/sermon-series`) couvrant **l'intégralité de
> chacun des 27 livres du Nouveau Testament**, semaine par semaine, en *lectio continua*.

---

## 1. Résumé exécutif

Le dépôt vise une ressource d'étude et de préparation de prédication couvrant tout le NT, livre
par livre, conforme à la théologie de John MacArthur (cadre fixé par `CLAUDE.md` et tranché par
`NEG - MacArthur.pdf`). Ce PRD transforme cet objectif en une **chaîne de production
standardisée et répétable** appliquée identiquement aux 27 livres.

Pour **chaque livre** du NT, le produit fini comprend :

1. **Une série de prédications** (`00 - Introduction/Serie.md` + `.pdf`), produite par
   `/sermon-series`, qui découpe le livre en péricodes consécutives semaine par semaine, **sans
   lacune ni chevauchement**, du premier au dernier verset.
2. **Une recherche globale du livre** (`00 - Introduction/Recherche.md` + `.pdf`), produite par
   `/sermon-JMA` sur l'étendue complète du livre, servant de rampe d'accès au dimanche
   d'introduction.
3. **Une recherche exégétique par péricope** (un dossier `NN - <titre> (Réf c.v-v)/` par semaine),
   chacune produite par `/sermon-JMA`, accompagnée de son `index.html` et de son `.pdf`.

L'état de référence (juin 2026) : Jacques est **complet** ; Galates, Luc et Actes ont leur
`00 - Introduction` amorcé ; les 27 livres ont déjà leurs fichiers de référence
`NEG - <Livre>.md` et `JMA - <Livre>.md`. Ce PRD pilote le reste jusqu'à l'achèvement du NT.

---

## 2. Contexte et motivation

- **Source de vérité doctrinale** : `NEG - MacArthur.pdf` (La Bible d'étude MacArthur complète,
  texte NEG, 2216 p.) **tranche toute conformité** et prime sur la mémoire et les sources
  générales. Repères de page par livre : voir `CLAUDE.md` (section « Gotchas »).
- **Cadre théologique non négociable** : lentille **MacArthur seul** (baptiste réformé,
  dispensationalisme prémillénariste prétribulationniste, cessationnisme strict, Lordship
  Salvation, justification forensique avec double imputation). Voir `CLAUDE.md` § « Cadre
  théologique » et la « Carte de conformité par corpus ».
- **Gabarit de référence** : `48 - Galates/00 - Introduction` (cas fondateur de ce PRD) et
  `59 - Jacques` (livre intégralement réalisé : 12 dossiers de péricodes + site de présentation).
- **Traduction** : NEG 1979. Originaux NA28 / BHS, translittérés avec glose. **Français canadien**
  correctement accentué. **Aucun tiret cadratin (—).**

---

## 3. Objectif vérifiable (définition du succès global)

> **Succès du programme** : pour les 27 livres du NT (`40 - Matthieu` à `66 - Apocalypse`), il
> existe une série complète conforme et, pour chaque semaine de chaque série, un dossier de
> péricope contenant les trois fichiers cohérents (`.md`, `.pdf`, `index.html`), la réunion des
> péricopes reconstituant l'intégralité du livre sans verset sauté ni chevauchement, le tout
> conforme au `NEG - MacArthur.pdf`.

Ce succès se mesure livre par livre par la **liste de contrôle d'acceptation** (§ 10). Aucun
livre n'est déclaré « fait » sans que sa liste soit cochée et **vérifiée par constat** (pas
d'affirmation sans preuve : voir `CLAUDE.md` global, principe 4).

---

## 4. Portée

### 4.1 Dans la portée

- Production des **séries** (1 par livre) via `/sermon-series`.
- Production des **recherches globales** (1 par livre) via `/sermon-JMA`.
- Production des **recherches de péricope** (1 par semaine) via `/sermon-JMA`.
- Production des **`index.html`** de chaque péricope et du `00 - Introduction` (gabarit visuel
  Jacques), et **régénération des `.pdf`** après toute édition.
- Création et nommage des **dossiers de péricodes** dérivés de la série.
- **Contrôle de conformité** doctrinale et éditoriale (§ 9, § 10, § 11).

### 4.2 Hors de la portée

- Rédaction de plans de prédication, d'esquisses ou de sermons (les skills `/sermon-JMA` et
  `/sermon-series` sont **recherche et planification seulement**, jamais rédaction de sermon).
- Régénération des fichiers de référence `NEG - <Livre>.md` / `JMA - <Livre>.md` (déjà extraits
  pour les 27 livres via `extract_nt.py` ; hors de ce PRD sauf correction ponctuelle).
- Toute version biblique autre que NEG 1979 ; tout commentaire hors corpus MacArthur / Master's
  Seminary.

---

## 5. Acteurs, outils et dépendances

| Élément | Rôle | Notes |
|---|---|---|
| `/sermon-series` | Produit la série (portée, 3 titres, table semaine par semaine, arc, notes) | Sortie JSON → `generate-pdf.py` → `.pdf` + `.md` jumeau |
| `/sermon-JMA` | Produit la recherche (7 sections, lentille MacArthur unique) | Sortie JSON → `generate-pdf.py` → `.pdf` + `.md` jumeau |
| `oia-reformee` | Grille de référence doctrinale (analyse O.I.A.) | Appui de contrôle, non producteur du livrable |
| `pastor-foundation` | Variables d'Église et de voix | Pasteur = **Simon Ouellette** ; Église = **Église Baptiste de Charlesbourg (EBC)** |
| `generate-pdf.py` | Rend le `.pdf` + le `.md` jumeau depuis le JSON | Fourni par le skill `sermon-JMA`, **non versionné** ; exige `reportlab` (`pip install reportlab`) |
| `NEG - MacArthur.pdf` | **Arbitre de conformité** (AT + NT) | Extraire par livre avec PyMuPDF, `PYTHONUTF8=1` (voir `CLAUDE.md`) |
| `NEG - <Livre>.md` | Texte NEG du livre | Source du texte des péricopes ; un seul livre par fichier |
| `JMA - <Livre>.md` | Notes d'étude MacArthur du livre | Source doctrinale de premier recours |
| `59 - Jacques` | Gabarit d'or (structure + visuel `index.html`) | Référence visuelle : `59 - Jacques/00 - Introduction/index.html` |

**Contraintes d'environnement** (rappel `CLAUDE.md`) :

- `rm` / `Remove-Item` **refusés** : supprimer via `python -c "import os; os.remove(r'...')"`.
- Renommer / déplacer : préférer `git mv`.
- `generate-pdf.py` écrit dans le **répertoire courant** : exécuter la génération **depuis le
  dossier cible** (ou déplacer ensuite les fichiers), pour que le `.md`/`.pdf` atterrissent au bon
  endroit.
- `sermon-series` peut laisser un artefact transitoire `serie-de-predications-temp.json` à la
  racine (à supprimer après génération).

---

## 6. Pipeline de production par livre

Quatre phases ordonnées. La phase 0 est déjà accomplie pour les 27 livres. Les phases 1 → 3 sont
le cœur de ce PRD. Le flux est **séquentiel par livre** (la série gouverne le découpage des
péricodes), mais **parallélisable entre péricodes** une fois la série figée.

```
Phase 0  Fichiers de référence du livre        [FAIT pour les 27 livres]
           NEG - <Livre>.md  +  JMA - <Livre>.md
              │
Phase 1  Dossier 00 - Introduction
           1a. Série            /sermon-series  →  Serie.md + Serie.pdf
           1b. Recherche globale /sermon-JMA    →  Recherche.md + Recherche.pdf
           1c. index.html + LogoEBC.avif        (gabarit Jacques)
              │  (la table semaine par semaine de la série gouverne la suite)
Phase 2  Création des dossiers de péricodes
           NN - <titre> (Réf c.v-v)/   un par ligne de la table de série
              │
Phase 3  Par péricope (parallélisable)
           3a. Recherche        /sermon-JMA  →  Recherche-MacArthur-<Livre>-<réf>.md + .pdf
           3b. index.html       (gabarit Jacques, fidèle au .md)
           3c. Régénération .pdf après toute édition du .md ou du .html
```

**Règle d'ordre** : la **phase 1a (série) précède toujours** les phases 2 et 3, car le nombre et
les bornes des péricodes (donc les noms de dossiers et les références de recherche) **découlent de
la table de série**. Ne jamais créer un dossier de péricope ni lancer une recherche de péricope
avant que la série du livre soit figée et conforme.

---

## 7. Spécification détaillée des livrables

### 7.1 Série de prédications (`/sermon-series`)

- **Entrée (prompt)** : nom du livre + « exposition suivie complète, *lectio continua*, couvrir
  l'intégralité du livre, suggérer la longueur d'après les péricodes naturelles » + cadre
  MacArthur + cohérence avec `Recherche.md` du livre. Gabarit de prompt : § 16.A.
- **Exigences de contenu** (impératives, d'après `CLAUDE.md` et le skill) :
  - Couverture **intégrale et sans lacune** : du premier au dernier verset, chaque semaine = **une
    péricope consécutive**, la réunion reconstitue le livre entier ; **aucun verset sauté, aucun
    chevauchement, aucune semaine hors de l'ordre du texte**.
  - Le **nombre de semaines découle des unités de sens** du livre (longueur, structure, densité
    doctrinale), **jamais d'un chiffre arbitraire**. Rythme d'exposition : **5 à 10 versets**
    bien traités par dimanche ; ralentir sur les paragraphes à charge doctrinale.
  - Chaque ligne : **titre thématique**, **référence (`c.v-v`)**, **idée maîtresse** (une
    affirmation, pas un sujet), **fil conducteur**.
  - Sections : Évaluation de la portée ; 3 propositions de titre ; table semaine par semaine ;
    arc narratif ; notes pratiques (vérification de la durée, semaines à traiter avec soin,
    recommandation de lancement).
- **Sortie** : `00 - Introduction/Serie.md` + `Serie.pdf` (via JSON → `generate-pdf.py`).
  **Nom canonique : `Serie.md` / `Serie.pdf`** (voir § 8.5).
- **Conformité** : idées maîtresses et arc doctrinal alignés sur MacArthur ; **valider les points
  sensibles** (foi/œuvres, justification, parousie, millénium, Israël/Église, dons, baptême,
  persévérance) contre `NEG - MacArthur.pdf`. En cas d'écart, **le PDF tranche**.

### 7.2 Recherche globale du livre (`/sermon-JMA`)

- **Entrée** : passage = **étendue complète du livre** (ex. « Galates 1.1 à 6.18 ») + topic =
  thèse du livre + questions de fond + contexte de série. Gabarit de prompt : § 16.B.
- **Sortie** : `00 - Introduction/Recherche.md` + `Recherche.pdf`.
- **Usage** : socle du **dimanche d'introduction** et fondement de cohérence pour la série
  (la série doit être **cohérente avec `Recherche.md`**).

### 7.3 Recherche exégétique de péricope (`/sermon-JMA`)

- **Entrée** : passage = la référence exacte de la semaine (`<Livre> c.v-v`) + topic = titre
  thématique de la semaine + idée maîtresse + questions. Gabarit de prompt : § 16.C.
- **Sept sections obligatoires** (skill `sermon-JMA`) :
  1. Contexte du passage
  2. Arrière-plan historique et culturel
  3. Étude des mots-clés (tableau : translittération, sens littéral, champ sémantique,
     traductions comparées **S21 / NEG79 / Darby / LSG / KJF**)
  4. Apports des commentateurs (**prose MacArthur**, citations exactes ou paraphrase, jamais
     d'invention)
  5. Renvois et passages parallèles (type : Parallèle direct / Lien thématique / Arrière-plan AT)
  6. Thèmes théologiques (« Dans le texte » + « Pour votre assemblée »)
  7. Pistes de réflexion (5 à 7 questions)
- **Sortie** : dans le dossier de péricope,
  `Recherche-MacArthur-<Livre>-<réf>.md` + `.pdf`.

### 7.4 `index.html` (péricope et `00 - Introduction`)

- Page web autonome **réutilisant le système visuel de
  `59 - Jacques/00 - Introduction/index.html`** : palette noir et orange, polices serif, hero /
  nav / sections / footer, animations « reveal », logo en relatif vers le `LogoEBC.avif` du
  dossier `00 - Introduction/` du livre.
- **Hero** : titre thématique (= titre de la prédication) + sur-titre « Recherche · <Livre> c.v-v ».
- **Contenu fidèle au `.md`**, transposé dans les composants : tableau `.mots`, renvois `.renvoi`
  (pastille de type), thèmes `.theme` à deux volets, questions numérotées `.questions`.
- **Footer** : EBC + pasteur Simon Ouellette + crédit AGB + mention NEG.
- **Liens** : chemins relatifs depuis le dossier de péricope vers le `00 - Introduction/` du même
  livre (logo, retour « vue d'ensemble ») ; **encodage URL** des espaces et accents (`%20`, etc.).

---

## 8. Conventions de nommage

### 8.1 Dossiers de livre
`NN - <Livre>` avec `NN` de **40 (Matthieu) à 66 (Apocalypse)** (ordre canonique des 66 livres).

### 8.2 Dossier d'introduction
`NN - <Livre>/00 - Introduction/` contient : `Recherche.md` + `.pdf`, `Serie.md` + `.pdf`,
`index.html`, `LogoEBC.avif`.

### 8.3 Dossiers de péricope
`NN - <titre de la prédication> (Réf c.v-v)/` où `NN` = numéro de semaine de la série
(`01`, `02`, …, aligné sur la table de série). Exemple :
`05 - La foi qui agit (Jacques 2.14-26)`.

### 8.4 Fichiers de recherche de péricope
`Recherche-MacArthur-<Livre>-<réf>.md` / `.pdf`, où `<réf>` = chapitre et versets en tirets,
**sans point** (ex. `2.14-26` → `2-14-26`). Exemple :
`Recherche-MacArthur-Jacques-2-14-26.md`.

### 8.5 Nom canonique de la série
Le nom canonique unique est **`Serie.md` / `Serie.pdf`**. Les quatre livres amorcés le
respectent déjà (Jacques, Galates, Luc, Actes), la dette de nommage héritée (conventions
`Série - Actes` et `Serie-de-Predications-Luc-…` mentionnées dans `CLAUDE.md`) ayant **déjà été
résorbée** dans le dépôt. Tout nouveau livre adopte directement `Serie.md` / `Serie.pdf`. En cas
de renommage résiduel, utiliser `git mv`.

> Note : la section « Nommage du plan de série en transition » de `CLAUDE.md` est **périmée** sur
> ce point ; les fichiers du dépôt font foi.

### 8.6 Signature (byline)
`date · AGB · EBC` (standard `CLAUDE.md`). Variables de foundation : pasteur = Simon Ouellette,
Église = Église Baptiste de Charlesbourg.

---

## 9. Règles de conformité doctrinale

1. **Le PDF tranche.** Avant de déclarer un livrable conforme, **confronter ses affirmations
   doctrinales aux notes de `NEG - MacArthur.pdf`** pour la péricope et le livre visés, en
   priorité sur les points sensibles. En cas d'écart, **le PDF prévaut** sur la mémoire et les
   sources générales.
2. **Lentille MacArthur unique.** Aucune alternative (amillénariste, Free Grace, NPP, etc.), même
   minoritaire. Ne nommer une position adverse que pour la **réfuter**, jamais comme « une option
   parmi d'autres ».
3. **Loci systématiques** (valables pour les 27 livres) : bibliologie, christologie, sotériologie,
   ecclésiologie, pneumatologie (cessationnisme strict), eschatologie (dispensationalisme
   prémillénariste prétribulationniste), herméneutique grammatico-historique. Détail : `CLAUDE.md`.
4. **Carte de conformité par corpus.** Tenir les points saillants et réfuter les dérives propres à
   chaque corpus (Évangiles, Actes, pauliniennes majeures, pauliniennes captivité/pastorales/
   Thessaloniciens, épîtres générales, Apocalypse). Détail et *flashpoints* : `CLAUDE.md`.
5. **Sources** : corpus MacArthur (MacArthur Study Bible / NT Commentary, gty.org, *Biblical
   Doctrine*) et cercle Master's Seminary. **Ne jamais inventer de citation** ni de référence
   non vérifiable ; paraphraser les positions documentées.
6. **Isolation des fichiers de référence** : `NEG - <Livre>.md` et `JMA - <Livre>.md` ne
   contiennent **que** le livre de leur dossier, **fondés exclusivement** sur `NEG - MacArthur.pdf`.

---

## 10. Critères d'acceptation (Definition of Done)

### 10.1 Par série (`Serie.md/.pdf`)
- [ ] Couverture **intégrale** du livre, premier au dernier verset, **sans lacune ni chevauchement**.
- [ ] Une semaine = une péricope **consécutive**, dans l'ordre du texte.
- [ ] Nombre de semaines justifié par les **unités de sens** (pas un chiffre arbitraire) ; rythme
      5 à 10 versets/semaine.
- [ ] Chaque ligne porte titre + référence `c.v-v` + idée maîtresse + fil conducteur.
- [ ] 5 sections présentes (portée, 3 titres, table, arc, notes pratiques).
- [ ] Idées maîtresses et arc **conformes MacArthur** et **vérifiés contre le PDF** sur les points
      sensibles du corpus.
- [ ] `Serie.md` **et** `Serie.pdf` présents et jumeaux (nom canonique `Serie`).

### 10.2 Par recherche globale (`Recherche.md/.pdf`)
- [ ] Couvre l'**étendue complète** du livre.
- [ ] 7 sections du gabarit `sermon-JMA` présentes et substantielles.
- [ ] **Cohérente avec la série** (thèse, arc, verset directeur).
- [ ] `.md` **et** `.pdf` présents et jumeaux.

### 10.3 Par péricope (un dossier par semaine)
- [ ] Dossier nommé `NN - <titre> (Réf c.v-v)` aligné sur la table de série.
- [ ] `Recherche-MacArthur-<Livre>-<réf>.md` : 7 sections présentes ; tableau de mots avec les
      5 traductions ; prose MacArthur ; renvois typés ; thèmes à deux volets ; 5 à 7 pistes.
- [ ] `.pdf` jumeau régénéré, à jour du `.md`.
- [ ] `index.html` présent, fidèle au `.md`, gabarit visuel Jacques, liens relatifs encodés,
      footer conforme.
- [ ] **Parité doctrinale `.md` ↔ `.html`** sur la prose doctrinale.
- [ ] Conformité doctrinale **vérifiée contre le PDF** pour la péricope.

### 10.4 Par livre (achèvement)
- [ ] Phase 0 ✓ (fichiers de référence).
- [ ] Phase 1 ✓ (série + recherche globale + `index.html` du 00 + logo).
- [ ] Phase 2 ✓ (tous les dossiers de péricodes créés, 1 par semaine).
- [ ] Phase 3 ✓ (chaque péricope a ses 3 fichiers cohérents).
- [ ] **Recomposition vérifiée** : la concaténation des références de péricodes couvre le livre
      sans trou (contrôle explicite verset par verset des bornes).

### 10.5 Programme (NT complet)
- [ ] Les 27 livres satisfont 10.4.

---

## 11. Contrôle qualité éditorial

- **Aucun tiret cadratin (—)** : virgule, deux-points ou point à la place.
- **Français canadien correctement accentué.** Après une génération par sous-agent, **vérifier la
  densité d'accents** : environ **25 à 33 caractères accentués par Ko** pour une prose dense ; un
  ratio **inférieur à 15** signale des accents manquants à régénérer.
- **Corrections chirurgicales** : ne toucher que ce qu'exige la tâche ; conserver style, densité
  académique, structure, grec translittéré, références.
- **Parité `.md` ↔ `.html`** : toute correction de prose doctrinale s'applique aux **deux**
  fichiers (le `.html` porte `&nbsp;` et `<i>…</i>`). Les écarts **structurels** sont voulus
  (le `.html` transpose en puces / intertitres / chapeau) ; ne pas forcer une parité littérale.
- **Régénérer le `.pdf`** après toute modification du `.md` ou de l'`.html`.
- Citations bibliques **NEG 1979** ; grec/hébreu translittérés avec glose ; substrats NA28 / BHS.

**Commande de contrôle de densité d'accents** (exemple, à exécuter sur un fichier généré) :

```bash
python -c "import sys,io; t=io.open(sys.argv[1],encoding='utf-8').read(); a=sum(c in 'àâäçéèêëîïôöùûüÀÂÄÇÉÈÊËÎÏÔÖÙÛÜ' for c in t); print(f'{a} accents / {len(t)/1024:.1f} Ko = {a/(len(t)/1024):.1f} par Ko')" "chemin/vers/fichier.md"
```

---

## 12. Orchestration et mise à l'échelle

### 12.1 Ordre de production recommandé
1. **Achever Galates** (série déjà produite) : phase 2 + phase 3 sur les 23 péricodes, plus
   `index.html` + logo du `00 - Introduction`. Sert de **seconde validation du pipeline** après
   Jacques.
2. **Compléter Luc et Actes** : série et recherche globale déjà présentes (nom canonique
   `Serie.md`) ; vérifier leur conformité, puis phases 2 et 3.
3. **Épîtres d'une seule saison** (rendement rapide, faible risque) :
   Philémon, 2-3 Jean, Jude, Tite, 2 Thessaloniciens, Colossiens, Philippiens, 1-2 Thess,
   1-2 Timothée, 1-2 Pierre, 1 Jean, Éphésiens.
4. **Pauliniennes majeures et Hébreux** : Romains, 1-2 Corinthiens, Hébreux (denses ; rythme lent).
5. **Évangiles et Apocalypse** (arcs pluriannuels) : Matthieu, Marc, Jean, Apocalypse
   (Luc traité en 2).

Justification : commencer par un livre dont la série existe (Galates) valide la chaîne aval ;
enchaîner les petits livres maximise le nombre de livres « faits » tôt ; garder les grands arcs
pour la fin une fois le pipeline parfaitement rodé.

### 12.2 Mise à l'échelle par workflow (`ultracode`)
Le travail dépasse une seule passe : c'est un cas type de **workflow dynamique** (`CLAUDE.md`
global, point 6). Modèle d'orchestration recommandé **par livre**, une fois la série figée :

- **Étape 1 (barrière)** : produire/valider la **série** du livre (gouverne tout l'aval).
- **Étape 2 (pipeline parallèle)** : pour chaque ligne de la table de série, en parallèle :
  `créer le dossier` → `/sermon-JMA` (recherche) → `générer .pdf` → `index.html`.
  Isolation `worktree` si plusieurs livres sont produits simultanément et que des fichiers sont
  écrits en parallèle.
- **Étape 3 (vérification adverse)** : pour chaque péricope, un agent **réfutateur** confronte la
  prose au `NEG - MacArthur.pdf` et au gabarit (densité d'accents, em-dash, 7 sections, parité
  `.md`/`.html`). Ne déclarer « fait » qu'après accord de la vérification.
- **Règle de convergence** : reprise possible (progression jalonnée) ; une exécution interrompue
  reprend au lieu de repartir de zéro.

**Confirmation requise avant lancement** (`CLAUDE.md` global) : énoncer le plan et le seuil de
vérification, puis confirmer. Ne pas déclencher de workflow pour ce qu'une seule passe règle.

### 12.3 Suivi de l'avancement
Tenir l'inventaire (§ 13) à jour à chaque livre achevé ; cocher les listes du § 10. La preuve
prime sur l'affirmation : aucun livre « fait » sans constat vérifié de la recomposition complète.

---

## 13. Inventaire des 27 livres du Nouveau Testament

**Légende état** : Réf = fichiers `NEG`/`JMA` présents ; Glob = recherche globale `00 - Introduction`
présente ; Sér = série présente ; Péri = dossiers de péricodes présents.
**Régime** : `1 saison` (un seul arc) ou `arc pluriannuel` (à scinder en sous-séries).
**Sem. (est.)** : estimation **indicative** de semaines (le compte réel **découle des péricodes
naturelles**, fixé par `/sermon-series`, jamais d'avance).

| # | Livre | Ch / V | Régime | Sem. (est.) | État actuel | Prochaine action |
|---|---|---|---|---|---|---|
| 40 | Matthieu | 28 / 1071 | arc pluriannuel | 120-150 | Réf ✓ | Phase 1 (série, scinder en sous-séries) |
| 41 | Marc | 16 / 678 | arc pluriannuel | 80-100 | Réf ✓ | Phase 1 |
| 42 | Luc | 24 / 1151 | arc pluriannuel | 130-160 | Réf ✓ · Glob ✓ · Sér ✓ | Phases 2-3 |
| 43 | Jean | 21 / 879 | arc pluriannuel | 100-130 | Réf ✓ | Phase 1 |
| 44 | Actes | 28 / 1007 | arc pluriannuel | 110-140 | Réf ✓ · Glob ✓ · Sér ✓ | Phases 2-3 |
| 45 | Romains | 16 / 433 | arc pluriannuel | 60-80 | Réf ✓ | Phase 1 |
| 46 | 1 Corinthiens | 16 / 437 | arc pluriannuel | 55-70 | Réf ✓ | Phase 1 |
| 47 | 2 Corinthiens | 13 / 257 | 1 saison longue | 40-50 | Réf ✓ | Phase 1 |
| 48 | Galates | 6 / 149 | 1 saison | **23 (figé)** | Réf ✓ · Glob ✓ · Sér ✓ | **Phases 2-3** (créer 23 dossiers + recherches + index.html ; logo du 00) |
| 49 | Éphésiens | 6 / 155 | 1 saison | 24-30 | Réf ✓ | Phase 1 |
| 50 | Philippiens | 4 / 104 | 1 saison | 16-20 | Réf ✓ | Phase 1 |
| 51 | Colossiens | 4 / 95 | 1 saison | 14-18 | Réf ✓ | Phase 1 |
| 52 | 1 Thessaloniciens | 5 / 89 | 1 saison | 12-16 | Réf ✓ | Phase 1 |
| 53 | 2 Thessaloniciens | 3 / 47 | 1 saison | 8-10 | Réf ✓ | Phase 1 |
| 54 | 1 Timothée | 6 / 113 | 1 saison | 16-22 | Réf ✓ | Phase 1 |
| 55 | 2 Timothée | 4 / 83 | 1 saison | 12-16 | Réf ✓ | Phase 1 |
| 56 | Tite | 3 / 46 | 1 saison | 7-9 | Réf ✓ | Phase 1 |
| 57 | Philémon | 1 / 25 | 1 saison courte | 3-4 | Réf ✓ | Phase 1 |
| 58 | Hébreux | 13 / 303 | arc pluriannuel | 45-60 | Réf ✓ | Phase 1 |
| 59 | Jacques | 5 / 108 | 1 saison | **12 (réalisé)** | **COMPLET** (gabarit d'or) | Aucune (référence) |
| 60 | 1 Pierre | 5 / 105 | 1 saison | 16-20 | Réf ✓ | Phase 1 |
| 61 | 2 Pierre | 3 / 61 | 1 saison | 10-12 | Réf ✓ | Phase 1 |
| 62 | 1 Jean | 5 / 105 | 1 saison | 16-20 | Réf ✓ | Phase 1 |
| 63 | 2 Jean | 1 / 13 | 1 saison courte | 2-3 | Réf ✓ | Phase 1 |
| 64 | 3 Jean | 1 / 14 | 1 saison courte | 2-3 | Réf ✓ | Phase 1 |
| 65 | Jude | 1 / 25 | 1 saison courte | 4-5 | Réf ✓ | Phase 1 |
| 66 | Apocalypse | 22 / 404 | arc pluriannuel | 50-70 | Réf ✓ | Phase 1 |

> Les comptes de versets sont indicatifs (NEG). Les estimations de semaines servent au
> séquencement, **non à contraindre** le découpage : `/sermon-series` fixe le compte réel d'après
> les unités de sens du texte.

---

## 14. Jalons recommandés

| Jalon | Contenu | Critère de sortie |
|---|---|---|
| J1 | Achèvement de **Galates** (phases 2-3) | 23 péricodes complètes + recomposition vérifiée |
| J2 | **Luc** et **Actes** complétés + noms de série uniformisés | 2 livres conformes au § 10.4 |
| J3 | **Épîtres d'une saison** (12 livres, § 12.1 pt 3) | 12 livres conformes |
| J4 | **Pauliniennes majeures + Hébreux** | Romains, 1-2 Co, Hébreux conformes |
| J5 | **Évangiles + Apocalypse** (arcs pluriannuels) | Matthieu, Marc, Jean, Apocalypse conformes |
| J6 | **Clôture NT** | Les 27 livres satisfont le § 10.5 |

---

## 15. Risques et mitigations

| Risque | Impact | Mitigation |
|---|---|---|
| Dérive doctrinale d'un sous-agent (hors lentille MacArthur) | Contenu non conforme | Étape de **vérification adverse** contre le PDF (§ 12.2) ; le PDF tranche |
| Accents manquants après génération par sous-agent | Français dégradé | **Contrôle de densité d'accents** systématique (§ 11) ; régénérer si < 15/Ko |
| Tirets cadratins introduits | Violation de règle | Recherche `—` avant validation ; remplacement |
| Lacune ou chevauchement de péricodes | Couverture incomplète | **Contrôle de recomposition** verset par verset (§ 10.4) |
| `.pdf` désynchronisé du `.md`/`.html` | Incohérence des livrables | **Régénérer le `.pdf`** après toute édition (§ 11) |
| `generate-pdf.py` écrit au mauvais endroit | Fichiers égarés | Exécuter **depuis le dossier cible** ou déplacer (`git mv`) (§ 5) |
| `reportlab` absent | Échec de génération | `pip install reportlab` en préalable |
| Réintroduction d'un nom de série non canonique sur un nouveau livre | Incohérence | Adopter directement `Serie.md` / `Serie.pdf` (§ 8.5) |
| Sous-estimation des grands livres | Planning irréaliste | Régime `arc pluriannuel` + scission en sous-séries (§ 13) |

---

## 16. Annexes : gabarits de prompt

> Remplacer `<Livre>`, `<étendue>`, `<réf>`, `<titre>`, `<idée>` par les valeurs du livre / de la
> semaine. Exécuter la génération **depuis le dossier cible**.

### 16.A : Série (`/sermon-series`)
```
/sermon-series
Livre : <Livre> (NT, dépôt Biblique, EBC). Exposition suivie complète, lectio continua.
Couvre l'INTÉGRALITÉ du livre, du premier au dernier verset, sans lacune ni chevauchement ;
une semaine = une péricope consécutive. Suggère la longueur d'après les péricodes naturelles
(5 à 10 versets/semaine ; ralentir sur les paragraphes doctrinaux denses). Cadre théologique :
John MacArthur seul (dispensationalisme prémillénariste prétribulationniste, cessationnisme,
Lordship Salvation). Cohérence exigée avec 00 - Introduction/Recherche.md. Sortie au nom
canonique Serie.md / Serie.pdf. Pasteur Simon Ouellette, Église Baptiste de Charlesbourg.
```

### 16.B : Recherche globale (`/sermon-JMA`)
```
/sermon-JMA
Passage : <Livre> <étendue complète, ex. 1.1 à 6.18>.
Topic : thèse et argument d'ensemble du livre, pour le dimanche d'introduction de la série.
Questions : enjeux doctrinaux majeurs du livre et flashpoints du corpus (voir CLAUDE.md).
Lentille MacArthur unique. Sortie : 00 - Introduction/Recherche.md + Recherche.pdf.
```

### 16.C : Recherche de péricope (`/sermon-JMA`)
```
/sermon-JMA
Passage : <Livre> <réf, ex. 2.14-26>.
Topic : <titre thématique de la semaine>. Idée maîtresse : <idée>.
Série : exposition suivie de <Livre>, semaine <NN>.
Questions : <points interprétatifs / tensions de la péricope>.
Lentille MacArthur unique ; valider contre NEG - MacArthur.pdf. Sortie dans le dossier
NN - <titre> (Réf c.v-v)/ : Recherche-MacArthur-<Livre>-<réf>.md + .pdf, puis index.html.
```

---

## 17. Références

- `CLAUDE.md` (racine) : cadre théologique, structure, règles d'édition, gotchas, table des pages
  du PDF par livre.
- `NEG - MacArthur.pdf` : **arbitre de conformité** (AT + NT).
- `59 - Jacques/` : livre entièrement réalisé (gabarit de structure et `index.html`).
- `48 - Galates/00 - Introduction/` : cas de référence de ce PRD (série 23 semaines + recherche
  globale).
- Skills : `/sermon-series`, `/sermon-JMA`, `oia-reformee`, `pastor-foundation`.

*Soli Deo Gloria.*
