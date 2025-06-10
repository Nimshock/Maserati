# Maserati
Proyecto Final de Ciclo: Aplicación Web Maserati
# Proyecto Final de Ciclo: Aplicación Web Maserati

Este repositorio contiene el código fuente de una aplicación web completa desarrollada desde cero con **PHP nativo** y **MySQL**. El proyecto simula un portal para la marca de automóviles de lujo Maserati, implementando funcionalidades tanto para usuarios finales como para un panel de administración interna.

La aplicación demuestra un manejo robusto de la seguridad, una arquitectura de software modular y una clara separación de roles, integrando diversas tecnologías de frontend y backend para crear una experiencia de usuario completa y funcional.

## Características Principales

### 👨‍💻 Portal de Usuario (`index.php`)
- **Diseño Dinámico:** Una página de bienvenida con un diseño interactivo de tipo "single-page", que incluye:
    - Un slider principal animado en la cabecera.
    - Secciones de características, clientes y precios.
    - Una galería de modelos de coches con un filtro dinámico (BEV / Híbrido).
    - Un visor de detalles expandible para cada modelo de coche.
    - Un mapa interactivo (Leaflet.js) en la sección de contacto.
- **Sistema de Autenticación:**
    - Registro de nuevas cuentas de usuario con validación y hashing seguro de contraseñas (bcrypt).
    - Inicio de sesión para usuarios registrados.
- **Sistema de Reservas:**
    - Los usuarios pueden reservar los modelos de coches disponibles desde la galería.
    - **Regla de negocio:** Se implementa una validación que impide a los usuarios realizar una reserva si no han completado primero su documentación personal.
- **Panel de Cuenta de Usuario (`configuracion_user/`):**
    - **Gestión de Perfil:** Permite al usuario editar su nombre de usuario y cambiar su contraseña de forma segura.
    - **Gestión de Documentación:** Funcionalidad CRUD completa para que el usuario cree, vea y edite su documentación personal.
    - **Historial de Reservas:** Una sección donde el usuario puede consultar el historial y el estado de todas las reservas que ha realizado.

### ⚙️ Panel de Administración (`configuracion_admin/`)
- **Acceso Restringido:** Un portal de inicio de sesión separado y protegido, accesible únicamente para usuarios con el rol de 'admin'.
- **Dashboard Principal:** Un panel de control con accesos directos a las principales áreas de gestión.
- **Gestión Completa de Usuarios:**
    - Visualización de todos los usuarios en una tabla interactiva con paginación, búsqueda y ordenación.
    - Posibilidad de editar los datos de un usuario, incluyendo su rol (Usuario/Admin) y su contraseña.
    - Eliminación de usuarios, que gracias a `ON DELETE CASCADE` elimina también todos sus datos asociados (documentación, reservas), manteniendo la integridad de la base de datos.
- **Gestión Completa de Documentaciones:**
    - Visualización y búsqueda de todas las documentaciones creadas por los usuarios.
    - Funcionalidad para editar y eliminar cualquier documentación, actualizando el estado del usuario correspondiente.
- **Gestión Completa de Reservas:**
    - Visualización y búsqueda de todas las reservas de la plataforma.
    - Posibilidad de editar el estado de una reserva (Activa, Completada, Cancelada) y de eliminarla individualmente sin afectar al usuario.

## Tecnologías Utilizadas

-   **Backend:**
    -   **PHP 8.2** (Nativo, sin frameworks).
    -   Conexión a base de datos con **MySQLi**, utilizando sentencias preparadas para evitar inyección SQL.
    -   Gestión de sesiones (`$_SESSION`) para la autenticación y el estado del usuario.

-   **Frontend:**
    -   **HTML5** y **CSS3**.
    -   **JavaScript (jQuery):** Para la interactividad de la página principal (`index.php`), incluyendo animaciones y plugins.
    -   **Dos sistemas de diseño distintos:**
        1.  **Pluton Theme (Bootstrap 2.3.2):** Utilizado para la página principal (`index.php`), con un fuerte enfoque en animaciones.
        2.  **SB Admin Theme (Bootstrap 5):** Utilizado para los paneles de administración y configuración de usuario, ofreciendo una interfaz moderna y responsiva.
    -   **Librerías JS Adicionales:** `cSlider`, `bxSlider` (sliders), `MixItUp` (filtros), `Leaflet.js` (mapas), `Simple-DataTables` (tablas interactivas).

-   **Base de Datos:**
    -   **MySQL / MariaDB**.
    -   Diseño relacional normalizado con claves foráneas.
    -   Uso de `ON DELETE CASCADE` para mantener la integridad referencial de los datos.
    -   Transacciones SQL para operaciones críticas que requieren múltiples pasos.

-   **Seguridad:**
    -   Hashing de contraseñas con `password_hash()` (bcrypt).
    -   Uso de sentencias preparadas en todas las consultas SQL.
    -   Validación de roles de usuario para el acceso a las secciones de administración.

## Instalación y Puesta en Marcha

1.  **Requisitos:** Tener un servidor web local como XAMPP, WAMP o MAMP que soporte PHP 8+ y MySQL.
2.  **Base de Datos:**
    -   Crea una nueva base de datos en tu gestor (ej. phpMyAdmin).
    -   Importa el archivo `maserati_pfc.sql` para crear todas las tablas, relaciones y datos iniciales.
3.  **Configuración:**
    -   Abre el archivo `config/config.ini`.
    -   Modifica los valores (`DB_HOST`, `DB_USER`, `DB_PASS`, `DB_NAME`) para que coincidan con tu configuración de base de datos local.
4.  **Ejecución:**
    -   Coloca todos los archivos del proyecto en la carpeta `htdocs` (o `www`) de tu servidor local.
    -   Accede al proyecto desde tu navegador (ej. `http://localhost/nombre_de_la_carpeta_del_proyecto/`).
    -   **Credenciales de Administrador por defecto:**
        -   **Usuario:** `admin`
        -   **Contraseña:** `admin`

## Autor

-   **Cosmin Florin Stoian Stoian**
