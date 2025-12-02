# ENCUESTAS-DDS

Sistema web completo para la creación, gestión y análisis de encuestas, desarrollado con Laravel 11 y Tailwind CSS.

## Características

- Registro y autenticación de usuarios
- Gestión de empresas
- Creación de encuestas personalizadas
- Múltiples tipos de preguntas (opción múltiple, texto libre)
- Sistema de respuestas públicas
- Reportes y análisis de resultados
- Panel de administración intuitivo

## Requisitos Previos

Antes de instalar el proyecto, asegúrate de tener instalado:

- **PHP >= 8.2** con las siguientes extensiones:
  - OpenSSL
  - PDO
  - Mbstring
  - Tokenizer
  - XML
  - Ctype
  - JSON
  - BCMath
  - SQLite (para la base de datos)
- **Composer** (Gestor de dependencias de PHP)
- **Node.js >= 18** y **npm** (Para compilar assets frontend)
- **Git** (Para clonar el repositorio)

## Instalación

Sigue estos pasos para configurar el proyecto en tu máquina local:

### 1. Clonar el repositorio

```bash
git clone https://github.com/SANDEV23/ENCUESTAS-DDS.git
cd ENCUESTAS-DSS
```

### 2. Instalar dependencias de PHP

```bash
composer install
```

### 3. Configurar el archivo de entorno

Copia el archivo de ejemplo y genera la clave de aplicación:

```bash
# En Windows (CMD)
copy .env.example .env

# En Windows (PowerShell) o Linux/Mac
cp .env.example .env

# Generar clave de aplicación
php artisan key:generate
```

### 4. Configurar la base de datos

El proyecto está configurado para usar SQLite por defecto. Crea el archivo de base de datos:

```bash
# En Windows (CMD)
type nul > database\database.sqlite

# En Windows (PowerShell)
New-Item database\database.sqlite

# En Linux/Mac
touch database/database.sqlite
```

**Nota:** Si prefieres usar MySQL o PostgreSQL, edita el archivo `.env` y configura las credenciales correspondientes.

### 5. Ejecutar las migraciones

Crea las tablas de la base de datos:

```bash
php artisan migrate
```

### 6. Instalar dependencias de Node.js

```bash
npm install
```

### 7. Compilar los assets frontend

```bash
# Para desarrollo (con hot-reload)
npm run dev

# Para producción
npm run build
```

### 8. Iniciar el servidor de desarrollo

En una nueva terminal, ejecuta:

```bash
php artisan serve
```

El sitio estará disponible en: `http://localhost:8000`

## Uso

### Primer acceso

1. Abre tu navegador en `http://localhost:8000`
2. Haz clic en "Registrar Empresa" si representas una organización
3. O crea una cuenta de usuario directamente en "Crear Cuenta"
4. Inicia sesión con tus credenciales

### Crear una encuesta

1. Desde el dashboard, ve a "Encuestas"
2. Haz clic en "Nueva Encuesta"
3. Completa los datos básicos
4. Agrega preguntas de diferentes tipos
5. Publica la encuesta para empezar a recibir respuestas

### Compartir encuestas

Las encuestas generan un enlace público que puedes compartir con los participantes sin que necesiten crear una cuenta.

## Estructura del Proyecto

```
SISTEMA_DE_ENCUESTAS/
├── app/
│   ├── Http/Controllers/    # Controladores
│   ├── Models/              # Modelos Eloquent
│   └── ...
├── database/
│   ├── migrations/          # Migraciones de base de datos
│   └── database.sqlite      # Base de datos SQLite
├── resources/
│   ├── views/              # Vistas Blade
│   └── css/                # Estilos
├── routes/
│   └── web.php             # Rutas de la aplicación
├── public/                 # Archivos públicos
└── ...
```

## Scripts Disponibles

```bash
# Desarrollo
npm run dev              # Servidor de desarrollo con hot-reload
php artisan serve        # Servidor PHP en localhost:8000

# Producción
npm run build           # Compilar assets para producción

# Base de datos
php artisan migrate             # Ejecutar migraciones
php artisan migrate:fresh       # Resetear base de datos y migrar
php artisan migrate:status      # Ver estado de migraciones

# Caché y optimización
php artisan cache:clear         # Limpiar caché
php artisan config:clear        # Limpiar caché de configuración
php artisan route:c