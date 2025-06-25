# Symfony Docker Project

A complete Symfony development environment with Docker, featuring PHP 8.3, Nginx, PostgreSQL, and Node.js for modern web development.

## ✨ Features

- **PHP 8.3** with FPM and Xdebug
- **Nginx** as web server
- **PostgreSQL 16** database
- **Adminer** for database management
- **Mailpit** for email testing
- **Node.js 20** for asset compilation
- **Tailwind CSS** ready to use

## 🚀 Quick Start

### Prerequisites
- Docker and Docker Compose
- Git

### Getting Started

#### Manual Setup
1. **Clone the repository**
```bash
git clone https://github.com/glerique/docker-symfony.git
cd docker-symfony
```

2. **Copy environment file**
```bash
cp .env.example .env.local
# Edit .env.local with your specific configuration
```

3. **Start containers**
```bash
docker-compose up -d
```

4. **Install PHP dependencies**
```bash
docker exec -it docker-symfony-php-1 composer install
```

5. **Install Node.js dependencies**
```bash
docker exec -it docker-symfony-node-1 npm ci
```

## 🔗 Available Services

- **Symfony Application**: http://localhost:8080
- **Adminer (Database)**: http://localhost:8081
- **Mailpit (Email testing)**: http://localhost:8025

## 📊 Database Configuration

- **Host**: db
- **Port**: 5432
- **Database**: symfony
- **Username**: symfony
- **Password**: secret

## 📁 Environment Configuration

This project uses Symfony's environment file hierarchy:

- **`.env`** - Default values (committed to Git)
- **`.env.local`** - Your local overrides (ignored by Git)
- **`.env.example`** - Template file with all available variables

**Important**: Never commit secrets or local configuration to `.env.local`!

## 🛠️ Useful Commands

### PHP/Symfony
```bash
# Enter PHP container
docker exec -it docker-symfony-php-1 bash

# Run Symfony commands
docker exec -it docker-symfony-php-1 php bin/console cache:clear

# Install PHP package
docker exec -it docker-symfony-php-1 composer require <package>
```

### Node.js/Assets
```bash
# Enter Node container
docker exec -it docker-symfony-node-1 sh

# Build assets
docker exec -it docker-symfony-node-1 npm run build

# Watch mode (development)
docker exec -it docker-symfony-node-1 npm run watch

# Install Node package
docker exec -it docker-symfony-node-1 npm install <package-name>
```

### Database
```bash
# Create database
docker exec -it docker-symfony-php-1 php bin/console doctrine:database:create

# Run migrations
docker exec -it docker-symfony-php-1 php bin/console doctrine:migrations:migrate
```