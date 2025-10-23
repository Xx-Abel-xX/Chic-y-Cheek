# ChicCheek - Ecommerce Platform

Plataforma de ecommerce con frontend estático y backend Express.js.

## 🚀 Deployment en Railway

### 1. Preparar el proyecto

```bash
# Instalar dependencias
npm install

# Crear archivo .env con tus variables
cp .env.example .env
```

### 2. Subir a GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/tu-usuario/tu-repo.git
git push -u origin main
```

### 3. Deploy en Railway

1. Ve a [railway.app](https://railway.app) y registrate con GitHub
2. Click en "New Project" → "Deploy from GitHub repo"
3. Selecciona tu repositorio
4. Railway detectará automáticamente Node.js

### 4. Configurar MySQL en Railway

1. En tu proyecto Railway, click en "New" → "Database" → "Add MySQL"
2. Railway generará automáticamente: `MYSQL_URL`, `MYSQLHOST`, `MYSQLPORT`, etc.

### 5. Configurar variables de entorno

En Railway, ve a "Variables" y agrega:

```
PORT=5000
CORS_ORIGIN=https://tu-app.up.railway.app
DB_HOST=${{MYSQLHOST}}
DB_PORT=${{MYSQLPORT}}
DB_NAME=${{MYSQLDATABASE}}
DB_USER=${{MYSQLUSER}}
DB_PASSWORD=${{MYSQLPASSWORD}}
SESSION_SECRET=genera-uno-seguro
JWT_SECRET=genera-uno-seguro
COOKIE_DOMAIN=.railway.app
GOOGLE_CLIENT_ID=tu-id
GOOGLE_CLIENT_SECRET=tu-secret
GOOGLE_CALLBACK_URL=https://tu-app.up.railway.app/api/auth/google/callback
STRIPE_PUBLISHABLE_KEY=tu-key
STRIPE_SECRET_KEY=tu-secret
STRIPE_WEBHOOK_SECRET=tu-webhook-secret
AWS_ACCESS_KEY_ID=tu-key
AWS_SECRET_ACCESS_KEY=tu-secret
AWS_REGION=us-east-2
AWS_S3_BUCKET_NAME=uploader-chiccheek
```

### 6. Inicializar base de datos

Conecta a tu base de datos Railway y ejecuta los scripts SQL de `db/`.

### 7. Actualizar URLs

Actualiza en tu frontend todos los `localhost:5000` por `https://tu-app.up.railway.app`

## 💻 Desarrollo Local

```bash
# Iniciar todo (frontend + backend + stripe)
npm run dev

# Solo frontend
npm run front

# Solo backend
npm run api
```

## 📝 Notas

- **Frontend**: Se sirve desde `http://localhost:3000`
- **Backend**: API en `http://localhost:5000/api`
- **Base de datos**: MySQL en puerto 3306

## ⚠️ Seguridad

- Nunca subas el archivo `.env` a GitHub
- Genera secretos seguros para producción
- Actualiza las URLs de callback de Google OAuth
- Configura webhooks de Stripe con la nueva URL
