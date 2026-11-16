[![Academic Year](https://img.shields.io/badge/Epitech-Tek1-blue?style=for-the-badge&logo=epitech&logoColor=white)](https://www.epitech.eu/)
[![Framework: Express](https://img.shields.io/badge/Node.js-Express-green.svg?style=for-the-badge&logo=express)](https://expressjs.com/)
[![Database: MySQL](https://img.shields.io/badge/Database-MySQL-4479A1.svg?style=for-the-badge&logo=mysql)](https://www.mysql.com/)
[![Module](https://img.shields.io/badge/Module-B--WEB--200-informational?style=for-the-badge)](#)

# 📋 EpyTodo — API REST de Gestion de Tâches & Utilisateurs

**EpyTodo** est une API RESTful complète développée en **Node.js** avec le framework **Express** et une base de données relationnelle **MySQL**. Elle implémente un système d'authentification par token JWT et un CRUD sécurisé pour la gestion de tâches personnelles.

---

## 🚀 Fonctionnalités & Routes de l'API

### 🔐 Authentification
- `POST /register` : Inscription d'un nouvel utilisateur (hachage du mot de passe avec bcrypt).
- `POST /login` : Connexion et délivrance d'un token d'authentification JSON Web Token (JWT).

### 👤 Gestion des Utilisateurs (`/user`, `/users`)
- `GET /user` : Récupère les informations du profil de l'utilisateur connecté (authentification requise).
- `GET /user/todos` : Récupère l'ensemble des tâches assignées à l'utilisateur connecté.
- `GET /users/:id` : Récupère les informations publiques d'un utilisateur par son ID.
- `PUT /users/:id` : Met à jour les informations d'un utilisateur.
- `DELETE /users/:id` : Supprime un compte utilisateur.

### 📝 Gestion des Tâches (`/todos`)
- `GET /todos` : Liste toutes les tâches enregistrées.
- `POST /todos` : Crée une nouvelle tâche (`title`, `description`, `due_time`, `user_id`, `status`).
- `GET /todos/:id` : Récupère les détails d'une tâche par son identifiant.
- `PUT /todos/:id` : Modifie les champs d'une tâche existante.
- `DELETE /todos/:id` : Supprime définitivement une tâche.

---

## 🗄️ Schéma de Base de Données (`epytodo.sql`)

- **Table `user`** : `id`, `email` (unique), `password` (hash bcrypt), `name`, `firstname`, `created_at`.
- **Table `todo`** : `id`, `title`, `description`, `created_at`, `due_time`, `status` (`not started`, `todo`, `in progress`, `done`), `user_id` (clé étrangère vers `user.id`).

---

## 📦 Installation & Démarrage

### 1. Initialiser la Base de Données
```bash
mysql -u root -p < epytodo.sql
```

### 2. Configurer les Variables d'Environnement (`.env`)
```ini
PORT=3000
MYSQL_HOST=localhost
MYSQL_USER=root
MYSQL_ROOT_PASSWORD=your_password
MYSQL_DATABASE=epytodo
SECRET=your_jwt_secret_key
```

### 3. Installer les Dépendances & Lancer le Serveur
```bash
npm install
npm start
```
Le serveur démarre par défaut sur `http://localhost:3000`.
