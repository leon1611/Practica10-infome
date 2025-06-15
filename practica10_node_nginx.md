
# Práctica #10 Creación de un entorno CRUD Mascotas con Docker Compose Con Node y Nginx.

## 1. Título

**Práctica No 9: Creación de un CRUD FullStack de Mascotas (React + Spring Boot + PostgreSQL + pgAdmin) utilizando Docker Compose**

## 2. Tiempo de duración

La duración estimada para esta práctica es de aproximadamente 1 a 2 horas.

## 3. Fundamentos

En esta práctica, se aplican los conocimientos de desarrollo fullstack y Docker para crear un sistema CRUD de Mascotas compuesto por un frontend en React, un backend en Spring Boot con Kotlin y una base de datos PostgreSQL, todo orquestado mediante Docker Compose. Adicionalmente, se incluye pgAdmin como herramienta de administración de la base de datos.

Node.js se utiliza en este contexto como el entorno de ejecución para el desarrollo y compilación del frontend en React. Esto permite a los desarrolladores aprovechar las herramientas y el ecosistema de npm (Node Package Manager) para gestionar dependencias y scripts de construcción.

Nginx es incorporado como un servidor web de alto rendimiento y un proxy inverso. Su función principal aquí es servir los archivos estáticos del frontend de React (una vez compilados) de manera eficiente. También puede actuar como un proxy inverso para el backend de Spring Boot, centralizando el acceso a la aplicación y facilitando la gestión de dominios y certificados SSL en entornos de producción.

Docker Compose simplifica el levantamiento de múltiples servicios mediante un archivo `docker-compose.yml`, permitiendo definir redes, volúmenes y configuraciones de cada contenedor involucrado, logrando un entorno completamente aislado y reproducible.

## 4. Conocimientos previos

Docker permite crear contenedores para ejecutar aplicaciones de forma aislada, simplificando la configuración de entornos de desarrollo y despliegue (**Docker Documentation, 2025**). Docker Compose facilita la definición de entornos multi-contenedor mediante archivos YAML (**Docker Documentation, 2025**).

Spring Boot es un framework de desarrollo en Java/Kotlin que permite construir APIs REST de forma rápida (**Walls, 2016**), mientras que React permite construir interfaces de usuario interactivas en el navegador (**Griffiths, 2021**). PostgreSQL es un sistema de bases de datos relacional robusto y de código abierto (**PostgreSQL Documentation, 2025**). Finalmente, pgAdmin permite administrar de forma visual bases de datos PostgreSQL.

Node.js es un entorno de ejecución de JavaScript de código abierto, multiplataforma, que permite la ejecución de código JavaScript del lado del servidor (**Node.js Documentation, 2025**). Nginx es un servidor web de código abierto que también se puede utilizar como proxy inverso, equilibrador de carga, proxy de correo y caché HTTP (**Nginx Documentation, 2025**).

## 5. Objetivos a alcanzar

* Construir un archivo `docker-compose.yml` que integre los cuatro servicios.
* Implementar un backend REST con Spring Boot (Kotlin) para el manejo de mascotas.
* Construir un frontend en React con funcionalidad CRUD completa.
* Configurar pgAdmin para la administración de la base de datos.
* Definir redes y volúmenes Docker para la persistencia de datos y la comunicación entre servicios.
* Utilizar Node.js para la compilación del frontend de React.
* Configurar Nginx para servir el frontend de React y, opcionalmente, como proxy inverso para el backend.

## 6. Equipo necesario

* Computador con sistema operativo **Windows 10 con WSL 2** (o equivalente con Docker Desktop instalado).
* Docker Desktop y WSL instalados y en ejecución.
* Editor de código (Visual Studio Code o similar).
* Conexión a Internet para descarga de imágenes Docker y dependencias.
* Instalación de Node.js (incluido NPM) para el desarrollo del frontend.

## 7. Material de apoyo

* Documentación oficial de Docker, Spring Boot, React y PostgreSQL.
* Documentación de pgAdmin.
* Apuntes y ejemplos de clases.
* Documentación oficial de Node.js.
* Documentación oficial de Nginx.

## 8. Procedimiento

**Paso 1:** Crear la estructura de directorios del proyecto:

```
Otros/
├── mascota/          (Backend Spring Boot)
├── mascota-frontend/ (Frontend React + Nginx)
└── docker-compose.yml
```

**Paso 2:** Desarrollar el backend con Spring Boot (Kotlin), implementando la entidad `Mascota` y los controladores REST para realizar las operaciones CRUD.

**Paso 3:** Desarrollar el frontend en React, diseñando la interfaz de usuario y conectándose al backend mediante fetch API, gestionando las operaciones de creación, edición, eliminación y listado de mascotas. Durante este paso, se utilizará Node.js para instalar dependencias y ejecutar los scripts de desarrollo de React.

**Paso 4:** Crear el archivo `docker-compose.yml` para orquestar los servicios:

* Servicio `db` utilizando la imagen oficial de PostgreSQL.
* Servicio `pgadmin` para administración de la base de datos.
* Servicio `backend` con Spring Boot.
* Servicio `frontend` con React y Nginx para servir el build.

![2](https://github.com/user-attachments/assets/f6e7e092-104a-4605-b5fb-b8e8db827cfa)


**Paso 5:** Configurar el backend para permitir CORS desde el frontend.

**Paso 6:** Construir los Dockerfile respectivos para backend y frontend, configurando correctamente los entornos. El Dockerfile del frontend incluirá pasos para construir la aplicación React con Node.js y luego copiar los archivos estáticos generados a un contenedor Nginx para su distribución.

**Paso 7:** Configurar Nginx como proxy inverso y servidor de archivos estáticos. A continuación, se muestra un fragmento del archivo `docker-compose.yml` donde se define el servicio `nginx` y cómo se mapean los volúmenes para su configuración y los archivos estáticos del frontend.

![5](https://github.com/user-attachments/assets/23ff28e0-ba30-4591-a5ea-448956dcef77)

Además, se debe configurar el archivo de configuración de Nginx (`nginx.conf`) para manejar las rutas del frontend, backend y pgAdmin.

![6](https://github.com/user-attachments/assets/ad23ed03-8e4a-44a8-859e-79c7f92deb47)

**Paso 8:** Ejecutar `docker-compose up --build` para levantar el sistema completo.

**Paso 9:** Acceder al sistema CRUD desde el navegador:

* Frontend: `http://localhost:3000`
  
![1](https://github.com/user-attachments/assets/87defee7-96c0-4525-bbc0-dd71bd8c2d2f)

* Backend (API): `http://localhost:8080/api/mascotas`

![3](https://github.com/user-attachments/assets/2403c67b-f11e-4a1d-a281-b9d3c4afa307)


* pgAdmin: `http://localhost:8081`

![4](https://github.com/user-attachments/assets/11d15058-c593-4566-b0f4-9902ff25b97d)

## 9. Resultados esperados

Al finalizar la práctica, se obtiene un entorno funcional de un CRUD de mascotas. El frontend permite registrar, editar, eliminar y visualizar mascotas, mientras que el backend gestiona las operaciones sobre la base de datos PostgreSQL. pgAdmin permite observar y administrar visualmente los registros almacenados.

El uso de Node.js para el proceso de compilación asegura que el frontend de React se prepare correctamente para su despliegue. La inclusión de Nginx garantiza que el frontend se sirva de manera eficiente y escalable, y facilita la configuración de un proxy inverso para la API, mejorando la gestión del tráfico y la seguridad al unificar los puntos de acceso a través de un único puerto.

El entorno se encuentra completamente dockerizado, permitiendo portabilidad, reproducibilidad y facilidad de despliegue.

## 10. Bibliografía

* Docker Documentation. (2025). _Docker: Documentation_. https://docs.docker.com
* Griffiths, A. (2021). _Learning React: Modern Patterns for Developing React Apps_. O'Reilly Media.
* Node.js Documentation. (2025). _Node.js Documentation_. https://nodejs.org/docs/
* Nginx Documentation. (2025). _Nginx Documentation_. https://nginx.org/en/docs/
* PostgreSQL Documentation. (2025). _PostgreSQL Official Documentation_. https://www.postgresql.org/docs/
* Walls, C. (2016). _Spring Boot in Action_. Manning Publications.

