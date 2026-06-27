# 📋 GUÍA DE DESPLIEGUE — RecuperaciónJA
## GitHub + Supabase + Vercel — Paso a paso

---

## PASO 1 — Crear cuenta en Supabase (5 minutos)

1. Ve a **supabase.com** → Click en "Start your project" → "Sign in with GitHub"
   (usa tu cuenta de GitHub que ya tienes ✅)

2. Haz click en **"New project"**
   - Organization: tu usuario de GitHub
   - Name: `recuperacion-ja`
   - Database Password: genera una contraseña fuerte y **guárdala**
   - Region: **South America (São Paulo)** — la más cercana a Colombia
   - Click en **"Create new project"** — espera 2 minutos

3. Cuando esté listo, ve a **Settings → API** (en el menú de la izquierda)
   Copia estos dos valores (los necesitas en el Paso 3):
   - **Project URL** → se ve así: `https://abcxyz123.supabase.co`
   - **anon public key** → empieza con `eyJ...`

---

## PASO 2 — Crear las tablas en Supabase (2 minutos)

1. En el menú de la izquierda, click en **"SQL Editor"**
2. Click en **"New query"**
3. Abre el archivo `sql/crear_tablas.sql` que está en este proyecto
4. Copia TODO el contenido y pégalo en el editor de Supabase
5. Click en **"Run"** (botón verde)
6. Debes ver: `Success. No rows returned` — eso significa que todo salió bien ✅

---

## PASO 3 — Configurar las credenciales en el código (2 minutos)

1. Abre el archivo `js/supabase-config.js`
2. Reemplaza los valores:

```javascript
// ANTES (valores de ejemplo):
const SUPABASE_URL = 'https://XXXXXXXXXXXXXXXXXXXX.supabase.co';
const SUPABASE_KEY = 'eyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX';

// DESPUÉS (tus valores reales):
const SUPABASE_URL = 'https://tuproyecto.supabase.co';  // tu URL real
const SUPABASE_KEY = 'eyJ...tuclavereal...';             // tu anon key real
```

3. Guarda el archivo

---

## PASO 4 — Subir el código a GitHub (5 minutos)

### Opción A — Con Git (si ya lo tienes instalado)

Abre una terminal en la carpeta del proyecto y ejecuta:

```bash
git init
git add .
git commit -m "Initial commit — RecuperaciónJA"
git branch -M main
git remote add origin https://github.com/TUUSUARIO/recuperacion-ja.git
git push -u origin main
```

### Opción B — Sin Git (más fácil, solo con el navegador)

1. Ve a **github.com** → Click en "+" (arriba a la derecha) → "New repository"
2. Repository name: `recuperacion-ja`
3. Visibility: **Private** (para que sea solo tuyo)
4. Click en **"Create repository"**
5. En la página del repositorio vacío, click en **"uploading an existing file"**
6. Arrastra TODOS los archivos del proyecto:
   - `index.html`
   - `css/styles.css`
   - `js/supabase-config.js`
   - `js/app.js`
   - `sql/crear_tablas.sql`
7. Commit message: `"Initial commit"`
8. Click en **"Commit changes"** ✅

---

## PASO 5 — Desplegar en Vercel (3 minutos)

1. Ve a **vercel.com** → Click en "Continue with GitHub" → Autoriza Vercel

2. Click en **"Add New Project"** → **"Import Git Repository"**

3. Busca `recuperacion-ja` en la lista → Click en **"Import"**

4. En la pantalla de configuración:
   - Framework Preset: **Other** (no es React ni Next.js)
   - Root Directory: `./` (dejar como está)
   - Build Command: **dejar vacío**
   - Output Directory: **dejar vacío**

5. Click en **"Deploy"** → Espera 1 minuto

6. ✅ ¡Listo! Vercel te da un link como:
   `https://recuperacion-ja-XXXXX.vercel.app`

   Ese es tu link permanente — funciona desde cualquier dispositivo.

---

## PASO 6 — Verificar que todo funciona

1. Abre el link de Vercel en tu teléfono
2. Ve a la sección **"Medidas"** — deberías ver la Semana 1 ya cargada
   con tus datos basales (90.8 kg, grasa 30.8%, etc.)
3. Ve al **"Dashboard"**, registra tu dolor de hoy y guarda
4. Recarga la página — si el registro sigue ahí, ¡Supabase está funcionando! ✅

---

## ACTUALIZACIONES FUTURAS

Cada vez que quieras cambiar algo en la app:

1. Modifica el archivo correspondiente en GitHub
   (puedes editarlo directamente en el navegador en github.com)
2. Haz commit
3. Vercel lo detecta automáticamente y actualiza la app en 1-2 minutos

---

## RESUMEN DE CUENTAS NECESARIAS

| Plataforma | Para qué | Costo |
|---|---|---|
| GitHub | Almacenar el código | Gratis |
| Supabase | Base de datos permanente | Gratis (hasta 500MB) |
| Vercel | Publicar la app en internet | Gratis |

---

## ¿PROBLEMAS? — Errores frecuentes

**"Failed to fetch" o "Error al conectar"**
→ Revisa que la URL y la KEY en `supabase-config.js` sean correctas
→ Verifica que las tablas en Supabase se hayan creado (Paso 2)

**La app carga pero no guarda datos**
→ Ve a Supabase → Authentication → Policies
→ Verifica que las políticas de acceso público estén creadas

**Vercel da error de build**
→ Asegúrate de que Framework Preset esté en "Other"

---

¿Dudas en algún paso? El equipo médico también sabe de tecnología 😄
