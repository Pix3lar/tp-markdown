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

## Tests
Lancez pytest depuis la racine du projet et avec l'environnement virtuel activé. Le résultat attendu est 40 passed, ce qui veux dire que tous les tests réussissent.

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

## Licence

## Contact
