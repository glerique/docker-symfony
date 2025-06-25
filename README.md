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

**Option 1: Using Makefile (Recommended)**
```bash
git clone https://github.com/glerique/docker-symfony.git
cd docker-symfony
make install
```

**Option 2: Manual setup**
```bash
# Clone and setup
git clone https://github.com/glerique/docker-symfony.git
cd docker-symfony
cp .env.example .env.local

# Start the project
docker-compose up -d

# Install dependencies
docker exec -it docker-symfony-php-1 composer install
docker exec -it docker-symfony-node-1 npm ci

# Open http://localhost:8080
```

## 🔧 Detailed Setup

### Prerequisites
- Docker and Docker Compose
- Git

### Getting Started

### Getting Started

1. **Clone the repository**
```bash
git clone https://github.com/glerique/docker-symfony.git
cd docker-symfony
```

2. **Copy environment file**
```bash
cp .env.example .env.local
# Edit .env.local with your specific configuration if needed
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

6. **Access the application**
   - Open http://localhost:8080 in your browser
```bash
docker exec -it docker-symfony-node-1 npm ci
```

## 🔗 Available Services

- **Symfony Application**: http://localhost:8080
- **Adminer (Database)**: http://localhost:8081
- **Mailpit (Email testing)**: http://localhost:8025

## 🐛 Troubleshooting

### Container names not found?
If you get "No such container" errors, check the actual container names:
```bash
docker ps
# Then use the correct container names in commands
```

### Port already in use?
If port 8080 is already used, you can change it in `docker-compose.yaml`:
```yaml
nginx:
  ports:
    - "8081:80"  # Change 8080 to 8081 or any available port
```

### Permission issues?
If you have permission issues with files:
```bash
sudo chown -R $USER:$USER .
```

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

### Using Makefile
```bash
make help       # Show all available commands
make install    # Full project setup
make up         # Start containers
make down       # Stop containers
make logs       # Show container logs
make shell      # Enter PHP container
make composer   # Install PHP dependencies
make npm        # Install Node dependencies
make clean      # Clean containers and volumes
```

### Manual Docker Commands
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

## 🏗️ Project Structure

```
├── docker/
│   ├── nginx/          # Nginx configuration
│   └── php/           # PHP Dockerfile
├── assets/            # CSS/JS files
├── src/               # Symfony source code
├── templates/         # Twig templates
├── public/            # Web entry point
└── docker-compose.yaml # Services configuration
```

## 🤝 Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the [MIT License](LICENSE).
