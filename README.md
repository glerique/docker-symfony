# Projet Symfony avec Docker

## 🚀 Installation

### Prérequis
- Docker et Docker Compose
- Git

### Lancement du projet

#### Option 1 : Script automatique
```bash
git clone <url-du-repo>
cd docker-symfony
./setup.sh
```

#### Option 2 : Makefile (recommandé)
```bash
git clone <url-du-repo>
cd docker-symfony
make install
```

#### Option 3 : Manuel
1. **Cloner le repository**
```bash
git clone <url-du-repo>
cd docker-symfony
```

2. **Copier le fichier d'environnement**
```bash
cp .env.local .env
```

3. **Démarrer les conteneurs**
```bash
docker-compose up -d
```

4. **Installer les dépendances PHP**
```bash
docker exec -it docker-symfony-php-1 composer install
```

5. **Installer les dépendances Node.js**
```bash
docker exec -it docker-symfony-node-1 npm ci
```

## 🔗 Services disponibles

- **Application Symfony** : http://localhost:8080
- **Adminer (base de données)** : http://localhost:8081
- **Mailpit (emails)** : http://localhost:8025

## 📊 Base de données

- **Host** : db
- **Port** : 5432
- **Database** : symfony
- **Username** : symfony
- **Password** : secret

## 🛠️ Commandes utiles

### PHP/Symfony
```bash
# Entrer dans le conteneur PHP
docker exec -it docker-symfony-php-1 bash

# Lancer une commande Symfony
docker exec -it docker-symfony-php-1 php bin/console cache:clear

# Installer une dépendance
docker exec -it docker-symfony-php-1 composer require <package>
```

### Node.js/Assets
```bash
# Entrer dans le conteneur Node
docker exec -it docker-symfony-node-1 sh

# Build des assets
docker exec -it docker-symfony-node-1 npm run build

# Watch mode (développement)
docker exec -it docker-symfony-node-1 npm run watch

# Installer un nouveau package (utiliser npm install)
docker exec -it docker-symfony-node-1 npm install <package-name>
```

### Base de données
```bash
# Créer la base de données
docker exec -it docker-symfony-php-1 php bin/console doctrine:database:create

# Lancer les migrations
docker exec -it docker-symfony-php-1 php bin/console doctrine:migrations:migrate
```

## 🏗️ Architecture

```
├── docker/
│   ├── nginx/          # Configuration Nginx
│   └── php/           # Dockerfile PHP
├── assets/            # Fichiers CSS/JS
├── src/               # Code source Symfony
├── templates/         # Templates Twig
├── public/            # Point d'entrée web
└── docker-compose.yaml # Configuration des services
```
