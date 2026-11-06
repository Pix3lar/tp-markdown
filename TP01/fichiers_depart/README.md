# pluvio

> Les données de ce projet sont entièrement fictives : elles ne proviennent
> d'aucune station de mesure.

## Description

`pluvio` est un petit outil Python en ligne de commande. Il lit un fichier
CSV de relevés de pluie de communes de Martinique et calcule des
statistiques : nombre de relevés, total, moyenne, maximum, total par commune.
Il s'adresse à toute personne qui découvre le projet et veut obtenir ces
statistiques depuis un terminal, sans écrire de code.

## Prérequis

- Python 3.10 ou plus récent
- Git, pour cloner le dépôt
- pytest 7 ou plus récent, installé avec les dépendances (voir Installation)

## Installation

Clonez le dépôt, placez-vous à la racine du projet, créez un environnement
virtuel dans le dossier `.venv`, activez-le, puis installez les dépendances.

Sous Linux et macOS (bash) :

```bash
git clone https://github.com/Pix3lar/tp-markdown.git
cd tp-markdown/TP01/fichiers_depart
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Sous Windows (PowerShell) :

```powershell
git clone https://github.com/Pix3lar/tp-markdown.git
cd tp-markdown\TP01\fichiers_depart
py -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Utilisation

Lancez les commandes depuis la racine du projet, environnement virtuel
activé. L'outil prend en argument le chemin d'un fichier CSV dont les
colonnes sont `date`, `commune` et `pluie_mm` ; les lignes qui commencent
par `#` sont ignorées. Le schéma suivant montre le trajet des données :

![Flux de pluvio : CSV, stats.py, cli.py, terminal](docs/schema_flux.svg)

Total de pluie de chaque commune :

```bash
python -m pluvio.cli data/pluies_fictives.csv --par-commune
```

```text
Commune           Total (mm)
Fort-de-France         115.6
La Trinité             171.4
Le Lamentin            170.4
Le Robert              203.3
Sainte-Anne            190.8
Schœlcher              225.0
```

Statistiques d'une seule commune (nom entre guillemets, car il contient une
espace) :

```bash
python -m pluvio.cli data/pluies_fictives.csv --commune "Le Robert"
```

```text
Relevés : 15
Total : 203.3 mm
Moyenne : 13.6 mm
Maximum : 34.6 mm (2025-01-02)
```

Statistiques d'une commune pour un mois donné :

```bash
python -m pluvio.cli data/pluies_fictives.csv --commune "Le Robert" --mois 2025-01
```

```text
Relevés : 10
Total : 140.4 mm
Moyenne : 14.0 mm
Maximum : 34.6 mm (2025-01-02)
```

Options de la commande (liste complète : `python -m pluvio.cli --help`) :

| Option | Argument | Rôle | Exemple |
|---|---|---|---|
| `--commune` | texte | ne garder que cette commune | `--commune "Le Robert"` |
| `--mois` | AAAA-MM | ne garder que ce mois | `--mois 2025-01` |
| `--par-commune` | aucun | afficher le total de chaque commune | `--par-commune` |

La commande renvoie le code 0 en cas de succès, 1 si aucun relevé ne
correspond aux critères et 2 si le fichier ne peut pas être lu.

## Tests
Racine : lancez pytest avec l'environnement virtuel activé (40 passed).

## Arborescence
.
├── LICENSE
├── README.md                 # le fichier actuel
├── data/
│   └── pluies_fictives.csv   # relevés de pluie fictifs
├── docs/
│   ├── revue_modele.md       # modèle de revue de README
│   └── schema_flux.svg       # schéma du flux de données
├── exercices/
│   ├── ex1_erreurs.md
│   ├── ex2_rendu.md
│   └── ex2_rendu_cible.png
├── grille_qualite_readme.md
├── pluvio/
│   ├── __init__.py
│   ├── cli.py                # interface en ligne de commande
│   └── stats.py              # lecture du CSV et calculs
├── pytest.ini                # configuration de pytest
├── rendre_zip.py             # création archive de rendu
├── requirements.txt          # dépendances (pytest)
├── tests/
│   ├── test_cli.py
│   ├── test_readme.py
│   ├── test_stats.py
│   └── test_verifier_readme.py
└── verifier_readme.py        # contrôle automatique d'un README

## Contribution
Mettez ```main``` à jour avec ```git switch main``` puis ```git pull```.
Créez une branche de travail avec ```git switch -c NOM_DE_BRANCHE```.
Faites des commits courts, au format ```type: résumé```.
Vérifiez que ```pytest``` réussit avant de pousser.
Poussez avec ```git push -u origin NOM_DE_BRANCHE```, puis ouvrez une PR.

## Licence
Ce projet est distribué sous licence MIT. Voir le fichier [LICENSE].

## Contact
Pour une question/un bug ouvrez une issue sur le dépôt GitHub : ```https://github.com/Pix3lar/tp-markdown/issues```.