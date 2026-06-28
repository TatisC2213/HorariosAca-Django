# HorariosAca — Django + MySQL

Aplicación web para la gestión y generación de horarios académicos.

## Tecnologías

| Capa | Tecnología |
|------|-----------|
| Frontend | HTML, CSS, JavaScript |
| Backend | Python 3.14 + Django 6.0 |
| Base de datos | MySQL 8.4 (Laragon) |
| Servidor web | Apache (Laragon) |

---

## Requisitos previos

- [Laragon](https://laragon.org/download/) — incluye Apache y MySQL
- [Python 3.12+](https://www.python.org/downloads/) — marcar **"Add python.exe to PATH"** al instalar
- [Git](https://git-scm.com/downloads)

---

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/DyowenDozh/HorariosAca-Django.git
cd HorariosAca-Django
```

### 2. Configurar el frontend

Copiar la carpeta `frontend/HorariosAca` dentro de la carpeta `www` de Laragon:

```
C:\laragon\www\HorariosAca\
```

### 3. Crear la base de datos

Iniciar Laragon y abrir [http://localhost/phpmyadmin](http://localhost/phpmyadmin) o usar DBeaver conectado a `localhost:3306`. Ejecutar:

```sql
CREATE DATABASE horariosaca CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```

### 4. Configurar el backend

Navegar a la carpeta del backend:

```bash
cd "backend/HorariosAca Python modulo registro/tallerexpress"
```

Crear y activar el entorno virtual:

```bash
# Windows CMD
python -m venv .venv
.venv\Scripts\activate.bat
```

Instalar dependencias:

```bash
pip install -r requirements.txt
```

> Si `pip` no funciona, usar: `C:\Python314\python.exe -m pip install -r requirements.txt`

Aplicar migraciones:

```bash
python manage.py migrate
```

### 5. Correr el servidor

```bash
python manage.py runserver
```

El backend queda disponible en `http://localhost:8000`.

---

## Uso

1. Iniciar **Laragon** (Start All — Apache + MySQL)
2. Correr el servidor Django (`python manage.py runserver`)
3. Abrir en el navegador: [http://localhost/HorariosAca/login.html](http://localhost/HorariosAca/login.html)

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
│   └── tallerexpress/
│       ├── accounts/        # App de usuarios (modelos, vistas, URLs)
│       ├── tallerexpress/   # Configuración Django (settings, urls)
│       ├── manage.py
│       └── requirements.txt
├── frontend/
│   └── HorariosAca/        # HTML, CSS, JS
│       ├── login.html
│       ├── register.html
│       ├── dashboard.html
│       ├── settings.html
│       └── ...
├── .gitignore
└── README.md
```

---

## Notas

- Las contraseñas se almacenan hasheadas con **bcrypt** (Django hashers).
- El archivo `settings.py` usa credenciales de desarrollo (`root` sin contraseña). No usar en producción.
- Si MySQL tiene contraseña, editar `backend/.../tallerexpress/settings.py`:
  ```python
  'PASSWORD': 'tu_contraseña',
  ```
