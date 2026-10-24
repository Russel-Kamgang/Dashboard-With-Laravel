<div align="center">

# Dashboard Laravel

**Application web Laravel 11 avec inscription, connexion et tableau de bord**

![Laravel](https://img.shields.io/badge/Laravel_11-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP_8.2-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)

</div>

---

## Présentation

Projet d'apprentissage du framework Laravel : une application MVC qui gère l'inscription d'utilisateurs, avec validation des formulaires côté serveur, persistance via Eloquent et des vues Blade stylées avec TailwindCSS.

## Fonctionnalités

- Page de connexion et page d'inscription
- Validation serveur des champs (nom, prénom, âge, email, confirmation du mot de passe)
- Enregistrement des utilisateurs avec Eloquent (`Personne`)
- Messages flash après inscription
- Vues Blade réutilisables (`partials/_form`) : tableau de bord, liste, formulaire, édition
- Migrations versionnées, dont l'ajout d'une colonne sur une table existante

## Architecture

```mermaid
flowchart LR
    browser((Navigateur)) --> routes[routes/web.php]
    routes --> ctrl[UserController]
    ctrl -->|validate| ctrl
    ctrl --> model[Model Personne<br/>Eloquent]
    model --> db[(MySQL)]
    ctrl --> views[Vues Blade<br/>login · register · dashboard]
```

| Route | Méthode | Action |
|-------|---------|--------|
| `/` | GET | Page de connexion |
| `/register` | GET | Formulaire d'inscription |
| `/register` | POST | Validation et création de l'utilisateur |

## Installation

Prérequis : PHP 8.2+, Composer, Node.js, MySQL.

```bash
git clone https://github.com/Russel-Kamgang/Dashboard-With-Laravel.git
cd Dashboard-With-Laravel

composer install
npm install

cp .env.example .env
php artisan key:generate
# Renseigner DB_DATABASE, DB_USERNAME et DB_PASSWORD dans .env

php artisan migrate
npm run dev        # dans un terminal
php artisan serve  # http://localhost:8000
```

## Structure

```
app/
├── Http/Controllers/     # UserController, AdminController
└── Models/               # Personne, Utilisateur, User
database/migrations/      # Schéma de la base
resources/views/          # Vues Blade
routes/web.php            # Routes de l'application
```

## Feuille de route

- [ ] Authentification complète (sessions, middleware `auth`)
- [ ] CRUD des utilisateurs depuis le tableau de bord
- [ ] Tests fonctionnels avec PHPUnit
- [ ] Conteneurisation avec Docker Compose (PHP-FPM, Nginx, MySQL)

## Licence

Code sous licence [MIT](https://opensource.org/licenses/MIT), comme le framework Laravel.
