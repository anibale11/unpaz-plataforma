# Plataforma en Django Material


<br />

> Caracterìsticas

- Dependencias (./requirements.txt): **Django 3.2.6 LTS**
- [SCSS compilation](#recompile-css) via **Gulp**
- SQLite Database, Django Native ORM
- Modular design, clean codebase
- Deployment scripts: Docker, Gunicorn / Nginx


<br />


## Como ejectuar en un host?

```bash
$ # Descargar código
$ git clone https://gitlab.com/anibale11/portal-plataforma-unpaz.git
$ cd portal-plataforma-unpaz
$
$ # ejectuar Virtualenv en  (Unix OS/Linux OS)
$ virtualenv env
$ source env/bin/activate
$
$ # ejecutar Virtualenv en (Windows OS)
$ virtualenv env
$ .\env\Scripts\activate
$
$ # Instalar modules - SQLite
$ pip3 install -r requirements.txt
$
$ # Crear tablas
$ python manage.py makemigrations
$ python manage.py migrate
$
$ # Iniciar aplicación (development mode)
$ python manage.py runserver # default port 8000
$
$ # Iniciar aplicación en otro puerto
$ # python manage.py runserver 0.0.0.0:<port>
$
$ # Acceder por browser: http://127.0.0.1:8000/
```

> Note: Para usar la aplicación debe registrarse, de esa manera podrá ver las páginas que necesitan logueo.

<br />

## Estructura de Código


```bash
< PROJECTO >
   |
   |-- apps/
   |    |
   |    |-- home/                          # A simple app that serve HTML files
   |    |    |-- views.py                  # Serve HTML pages for authenticated users
   |    |    |-- urls.py                   # Define some super simple routes  
   |    |
   |    |-- authentication/                # Handles auth routes (login and register)
   |    |    |-- urls.py                   # Define authentication routes  
   |    |    |-- views.py                  # Handles login and registration  
   |    |    |-- forms.py                  # Define auth forms (login and register)
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component
   |         |    |-- sidebar.html         # Sidebar component
   |         |    |-- footer.html          # App Footer
   |         |    |-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                   # Master pages
   |         |    |-- base-fullscreen.html  # Used by Authentication pages
   |         |    |-- base.html             # Used by common pages
   |         |
   |         |-- accounts/                  # Authentication pages
   |         |    |-- login.html            # Login page
   |         |    |-- register.html         # Register page
   |         |
   |         |-- home/                      # UI Kit Pages
   |              |-- index.html            # Index page
   |              |-- 404-page.html         # 404 page
   |              |-- *.html                # All other pages
   |
   |-- requirements.txt                     # Development modules - SQLite storage
   |
   |-- .env                                 # Inject Configuration via Environment
   |-- manage.py                            # Start the app - Django default start script
   |
   |-- ************************************************************************
```

<br />

### Recompile CSS


* 1 - Instalar tools
```
NodeJS 12.x or higher
Gulp - globally
npm install -g gulp-cli
Yarn (optional)
```
* 2 - ir a Directorio assets
```
$ cd apps/static/assets
```
* 3 - Instalar modulos
```
$ npm install
// OR
$ yarn
```
* 4 - Editar & Recompilar SCSS files
```
$ gulp scss
```
el archivo generado se guarda en static/assets/css

# Deployment
### Ejecutar aplicación en Docker (Recomendado)
---

Puedes ejecutar la aplicación en un contenedor, con los siguientes pasos  

> Descargar el código

```bash
$ git clone https://gitlab.com/anibale11/portal-plataforma-unpaz.git
$ cd portal-plataforma-unpaz
```

> Start the app in Docker

```bash
$ docker-compose pull && docker-compose build && docker-compose up -d
```

Visit `http://localhost:85` in your browser. The app should be up & running.
