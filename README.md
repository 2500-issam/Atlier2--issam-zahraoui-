# Atlier2--issam-zahraoui-
# École Mohammadia d’Ingénieurs – Département Modélisation et Informatique Scientifique

## Rapport d’Atelier 2 : Développement Web avec Django

**Réalisé par :** Issam ZAHRAOUI  
**Encadré par :** Pr. Abdelmajid BOUSSELHAM  
**Année universitaire :** 2025–2026

---

## Table des matières

1. [Introduction](#1-introduction)
2. [Objectifs](#2-objectifs)
3. [Définition des modèles](#3-définition-des-modèles)
   - 3.1 [Le modèle Product](#31-le-modèle-product)
   - 3.2 [Le modèle Category et la clé étrangère](#32-le-modèle-category-et-la-clé-étrangère)
4. [Migrations](#4-migrations)
5. [Vues](#5-vues)
6. [Configuration des URL](#6-configuration-des-url)
7. [Templates](#7-templates)
8. [Test de l’application](#8-test-de-lapplication)
9. [Connexion à MySQL](#9-connexion-à-mysql)
10. [Difficultés rencontrées](#10-difficultés-rencontrées)
11. [Conclusion](#11-conclusion)

---

## 1. Introduction

Cet atelier s’intéresse à la gestion et à la récupération des données dans une application Django.  
Le concept central est l’**ORM (Object Relational Mapping)** : un mécanisme qui permet de manipuler la base de données à travers des objets Python, sans écrire de requêtes SQL manuelles.  
Chaque classe Python définie comme modèle se traduit automatiquement en une table, et chacun de ses attributs correspond à une colonne.

---

## 2. Objectifs

Les compétences visées au terme de cet atelier sont :

- Concevoir et implémenter des modèles Django (`Product` et `Category`).
- Maîtriser le cycle de vie des migrations.
- Mettre en place des associations entre modèles via `ForeignKey`.
- Développer des vues et des templates permettant l’affichage des données.
- Configurer les routes de l’application.
- Tester l’application localement.
- Connecter le projet à une base de données MySQL.

---

## 3. Définition des modèles

### 3.1 Le modèle `Product`

Le modèle `Product` est défini dans `models.py` en héritant de `django.db.models.Model`.  
Il décrit la structure d’un produit avec les attributs suivants :

- `name` : désignation du produit (`CharField`).
- `description` : texte descriptif libre (`TextField`).
- `price` : montant décimal à deux chiffres (`DecimalField`).
- `stock` : quantité disponible, toujours positive (`PositiveIntegerField`).
- `image` : photo du produit, facultative (`ImageField`).
- `created_at` : horodatage de création, renseigné automatiquement (`DateTimeField`).

```python
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=255)
    description = models.TextField()
    price = models.DecimalField(max_digits=10, decimal_places=2)
    stock = models.PositiveIntegerField()
    image = models.ImageField(upload_to='products/', blank=True, null=True)
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.name
