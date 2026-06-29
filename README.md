# PA-CINEMA 🎬

Aplicación web de gestión de cine: catálogo de películas y sesiones, compra de entradas, gestión de usuarios y entrega de tickets. 

Proyecto desarrollado para la asignatura de **Proyecto de Aplicaciones (PA)** en la **Universidade da Coruña (UDC)**.

---

## 📂 Estructura del Proyecto

```text
PA-CINEMA/
├── backend/          # API REST en Spring Boot
├── frontend/         # Cliente web en React (Vite)
├── e2e-tests/        # Tests end-to-end con Maven
├── LICENSE.txt
└── README.md

```

---

## ☕ Backend (`/backend`)

API REST construida con **Spring Boot** y **Spring Data JPA**, con autenticación basada en **JWT** y persistencia en **MySQL**.

### Organización de Módulos

* **`model/entities`**: Entidades JPA (`User`, `Movie`, `Room`, `Session`, `Purchase`, `MovieSessions`) y sus repositorios (`*Dao`).
* **`model/services`**: Lógica de negocio: `UserService` (registro, login, perfil) y `CinemaService` (catálogo, sesiones, compras).
* **`model/exceptions`**: Excepciones de dominio (instancia no encontrada, asientos insuficientes, etc.).
* **`rest/controllers`**: Controladores REST (`UserController`, `CatalogController`, `PurchaseController`).
* **`rest/dtos`**: DTOs y conversores entre entidades y representación REST.
* **`rest/common`**: Configuración de seguridad (`SecurityConfig`, `JwtFilter`) y manejo global de errores (`CommonControllerAdvice`).
* **`src/sql`**: Scripts SQL para creación de esquema y carga de datos (`1-MySQLCreateTables.sql`, `2-MySQLCreateData.sql`).
* **`src/main/resources`**: Configuración (`application.yml`) e internacionalización de mensajes (**ES / EN / GL**).
* **`src/test`**: Tests unitarios y de integración de los servicios (`UserServiceTest`, `CinemaServiceTest`).

### 🚀 Ejecución

1. Asegúrate de tener una base de datos MySQL corriendo y configurada según el `application.yml`.
2. Ejecuta los scripts de `src/sql` para inicializar las tablas y los datos de prueba.
3. Levanta el servidor:
```bash
cd backend
mvn spring-boot:run

```



---

## ⚛️ Frontend (`/frontend`)

Cliente React construido con **Vite**, organizado por módulos funcionales y gestionado con el patrón **Redux** (actions, reducers, selectors).

### Organización de Módulos

* **`modules/catalog`**: Cartelera, detalle de película, selección de fecha y sesión.
* **`modules/shopping`**: Compra de entradas, historial y pasarela de entrega de tickets.
* **`modules/users`**: Autenticación, registro y gestión de perfil.
* **`modules/app` / `common**`: Estructura general (Header, Footer) y componentes compartidos (paginación, 404).
* **`backend/`**: Capa de abstracción y servicios de comunicación con la API (`appFetch`).
* **`i18n/`**: Soporte multiidioma con `react-intl` (**Español, Inglés, Galego**).

### 🚀 Ejecución

1. Crea un archivo `.env.development` basado en tus necesidades:
```env
VITE_API_URL=http://localhost:8080

```


2. Instala las dependencias y arranca el servidor de desarrollo:
```bash
cd frontend
npm install
npm run dev

```



---

## 🧪 Tests End-to-End (`/e2e-tests`)

Proyecto Maven independiente encargado de realizar las pruebas de caja negra sobre el sistema completo simulando el comportamiento del usuario.

```bash
cd e2e-tests
mvn test

```

---

## 📄 Licencia

Este proyecto está licenciado bajo los términos descritos en el archivo [LICENSE.txt](./LICENSE.txt)
```
