# HorariosAca — Django + MySQL

Aplicación web para la gestión y generación de horarios académicos. El frontend y backend están integrados en un solo proyecto Django.

## Tecnologías

| Capa | Tecnología |
|------|-----------|
| Frontend | HTML, CSS, JavaScript (servido por Django) |
| Backend | Python 3.12+ + Django 6.0 |
| Base de datos | MySQL 8.4 |
| Servidor web | Django (desarrollo) |

---

## Requisitos previos

- [Python 3.12+](https://www.python.org/downloads/) — marcar **"Add python.exe to PATH"** al instalar
- [Git](https://git-scm.com/downloads)
- MySQL 8.4 — puede usarse [Laragon](https://laragon.org/download/) o cualquier instalación de MySQL

---

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/DyowenDozh/HorariosAca-Django.git
cd HorariosAca-Django
```

### 2. Crear la base de datos

Conectarse a MySQL y ejecutar:

```sql
CREATE DATABASE horariosaca CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```

### 3. Configurar el backend

Navegar a la carpeta del proyecto:

```bash
cd "backend/HorariosAca Python modulo registro/tallerexpress"
```

Crear el entorno virtual:

```bash
python -m venv .venv
```

Activarlo (Windows CMD):

```bash
.venv\Scripts\activate.bat
```

Instalar dependencias:

```bash
pip install -r requirements.txt
```

Aplicar migraciones:

```bash
python manage.py migrate
```

### 4. Correr el servidor

```bash
python manage.py runserver
```

---

## Uso

1. Iniciar MySQL
2. Correr el servidor Django:
   ```bash
   python manage.py runserver
   ```
3. Abrir en el navegador:
   ```
   http://localhost:8000/
   ```

---

## Páginas disponibles

| URL | Descripción |
|-----|-------------|
| `http://localhost:8000/` | Página principal |
| `http://localhost:8000/login/` | Iniciar sesión |
| `http://localhost:8000/register/` | Registrarse |
| `http://localhost:8000/dashboard/` | Panel de horarios |
| `http://localhost:8000/settings/` | Configuración de cuenta |
| `http://localhost:8000/plans/` | Planes de suscripción |
| `http://localhost:8000/trash/` | Papelera |
| `http://localhost:8000/terms/` | Términos y condiciones |

---

## Endpoints de la API

| Método | URL | Descripción |
|--------|-----|-------------|
| POST | `/api/auth/register/` | Registrar usuario |
| POST | `/api/auth/login/` | Iniciar sesión |
| GET | `/api/auth/usuarios/{id}/` | Obtener datos del usuario |
| PUT | `/api/auth/usuarios/{id}/update/` | Actualizar nombre o contraseña |
| DELETE | `/api/auth/usuarios/{id}/delete/` | Eliminar cuenta |

---

## Estructura del proyecto

```
HorariosAca-Django/
├── backend/
│   └── HorariosAca Python modulo registro/
│       └── tallerexpress/
│           ├── accounts/           # App de usuarios (modelos, vistas, URLs)
│           ├── tallerexpress/      # Configuración Django (settings, urls, views)
│           ├── templates/          # Archivos HTML
│           │   ├── index.html
│           │   ├── login.html
│           │   ├── register.html
│           │   ├── dashboard.html
│           │   ├── settings.html
│           │   └── ...
│           ├── static/             # Archivos CSS, JS e imágenes
│           │   ├── style.css
│           │   ├── dashboard.css
│           │   ├── login.js
│           │   ├── register.js
│           │   └── ...
│           ├── manage.py
│           └── requirements.txt
├── .gitignore
└── README.md
```

---

## Notas

- Las contraseñas se almacenan hasheadas con **bcrypt** (Django hashers).
- El archivo `settings.py` usa credenciales de desarrollo (`root` sin contraseña). No usar en producción.
- Si MySQL tiene contraseña, editar `tallerexpress/settings.py`:
  ```python
  'PASSWORD': 'tu_contraseña',
  ```
- El `.venv` no está en el repositorio — cada desarrollador debe crearlo localmente con `python -m venv .venv`.
