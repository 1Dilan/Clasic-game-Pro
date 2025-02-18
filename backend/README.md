# Clasic-game-Pro
# Classic Game Pro - Backend Setup

## Estructura del Proyecto
```
backend/
├── src/                  # Código fuente de Laravel 8
├── docker/
│   ├── nginx/
│   │   └── default.conf # Configuración de Nginx
│   └── php/
│       └── Dockerfile   # Configuración de PHP
└── docker-compose.yml   # Configuración de Docker Compose
```

## Tecnologías Implementadas
- Docker y Docker Compose
- Laravel 8
- Nginx como servidor web
- MySQL 8.0 como base de datos
- PHP 8.0-fpm

## Configuración del Entorno

### Requisitos Previos
- Docker Desktop instalado
- Git instalado
- PowerShell (Windows)

### Servicios Docker Configurados
1. **PHP (Laravel)**
   - Contenedor: laravel_php
   - Configurado para Laravel 8
   - Incluye Composer y extensiones necesarias

2. **Nginx**
   - Contenedor: laravel_nginx
   - Puerto: 8000:80
   - Configurado como proxy inverso para PHP-FPM

3. **MySQL**
   - Contenedor: laravel_mysql
   - Puerto: 3306:3306
   - Credenciales por defecto:
     - Database: laravel
     - Username: laravel
     - Password: root

## Comandos Útiles

### Docker
```bash
# Iniciar contenedores
docker-compose up -d

# Detener contenedores
docker-compose down

# Reconstruir contenedores
docker-compose up -d --build

# Entrar al contenedor PHP
docker-compose exec php bash
```

### Laravel
```bash
# Generar key
php artisan key:generate

# Ejecutar migraciones
php artisan migrate

# Verificar versión
php artisan --version
```

## Rutas y Puertos
- Backend: http://localhost:8000
- Base de datos: localhost:3306

## Próximos Pasos
1. Configuración del frontend con React Native
2. Implementación de Kubernetes para despliegue
3. Configuración de CI/CD

## Notas Importantes
- Los archivos de configuración de Docker están en la carpeta `docker/`
- El código de Laravel se encuentra en la carpeta `src/`
- La base de datos persiste en un volumen Docker