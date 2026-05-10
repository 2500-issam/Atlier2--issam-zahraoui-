# Projet E-commerce Django

Ce projet est une application e-commerce développée avec Django. Il permet de gérer des produits et des catégories.

## Fonctionnalités

- Gestion des produits (nom, prix, image, catégorie)
- Gestion des catégories
- Interface d'administration Django
- Templates pour l'affichage des produits et catégories

## Installation

1. Clonez le repository :
   ```
   git clone <url-du-repo>
   cd ecommerce_project
   ```

2. Créez un environnement virtuel :
   ```
   python -m venv venv
   source venv/bin/activate  # Sur Windows : venv\Scripts\activate
   ```

3. Installez les dépendances :
   ```
   pip install -r requirements.txt
   ```

4. Appliquez les migrations :
   ```
   python manage.py migrate
   ```

5. Créez un superutilisateur :
   ```
   python manage.py createsuperuser
   ```

6. Lancez le serveur :
   ```
   python manage.py runserver
   ```

## Configuration PostgreSQL (optionnel)

Par défaut, le projet utilise SQLite. Pour utiliser PostgreSQL :

1. Installez PostgreSQL et créez une base de données `db_ecommerce`.
2. Modifiez `DATABASES` dans `settings.py` pour PostgreSQL (USER: postgres, PASSWORD: password par défaut).
3. Exécutez `python manage.py migrate`.

## Utilisation

- Accédez à l'application : http://127.0.0.1:8000/products/
- Interface admin : http://127.0.0.1:8000/admin/

## Structure du projet

- `ecommerce/` : Configuration principale
- `products/` : Application pour les produits et catégories
- `templates/` : Templates HTML
- `static/` : Fichiers statiques (CSS, JS)
- `media/` : Images uploadées

## Technologies utilisées

- Django 6.0.4
- Python 3.13
- Base de données : SQLite (par défaut) ou MySQL