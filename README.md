# Jacques — « La foi qui agit »

> Ressource d'étude biblique et de préparation de prédication sur l'épître de Jacques,
> préparée pour l'**Église Baptiste de Charlesbourg** (Québec).

Ce dépôt rassemble l'ensemble du matériel produit pour une exposition suivie
(*lectio continua*) de l'épître de Jacques : une page web de présentation destinée
à l'assemblée, des recherches exégétiques détaillées passage par passage, un plan
de série de prédication, et les introductions de référence qui ont servi de socle.

Une seule conviction traverse tout le projet, comme tout le livre de Jacques :
**la foi authentique se prouve par ses fruits.**

---

## Cadre théologique

Le contenu est élaboré dans un cadre **baptiste réformé / MacArthurien** :

- herméneutique grammatico-historique et exposition suivie du texte ;
- *sola fide* tenue avec Jacques 2 (« la foi seule sauve, mais la foi qui sauve n'est jamais seule ») ;
- souveraineté de Dieu, régénération monergique, persévérance des saints, *Lordship salvation* ;
- lecture cessationniste de Jacques 5.14-15 (soin pastoral ordinaire, non guérison charismatique
  ni extrême-onction) ;
- eschatologie dispensationaliste et prémillénariste à la manière de John MacArthur,
  l'alternative covenantale / amillénariste de la Confession de 1689 étant signalée honnêtement
  là où le texte le demande.

Sources doctrinales de référence : John MacArthur, Jean Calvin, la Confession de foi
baptiste de 1689 (1689 LBCF).

---

## Le site web

[`index.html`](index.html) est une page web autonome (HTML + CSS + JavaScript, sans dépendance
de build) qui présente l'épître à l'assemblée :

- page-titre, introduction, une section par chapitre (1 à 5) et conclusion ;
- versets clés en exergue, points de repère structurés, fil conducteur « la foi qui agit » ;
- mise en page pensée pour une lecture confortable (grands caractères, fortes capitales,
  thème sombre à accents ambrés, polices *Cormorant Garamond* / *EB Garamond*) ;
- barre de progression de lecture et révélation au défilement.

Citations bibliques : **Nouvelle Édition de Genève 1979 (NEG)**. Le logo
[`LogoEBC.avif`](LogoEBC.avif) est référencé par la page.

**Pour la consulter :** ouvrir `index.html` dans un navigateur (les polices proviennent de
Google Fonts ; une connexion Internet améliore le rendu, mais la page reste lisible hors ligne).

---

## Recherche exégétique et série de prédication

Chaque péricope dispose d'une **recherche exégétique** (`.md` source + `.pdf` rendu) et
correspond à une **semaine de prédication** de la série « La foi qui agit ». Les douze unités
suivent le découpage naturel de l'épître :

| Sem. | Passage | Recherche exégétique | Titre de la prédication |
|---|---|---|---|
| 1 | Jacques 1.1-12 | `Recherche-Exegetique-Jacques-1-1-12` | La joie au creuset de l'épreuve |
| 2 | Jacques 1.13-18 | `Recherche-Exegetique-Jacques-1-13-18` | Le Dieu qui ne change pas |
| 3 | Jacques 1.19-27 | `Recherche-Exegetique-Jacques-1-19-27` | Auditeurs ou praticiens |
| 4 | Jacques 2.1-13 | `Recherche-Exegetique-Jacques-2-1-13` | La foi sans partialité |
| 5 | Jacques 2.14-26 | `Recherche-Exegetique-Jacques-2-14-26` | La foi qui agit *(sommet doctrinal)* |
| 6 | Jacques 3.1-12 | `Recherche-Exegetique-Jacques-3-1-12` | Le petit membre, le grand feu |
| 7 | Jacques 3.13-18 | `Recherche-Exegetique-Jacques-3-13-18` | Deux sagesses |
| 8 | Jacques 4.1-10 | `Recherche-Exegetique-Jacques-4-1-10` | L'amitié du monde |
| 9 | Jacques 4.11-17 | `Recherche-Exegetique-Jacques-4-11-17` | Si le Seigneur le veut |
| 10 | Jacques 5.1-6 | `Recherche-Exegetique-Jacques-5-1-6` | Le cri des moissonneurs |
| 11 | Jacques 5.7-12 | `Recherche-Exegetique-Jacques-5-7-12` | Patience jusqu'à son retour |
| 12 | Jacques 5.13-20 | `Recherche-Exegetique-Jacques-5-13-20` | La prière qui agit |

Le plan détaillé de la série (idées maîtresses, arc narratif, notes pastorales) se trouve dans
[`<Série Global.md>`](<Série Global.md>), et une recherche couvrant l'épître d'un seul tenant
(Jacques 1.1 à 5.20) dans [`<Recherche Global.md>`](<Recherche Global.md>) — utile pour la
prédication d'introduction.

### Gabarit d'une recherche exégétique

Chaque document de recherche suit la même structure :

1. **Contexte du passage** — place de la péricope dans l'argument de l'épître ;
2. **Arrière-plan historique et culturel** — ce qui échappe au lecteur moderne ;
3. **Étude des mots-clés** — tableau (translittération, sens, champ sémantique, traductions
   comparées : S21, NEG79, Darby, LSG, KJF) ;
4. **Apports des commentateurs** — MacArthur, Calvin, 1689 LBCF ;
5. **Renvois et passages parallèles** ;
6. **Thèmes théologiques** — « Dans le texte » + « Pour votre assemblée » ;
7. **Pistes de réflexion** pour le prédicateur.

---

## Introductions de référence

Trois introductions issues d'ouvrages de référence, fournissant auteur, date, destinataires,
canonicité, style et plans de l'épître :

| Fichier | Source |
|---|---|
| [`Intro - MacArthur.md`](<Intro - MacArthur.md>) | *La Sainte Bible avec commentaires de John MacArthur* (Société Biblique de Genève, 2006) |
| [`Intro - Chercheur biblique.md`](<Intro - Chercheur biblique.md>) | J. Ronald Blue, *Commentaire biblique du chercheur, Nouveau Testament* (Publications Chrétiennes, 2013) |
| [`Intro - NBS.md`](<Intro - NBS.md>) | Notes d'étude de la *Nouvelle Bible Segond* (Société Biblique Française) |

---

## Structure du dépôt

```
.
├── index.html                              Site de présentation de l'épître (page unique)
├── LogoEBC.avif                            Logo de l'Église Baptiste de Charlesbourg
│
├── Intro - MacArthur.md                    Introductions de référence
├── Intro - Chercheur biblique.md
├── Intro - NBS.md
│
├── Recherche Global.md / .pdf              Recherche exégétique sur Jacques 1.1 à 5.20
├── Série Global.md / .pdf                  Plan de la série de prédication (12 semaines)
│
└── Recherche-Exegetique-Jacques-*.md / .pdf   12 recherches, une par péricope
```

Pour chaque recherche, le `.md` est la source rédigée et le `.pdf` en est l'export mis en page.
Le fichier `ruvector.db` (base de l'outillage local) est exclu du dépôt via
[`.gitignore`](.gitignore).

---

## Crédits

- **Église Baptiste de Charlesbourg** — Charlesbourg, Québec ; pasteur Simon Ouellette.
- Recherches et série signées **AGB · EBC**.
- Traduction de référence : Nouvelle Édition de Genève 1979 (NEG) ; textes originaux NA28 / BHS.

*Soli Deo Gloria.*
