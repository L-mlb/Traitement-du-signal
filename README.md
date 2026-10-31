# Traitement du signal audio et transmission numérique

## Présentation du projet

Ce projet explore le traitement d'un signal audio associé à un signal radioastronomique, puis la transmission numérique d'un message sous forme d'onde sonore. Ce projet s'inscrit dans le cadre d'un projet scolaire effectué en groupe avec d'autres camarades.

Le projet met en œuvre des notions de traitement du signal, de communications numériques, de programmation Python et de traitement de données binaires.

## Objectifs

- Observer un signal dans les domaines temporel et fréquentiel.
- Utiliser une transformée de Fourier rapide (FFT) et un spectrogramme pour caractériser un signal.
- Étudier le fonctionnement d'un filtre passe-bande et son intérêt pour réduire les composantes indésirables.
- Comprendre une modulation par déplacement de fréquence (FSK, utilisée sous forme audio dans le projet).
- Effectuer un codage et un décodage Manchester.
- Convertir du texte en octets UTF-8 et inversement.
- Appliquer un chiffrement XOR simple, puis effectuer l'opération inverse.
- Générer un signal audio représentant une suite de bits et l'enregistrer au format WAV.

## Technologies et bibliothèques

- **Python 3**
- **NumPy** : manipulation des tableaux numériques et des données binaires
- **SciPy** : lecture et écriture WAV, filtres numériques et outils de traitement du signal
- **Matplotlib** : tracé des signaux, spectres, spectrogrammes et diagrammes de Bode
- **Jupyter Notebook** : exécution progressive du projet et affichage des résultats
- **IPython** : lecture et affichage des signaux audio dans le notebook
- **Falstad** : simulation du filtre analogique RLC (outil externe au notebook)

## Installation

Créer un environnement Python, puis installer les bibliothèques nécessaires :

```bash
python -m venv .venv
```

Activer l'environnement :

```bash
# Windows
.venv\\Scripts\\activate

# Linux / macOS
source .venv/bin/activate
```

Installer les dépendances :

```bash
pip install numpy scipy matplotlib jupyter ipython
```

## Lancer le projet

1. Cloner ou télécharger le dépôt GitHub.
2. Placer le fichier audio d'entrée `signal_recu_transpose (1).wav` dans le même dossier que le notebook. Ce fichier est nécessaire aux premières parties d'analyse et de filtrage.
3. Ouvrir le notebook :

   ```bash
   jupyter notebook "Livrable 1 à 4.ipynb"
   ```

4. Exécuter les cellules dans l'ordre, car certaines variables et certains signaux sont réutilisés dans les cellules suivantes.
5. La dernière partie génère le fichier `signal_fsk.wav` dans le répertoire courant.

## Limites et améliorations connues

Le notebook constitue une démonstration pédagogique et une simulation logicielle. Quelques points doivent être corrigés ou vérifiés avant de considérer la transmission audio comme une boucle émission-réception entièrement validée :

- **Correspondance des fréquences en émission et en réception :** le générateur audio associe `0` à 880 Hz et `1` à 1 760 Hz. Dans la cellule de démodulation finale, les commentaires et la décision binaire associent au contraire `1` à 880 Hz et `0` à 1 760 Hz. Il faut harmoniser cette correspondance pour retrouver les bits d'origine.
- **Vérification finale du message :** l'affichage final de « Salut ! » s'appuie sur `bits_back`, une séquence obtenue lors d'une vérification effectuée avant la génération du fichier WAV. Pour valider réellement la transmission, le message final doit être reconstruit à partir des bits extraits du fichier `signal_fsk.wav`, après démodulation, décodage Manchester et déchiffrement XOR.
- **Recherche de la clé XOR :** la recherche de clé présentée dans le notebook est effectuée sur des octets issus de la chaîne de traitement logique précédente ; elle ne démontre pas, à elle seule, que la clé a été retrouvée à partir du signal audio reçu.
- **Fichier d'entrée :** `signal_recu_transpose (1).wav` est attendu par le notebook, mais n'est pas intégré automatiquement au code. Il doit être ajouté au dépôt ou fourni séparément, en tenant compte de ses éventuelles conditions de partage.

Ces points constituent des pistes d'amélioration pour fiabiliser le décodage et rendre la validation de bout en bout entièrement reproductible.

---

*Projet réalisé dans le cadre d'un travail sur le traitement du signal et les communications numériques.*
