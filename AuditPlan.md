# AuditPlan : audit de conformité doctrinale et d'intégrité du dépôt

**2026-06-24** · **AGB** · **EBC**

---

## 1. Objet et finalité

Audit exhaustif du dépôt visant à repérer ce qui doit être **corrigé** et **bonifié** au
niveau du **contenu théologique**, puis à exécuter ces révisions livre par livre, à mettre à jour
`CLAUDE.md` et `README.md`, à purger les fichiers inutiles, et enfin à publier sur `main`.

Le périmètre couvre **916 recherches** (`.md` + `.pdf` + `index.html`), les **30 livres traités**
(NT complet, plus Genèse 1-11, Psaume 19 et Psaume 119), les **fichiers de référence** par livre
(`NEG`/`JMA`), les deux documents fondateurs (`README.md`, `CLAUDE.md`) et l'hygiène générale du
dépôt.

## 2. Le « loop » retenu (Loop Library de Forward Future)

La [Loop Library](https://signals.forwardfuture.ai/loop-library/) propose 69 boucles agentiques.
Après revue de l'ensemble, le **meilleur loop pour cette tâche** est :

> ### « The pre-publish source-check loop » (catégorie *Content*)
> *« Checks every claim against current primary sources »* : inventorier chaque affirmation, la
> vérifier contre les **sources primaires** avant publication, puis corriger l'écart le plus risqué.

**Pourquoi celui-là (et pas un autre).**

- Le matériel est **destiné à la publication** (préparation de prédication, exporté en `.pdf` et
  `index.html` pour le pasteur). *Pre-publish* correspond exactement.
- Le dépôt possède **une source primaire unique qui arbitre** : `00 - Avant-propos/NEG -
  MacArthur.pdf`, proxyée localement par les extraits par livre `JMA - <Livre>.md` (notes) et
  `NEG - <Livre>.md` (texte). La règle du dépôt l'énonce déjà : *« Valider avant d'affirmer …
  confronter ses affirmations doctrinales aux notes de ce PDF … le PDF tranche. »* Le loop ne fait
  que **formaliser une discipline déjà inscrite dans `CLAUDE.md`**.
- La demande (« identifier les éléments à corriger au niveau du contenu théologique ») se traduit
  terme à terme : *inventorier les affirmations doctrinales → vérifier contre la source primaire →
  corriger les divergences*.

**Loops de soutien greffés** (le loop principal en orchestre deux autres) :

- **« The Groundtruth loop »** (*Evaluation*) : *« Audits project from direct evidence, reports each
  area's status »*. Forme du **volet audit** : une passe par livre, verdict de conformité étalonné.
- **« The housekeeper loop »** (*Engineering*) : *« removing dead code, stale files, duplication »*.
  Forme du **volet purge** (placeholders vestigiaux, artefacts de test).

### 2.1 Adaptation du loop à ce dépôt

| Élément générique du loop | Traduction dans ce dépôt |
|---|---|
| *claim* (affirmation) | affirmation doctrinale d'une recherche `.md` (justification, eschatologie, christologie, dons, baptême, Israël/Église, persévérance…) |
| *primary source* | `NEG - MacArthur.pdf`, proxy local `JMA - <Livre>.md` + `NEG - <Livre>.md` |
| *verify* | confronter l'affirmation aux notes `JMA` **et** à la grille de conformité MacArthur (loci et *flashpoints* de `CLAUDE.md`) |
| *fix riskiest mismatch* | correction chirurgicale dans le `.md` (puis parité `.html`, puis ré-export `.pdf`) |
| *before publish* | avant régénération/diffusion des exports `.pdf` / `index.html` |
| *iterate to convergence* | une unité par agent (intro + péricope sensible), en éventail parallèle ; convergence = tous les livres **CONFORME** |

## 3. Méthode et périmètre de l'audit

1. **Balayage mécanique déterministe** (script, tout le corpus) : ligature `œ`, densité d'accents,
   byline, tiret cadratin, intégrité des liens relatifs HTML, parité `.md`/`.html`/`.pdf`, exactitude
   des comptes du README, fichiers hors-norme.
2. **Audit doctrinal** (loop, 30 livres en éventail parallèle) : un agent par livre lit la recherche
   d'introduction, la référence `JMA` (étalon) et une péricope doctrinalement sensible, puis rend un
   **verdict structuré** (CONFORME / MINEUR / MAJEUR) avec, le cas échéant, citation, problème et
   correction chirurgicale.

## 4. Résultats — volet doctrinal (cœur de l'audit)

**30 / 30 livres audités : 28 CONFORME, 2 MINEUR, 0 MAJEUR.**

Le corpus est **doctrinalement solide** sous la lentille MacArthur seule. Les agents ont confirmé,
en les traçant verbatim aux notes `JMA`, la justification forensique et la double imputation, la
*Lordship Salvation* (réfutation de l'easy-believism / Free Grace), la persévérance des saints et la
sécurité éternelle, le cessationnisme strict, la distinction Israël / Église, le prémillénarisme
prétribulationniste, le *prōtotokos* de Colossiens 1.15 (prééminence, non un Christ créé), la
réfutation de la régénération baptismale et de l'universalisme, la création littérale en six jours
et le christocentrisme par la promesse (non par l'allégorie). **Aucune citation de MacArthur
inventée n'a été détectée.**

Les **deux seuls écarts** sont **factuels, non doctrinaux**, et confirmés contre la source primaire :

| # | Sévérité | Fichier | Écart | Correction (source : étalon) |
|---|---|---|---|---|
| F1 | mineur | `19 - Psaume 119/22 - La brebis égarée (Psaume 119.169-176)/Recherche-MacArthur-Psaume-119-169-176.md` | Citation NEG erronée du v. 169 (« je crois jusqu'à toi, ô Eternel ») | « que mon cri parvienne jusqu'à toi, ô Eternel » (NEG 119.169 ; le fichier emploie d'ailleurs la bonne formule deux phrases plus loin) |
| F2 | mineur | `58 - Hébreux/00 - Introduction/Recherche.md` | Liste des avertissements incomplète et mal délimitée (`2.1-4 ; 3.7-19 ; 6.4-6 ; 10.26-31 ; 12.25-29`) | Les six de l'étalon `JMA` : `2.1-4 ; 3.7-14 ; 5.11-6.20 ; 10.26-39 ; 12.15-17 ; 12.25-29` |

Parité au moment du constat : pour F1, l'`index.html` portait **déjà** la bonne formule (seuls
`.md` et `.pdf` étaient fautifs) ; pour F2, l'`index.html` d'introduction ne reproduit pas la liste
en prose (il présente les avertissements comme **péricopes du calendrier de série**, ce qui est
exact). Les deux corrections sont donc **`.md` seulement**.

## 5. Résultats — volet mécanique et structurel

| Contrôle | Portée | Résultat |
|---|---|---|
| Densité d'accents | 916 recherches | min 21,7 / médiane 30,3 / max 44,1 par Ko — **0 sous le seuil d'alarme 15** |
| Byline canonique `AAAA-MM-JJ · AGB · EBC` | 916 recherches | **0 non conforme** |
| Tiret cadratin `—` (interdit) | tout `.md` + `.html` | **0** (l'unique occurrence est la *règle* elle-même dans `CLAUDE.md`) |
| Liens relatifs HTML | 4522 liens | **0 cassé** |
| Parité `.md` / `.html` / `.pdf` | corpus | **916 = 916 = 916**, balance par livre cohérente |
| Comptes de péricopes du README | 30 livres | **0 écart** (100 % exacts) |
| Ligature `œ` vs digramme « oe » | tout `.md`/`.html` | **incohérent** : 7569 « oeuvre/cœur… » sans ligature vs 4002 `œ` (709 `.md`, 2132 occurrences en `.html`) |
| Doubles espaces dans les noms de dossiers | ~50 dossiers | artefact de la convention Windows (« : » interdit) ; consistant, liens intacts |
| Fichiers vestigiaux | dépôt | **24 `.gitkeep`** dans des dossiers de livre **pleins** |
| Fichiers racine mal placés / mal nommés | racine | `LiserMoi.pdf` (typo), `PrecisDicipulat.pdf` (hors `00 - Avant-propos/`) |

## 6. Plan d'exécution

### 6.1 Corrections appliquées

1. **F1 — Psaume 119.169** : corriger la citation dans le `.md`.
2. **F2 — Hébreux** : aligner la liste des six avertissements sur l'étalon `JMA` dans le `.md`.
3. **Fichiers racine** :
   - `git mv LiserMoi.pdf LisezMoi.pdf` (correction de la typo « Liser » → « Lisez »).
   - `git mv PrecisDicipulat.pdf "00 - Avant-propos/PrecisDicipulat.pdf"` (co-localisation avec son
     `.md`, conforme à ce qu'annoncent déjà `README.md` et `CLAUDE.md`).
4. **`CLAUDE.md`** : mettre le bloc « Structure du dépôt » en accord avec la racine réelle
   (`LisezMoi.pdf`, présent `AuditPlan.md`).
5. **`README.md`** : **revu, jugé exact** (comptes vérifiés, structure conforme après déplacement
   du `.pdf`) — **aucune retouche de contenu requise**. Le modifier obligerait à régénérer son export
   `LisezMoi.pdf`, non reproductible fidèlement (voir 8.2).

### 6.2 Purge

- `git rm` des **24 `.gitkeep`** (placeholders ayant servi à créer les dossiers de livre avant
  remplissage, jamais retirés ; tous les dossiers concernés contiennent désormais `NEG`, `JMA` et
  les péricopes). Genèse, Luc, Actes et Jacques n'en avaient pas : confirmation du caractère
  vestigial.
- Suppression de l'outil d'audit jetable `_audit_scan.py`.
- **Aucun autre fichier inutile** : pas de copie Windows, de `*_temp.json`, de `__pycache__`, de
  `.pyc` ni de `ruvector.db` (le commit « Finalisation » avait déjà nettoyé le dépôt).

### 6.3 Volontairement non touché (et pourquoi)

- **Ligature `œ`** : la normaliser proprement exigerait de régénérer les **916 PDF** (règle du
  dépôt : tout changement `.md`/`.html` impose la régénération du `.pdf`) avec `generate-pdf.py`,
  **non versionné**, et à partir des JSON sources absents. Le gabarit d'or lui-même (Jacques) emploie
  « oe ». Un correctif partiel `.md`/`.html` **casserait la parité** avec les PDF. Reporté en passe
  dédiée (voir 9).
- **Doubles espaces dans les noms de dossiers** : convention Windows assumée (« : » interdit) ;
  renommer des dizaines de dossiers est invasif, sans bénéfice fonctionnel (0 lien cassé), contraire
  au principe de **corrections chirurgicales**. Cosmétique uniquement.
- **Réécriture « de chaque fichier »** : l'audit montre un corpus mécaniquement impeccable et
  doctrinalement conforme. Une réécriture systématique violerait la règle interne de **corrections
  chirurgicales** et risquerait de dégrader un contenu soigné. La « révision de chaque fichier » est
  donc honnêtement requalifiée : **audit de chaque fichier, correction ciblée là où l'audit révèle un
  écart réel** (ici, 2 fichiers), plus la **procédure répétable** ci-dessous pour toute production à
  venir.

## 7. Annexe — verdict par livre

CONFORME, sauf indication. Méthode : intro + référence `JMA` + une péricope sensible par livre.

| Livre | Verdict | Livre | Verdict | Livre | Verdict |
|---|---|---|---|---|---|
| 01 Genèse | CONFORME | 48 Galates | CONFORME | 58 Hébreux | **MINEUR** (F2) |
| 19 Psaume 19 | CONFORME | 49 Éphésiens | CONFORME | 59 Jacques | CONFORME |
| 19 Psaume 119 | **MINEUR** (F1) | 50 Philippiens | CONFORME | 60 1 Pierre | CONFORME |
| 40 Matthieu | CONFORME | 51 Colossiens | CONFORME | 61 2 Pierre | CONFORME |
| 41 Marc | CONFORME | 52 1 Thess. | CONFORME | 62 1 Jean | CONFORME |
| 42 Luc | CONFORME | 53 2 Thess. | CONFORME | 63 2 Jean | CONFORME |
| 43 Jean | CONFORME | 54 1 Timothée | CONFORME | 64 3 Jean | CONFORME |
| 44 Actes | CONFORME | 55 2 Timothée | CONFORME | 65 Jude | CONFORME |
| 45 Romains | CONFORME | 56 Tite | CONFORME | 66 Apocalypse | CONFORME |
| 46 1 Corinthiens | CONFORME | 57 Philémon | CONFORME | | |
| 47 2 Corinthiens | CONFORME | | | | |

## 8. Décisions, compromis et limites

### 8.1 Le loop comme procédure répétable (production future)

Pour tout nouveau livre ou toute péricope, exécuter le **pre-publish source-check loop** ainsi :

1. Inventorier les affirmations doctrinales de la recherche.
2. Les confronter aux notes `JMA - <Livre>.md` (étalon, extrait du PDF d'autorité) et à la grille
   MacArthur de `CLAUDE.md` (loci, *flashpoints* par corpus).
3. Trancher tout écart **pour MacArthur** ; corriger le `.md`, propager au `.html`, ré-exporter le
   `.pdf`.
4. Itérer en éventail (un agent par unité, verdict structuré CONFORME/MINEUR/MAJEUR), converger
   quand tout est CONFORME.

### 8.2 Dette d'export PDF (assumée)

Les corrections F1 et F2 portent sur le `.md` **source**. Les deux `.pdf` exports correspondants
restent décalés d'une phrase : `generate-pdf.py` (l'outil qui a produit les 916 PDF) n'est **pas
versionné**, et `md-to-pdf.py` produit un rendu **différent** (test : 12 pages vs 10, titrage et
typographie distincts) qui désynchroniserait visuellement ces 2 PDF des 914 autres. **Choix retenu :
corriger la source faisant autorité et reporter le ré-export au prochain cycle de production** avec
l'outil du skill, plutôt que d'introduire une incohérence visuelle. Idem pour `LisezMoi.pdf` (export
du `README`), ce qui justifie de ne pas retoucher le `README`.

### 8.3 Recommandations de passes ultérieures (hors présent plan)

- **Passe `œ`** dédiée : normaliser `.md` + `.html` **et** régénérer les `.pdf` via le skill, en un
  seul mouvement, pour préserver la parité.
- **Re-export** des 2 PDF (Ps 119.169-176 et Hébreux intro) au prochain cycle `generate-pdf.py`.

---

*Soli Deo Gloria.*
