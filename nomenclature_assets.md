# Nomenclature des Assets — NEW ISLAND

## 1. La règle (à ne jamais casser)

```
NomPersonnage_etat.extension
```

- **NomPersonnage** : en PascalCase, **sans accent, sans espace, sans tiret**.
  → `Elisa`, pas `Élisa` / `elisa` / `Eliza`.
- **etat** : en minuscules, un seul mot descriptif de la pose/émotion (snake_case si plusieurs mots).
  → `inquiete`, `swimming`, `standard`, `nuit_rouge`.
- **Extension** :
  - `.png` pour tous les sprites de personnages (fond transparent obligatoire, alpha 24-bits).
  - `.jpg` pour tous les fonds d'écran (pas de transparence nécessaire, compression acceptable).

## 2. Pourquoi c'est strict (piège classique à éviter)

Ton code JS insère les noms de fichiers **tels quels** dans le DOM (`uiSprite.src = scene.char`). Sur ton PC (Windows/Mac), le système de fichiers **ignore la casse** : `elisa_tendre.png` et `Elisa_Tendre.png` s'affichent pareil en local, donc l'erreur ne se voit pas en testant chez toi.

**Mais dès que tu déploieras en ligne** (la grande majorité des hébergeurs web tournent sous Linux), le système de fichiers **respecte la casse** : `Elisa_tendre.png` ≠ `elisa_tendre.png` ≠ `Elisa_Tendre.png`. Une seule lettre mal casée = image cassée en prod alors que ça marchait "chez toi". D'où l'intérêt de figer la nomenclature maintenant, une fois pour toutes.

## 3. Checklist — fichiers EXACTS déjà attendus par le code actuel

Ce sont les noms extraits directement de ton `index.html`. Coche au fur et à mesure que tu exportes le rendu Sims 4 correspondant.

### Sprites (PNG, alpha, ancrage `bottom: 0`)

| Fichier attendu (exact) | Personnage | Contexte narratif (pour choisir la pose) |
|---|---|---|
| `Isabella_standard.png` | Isabella | S1 — jeu de la carte à Cannes, posture séductrice standard |
| `Isabella_soiree.png` | Isabella | S3 — soirée mousse, ambiance festive/provocante |
| `Isabella_argile.png` | Isabella | S4 — date 24h, rituel sensoriel, posture douce/intime |
| `Elisa_inquiete.png` | Élisa | S1 — premier doute, expression inquiète/jalouse |
| `Elisa_swimming.png` | Élisa | S2 — baignade complice, tenue maillot |
| `Elisa_angry.png` | Élisa | S2 — après la trahison de Simon, colère contenue |
| `Elisa_tendre.png` | Élisa | S3 — elle console le joueur, posture tendre/protectrice |
| `Elisa_ange.png` | Élisa | S4 — alarme à minuit, expression grave/déterminée |
| `Animatrice.png` | L'Animatrice | S1 et S5 — présentatrice/narratrice, posture neutre |
| `Ex_triste.png` | Ton Ex | S5 — confrontation finale, expression triste/remords |

### Fonds d'écran (JPG, `background-size: cover`)

| Fichier attendu (exact) | Utilisation |
|---|---|
| `fond_nuit_lagoon.jpg` | S1 (ouverture) et fin `fin_solo` |
| `fond_feu_camp.jpg` | Tous les feux de camp (S1, S2, S3-trahison, S5) + fin `fin_couple` |
| `fond_plage_jour.jpg` | S2 (arrivée/plage) + fin `fin_solo` (variante) |
| `fond_soiree_mousse.jpg` | S3 (soirée Tequila) |
| `fond_lac_secret.jpg` | S4 (date Isabella) + fin `fin_isabella` |
| `fond_villa_nuit_rouge.jpg` | S4 (alarme à minuit) |

**Total : 10 PNG + 6 JPG = 16 fichiers** pour que la version actuelle du jeu soit 100% illustrée.

## 4. Anticiper la suite (personnages du casting complet pas encore codés)

Ta roadmap liste 21 personnages, mais le code actuel n'en scripte que 4 (Isabella, Élisa, l'Animatrice, Ton Ex). Si/quand on enrichit le scénario avec Nathan, Jeremiah, Simon, Lana, Louis, Anita, etc., garde le même schéma :

```
Nathan_standard.png
Nathan_soiree.png
Jeremiah_depart.png
Simon_trahison.png
Lana_jacuzzi.png
Anita_douce.png
Louis_digne.png
```

Pas besoin de tout produire maintenant — juste garder cette convention prête pour ne pas repartir sur un système différent en cours de route.

## 5. Suggestion pour la suite immédiate

Vu que tu pars de renders Sims 4, une astuce : exporte toujours en gardant le **nom de travail Sims 4 dans un fichier séparé** (ex. un tableau perso), et renomme uniquement la copie finale détourée selon cette nomenclature — ça évite de mélanger tes fichiers de travail bruts avec les livrables finaux du jeu.
