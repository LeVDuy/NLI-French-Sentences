# French NLI : Inférence Automatique de la Relation entre Deux Phrases

Ce projet se concentre sur la tâche de **Natural Language Inference (NLI)** appliquée à la langue française. L'objectif est de déterminer la relation logique entre deux phrases : une *prémisse* (premise) et une *hypothèse* (hypothesis). 

Le système classifie cette relation selon trois catégories :
- **Entailment** 
- **Contradiction**
- **Neutral** 

## Objectifs du Projet
La NLI constitue une tâche fondamentale en Traitement Automatique des Langues Naturelles. L'objectif principal de ce dépôt est de comparer plusieurs stratégies d'apprentissage en mettant en évidence l'impact de :
1. **L'architecture du modèle :** Comparaison entre les architectures de type Encodeur et Décodeur.
2. **La stratégie d'adaptation :** Fine-tuning supervisé classique vs apprentissage en contexte (In-context learning).
3. **L'efficacité des paramètres :** Utilisation de techniques d'ajustement PEFT (Parameter-Efficient Fine-Tuning), notamment **LoRA**.

## Modèles et Approches
La NLI est ici traitée comme une tâche de classification de séquence (`SEQ_CLS`). Nous avons étudié et implémenté deux modèles encodeurs majeurs pour le français :

* **CamemBERT 2.0** (`almanach/camembert-base`) : Un modèle de type RoBERTa entraîné pour le français. Il est particulièrement performant pour encoder le sens des phrases et représente une excellente base pour la classification supervisée.
* **CamemBERTa 2.0** (`almanach/camemberta-base`) : Un modèle orienté français basé sur l'architecture DeBERTa. Il permet de comparer deux encodeurs francophones récents et d'observer comment les différences d'architecture (modules `query_proj`, `value_proj`) influencent l'application de méthodes comme LoRA.

## Pipeline d'Entraînement
Cette pipeline, de la donnée brute à l'entraînement, suit 5 étapes clés :
1. Chargement du tokenizer.
2. Tokenisation de la paire (`premise`, `hypothesis`).
3. Préparation des datasets via la bibliothèque HuggingFace.
4. Chargement du modèle de classification de séquence.
5. Injection de **LoRA** et lancement de l'entraînement supervisé.


## Installation et Utilisation

**1. Cloner le dépôt :**
```bash
git clone https://github.com/LeVDuy/NLI-French-Sentences.git
cd NLI-French-Sentences