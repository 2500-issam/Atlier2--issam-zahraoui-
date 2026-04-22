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

# 🛒 Django E-Commerce Project

Un projet web développé avec le framework **Django** dans le cadre du module *Développement Web avec Python* à l'**École Mohammadia d'Ingénieurs**.

---

## 📋 Description

Ce projet est une application e-commerce simple permettant de gérer des **produits** et des **catégories**. Il a été réalisé en deux ateliers :

- **Atelier 1** : Découverte de Django, architecture MVT, création du projet et des vues statiques.
- **Atelier 2** : Gestion des données avec l'ORM Django, modèles, migrations, interface admin et connexion MySQL.

---

## 🚀 Fonctionnalités

- Liste de tous les produits
- Détail d'un produit
- Liste de toutes les catégories
- Détail d'une catégorie avec ses produits
- Interface d'administration Django
- Upload d'images produits
- Connexion à MySQL (ou SQLite par défaut)

---

## 🛠️ Technologies utilisées

| Technologie | Version |
|---|---|
| Python | 3.10+ |
| Django | 4.2 (LTS) |
| MySQL | Via XAMPP (MariaDB 10.4) |
| Pillow | 12.x |

---

## 📁 Structure du projet

```
ecommerce_project/
├── ecommerce/              # Dossier principal du projet
│   ├── ecommerce/          # Configuration Django
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── wsgi.py
│   │   └── asgi.py
│   ├── products/           # Application products
│   │   ├── migrations/
│   │   ├── templates/
│   │   │   └── products/
│   │   │       ├── product_list.html
│   │   │       ├── product_detail.html
│   │   │       ├── category_list.html
│   │   │       └── category_detail.html
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   └── admin.py
│   ├── images/             # Dossier des médias (images produits)
│   │   └── products/
│   └── manage.py
└── myenv/                  # Environnement virtuel (non versionné)
```

---

## ⚙️ Installation et lancement

### 1. Cloner le projet

```bash
git clone https://github.com/votre-username/ecommerce-django.git
cd ecommerce-django
```

### 2. Créer et activer l'environnement virtuel

```bash
# Windows
virtualenv myenv
myenv\scripts\activate

# Linux / macOS
virtualenv myenv
source myenv/bin/activate
```

### 3. Installer les dépendances

```bash
pip install django==4.2
pip install pillow
```

### 4. Configurer la base de données

**Option A — SQLite (par défaut, aucune configuration)**

Django utilise SQLite automatiquement. Aucune configuration supplémentaire n'est nécessaire.

**Option B — MySQL avec XAMPP**

1. Lancer XAMPP et démarrer Apache + MySQL
2. Créer la base `db_ecommerce` dans phpMyAdmin
3. Installer le connecteur :
```bash
pip install mysqlclient
```
4. Modifier `settings.py` :
```python
DATABASES = {
    'default': {
        'ENGINE'  : 'django.db.backends.mysql',
        'NAME'    : 'db_ecommerce',
        'USER'    : 'root',
        'PASSWORD': '',
        'HOST'    : 'localhost',
        'PORT'    : '3306',
    }
}
```

### 5. Appliquer les migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Créer un super-utilisateur (admin)

```bash
python manage.py createsuperuser
```

### 7. Lancer le serveur

```bash
python manage.py runserver
```

---

## 🌐 URLs disponibles

| URL | Description |
|---|---|
| `http://127.0.0.1:8000/products/` | Liste des produits |
| `http://127.0.0.1:8000/products/<id>` | Détail d'un produit |
| `http://127.0.0.1:8000/products/categories/` | Liste des catégories |
| `http://127.0.0.1:8000/products/category/<id>/` | Produits d'une catégorie |
| `http://127.0.0.1:8000/admin/` | Interface d'administration |

---

