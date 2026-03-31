# MyBank 🏦

Projet full-stack banking app.

- **Backend** : Symfony 7.4 (REST API, JWT Auth, Doctrine ORM)
- **Frontend** : React 18 + Vite (TypeScript)

---

## Structure

```
Mybank/
├── backend/          # Symfony 7
├── frontend/         # React + Vite (TypeScript)
├── docker-compose.yml
└── README.md
```

---

## Démarrage (local sans Docker)

### Backend (Symfony)

```bash
cd backend

# Copier et adapter les variables d'env
cp .env .env.local

# Installer les dépendances
composer install

# Créer la base de données (SQLite par défaut)
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate

# Lancer le serveur de dev
symfony serve
# ou
php -S localhost:8000 -t public
```

> L'API sera disponible sur : http://localhost:8000

### Frontend (React)

```bash
cd frontend

# Installer les dépendances
npm install

# Lancer le serveur de dev
npm run dev
```

> L'app sera disponible sur : http://localhost:5173

---

## Démarrage (avec Docker)

```bash
# Démarrer tous les services
docker-compose up -d

# Backend : http://localhost:8000
# Frontend : http://localhost:5173
# PostgreSQL : localhost:5432
```

> En mode Docker, modifier `backend/.env.local` pour utiliser PostgreSQL au lieu de SQLite :
> ```
> DATABASE_URL="postgresql://mybank:mybank@127.0.0.1:5432/mybank?serverVersion=16&charset=utf8"
> ```

---

## Variables d'environnement

### Backend (`backend/.env.local`)

| Variable | Description | Défaut |
|---|---|---|
| `DATABASE_URL` | URL de connexion DB | SQLite local |
| `JWT_PASSPHRASE` | Passphrase clé JWT | auto-générée |
| `APP_SECRET` | Secret Symfony | configuré |

### Frontend (`frontend/.env.local`)

| Variable | Description | Défaut |
|---|---|---|
| `VITE_API_URL` | URL du backend Symfony | `http://localhost:8000` |

---

## Stack technique

| Couche | Technologie |
|---|---|
| Backend | Symfony 7.4, PHP 8.4 |
| Auth | JWT (LexikJWTAuthenticationBundle) |
| ORM | Doctrine |
| Base de données | SQLite (dev) / PostgreSQL (prod) |
| CORS | NelmioCorsBundle |
| Frontend | React 18, Vite, TypeScript |
| Routing | React Router DOM |
| State | Zustand |
| Data fetching | TanStack Query + Axios |
| Forms | React Hook Form + Zod |
# MyBankCDA3
