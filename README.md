# Projet : Modélisation du Risque de Crédit

## Description

Ce projet a pour objectif de construire un **modèle de scoring de crédit** permettant de prédire le risque de défaut des clients.  
Le workflow comprend :

1. **Préparation et exploration des données**  
   - Analyse des valeurs manquantes et des distributions  
   - Détection et traitement des valeurs atypiques  
   - Statistiques descriptives sur les variables continues et catégorielles  

2. **Transformation et encodage des variables**  
   - Conversion des variables discrètes en catégorielles  
   - Encodage des variables catégorielles en entiers (`0, 1, 2...`)  
   - Discrétisation de certaines variables numériques pour faciliter l’interprétation  

3. **Séparation train/test et contrôle de stabilité**  
   - Split stratifié pour préserver la distribution de la cible  
   - Vérification de la comparabilité entre train et test via le **Population Stability Index (PSI)**  

4. **Analyse de l’importance des variables**  
   - Calcul du **V de Cramer** pour les variables catégorielles  
   - Calcul du **Weight of Evidence (WoE)** et de l’**Information Value (IV)**  
   - Sélection des variables les plus pertinentes pour la modélisation  

5. **Modélisation et évaluation**  
   - Construction d’un modèle prédictif utilisant les variables sélectionnées  
   - Évaluation des performances sur le jeu de test  

---

## Installation et dépendances

Le projet utilise **Python 3** et peut être configuré via **`uv`** pour créer un environnement virtuel et installer les dépendances automatiquement.  

```bash
# Créer l'environnement virtuel
uv create -f

# Ajouter les packages utilisés dans le projet
uv add pandas numpy scikit-learn matplotlib seaborn
```

Alternativement, si vous préférez utiliser pip directement, vous pouvez installer les dépendances via le fichier requirements.txt fourni :

```bash
pip install -r requirements.txt
```

---

## Données

Le jeu de données principal est `credit.sas7bdat`.  
Toutes les manipulations et analyses sont effectuées à partir de ce fichier.

## Utilisation

1. **Chargement des données** : lire `credit.sas7bdat` dans un DataFrame Pandas.
2. **Exploration et préparation** : suivre les notebooks pour l’analyse des valeurs manquantes, détection d’outliers, statistiques descriptives et encodage des variables.
3. **Split train/test** : les notebooks montrent comment effectuer la séparation stratifiée pour préserver la distribution de la cible.
4. **Analyse des variables** : calcul du PSI, du V de Cramer, et de l’IV pour guider la sélection des variables.
5. **Modélisation** : utiliser les variables sélectionnées pour entraîner et tester un modèle prédictif.

## Notes importantes

- L’encodage des variables catégorielles est effectué **d’abord sur le train**, puis appliqué au test pour garantir la cohérence et éviter les erreurs de correspondance.
- Le PSI est calculé **après le split** pour vérifier que les distributions train et test sont comparables.
- Les variables continues peuvent être **discrétisées** pour faciliter l’interprétation et la création de catégories économiques logiques.