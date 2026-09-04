# Postgres Docker Template

Plantilla de base de datos PostgreSQL lista para ser utilizada en cualquier proyecto local a traves de Docker Compose.

---

## 1. Requisitos Previos

- Tener instalado Docker Desktop.
- Asegurarse de que el puerto 5432 este libre en su computadora.

## 2. Configuracion de Credenciales

Para mantener la seguridad y permitir que multiples desarrolladores configuren sus propias bases de datos, este proyecto utiliza variables de entorno. 

Siga estos pasos para configurar su base de datos local:

### Paso A: Crear el archivo de entorno
Copie el archivo base `.env.example` y nombre a la copia `.env` dentro de este mismo directorio.

### Paso B: Asignar valores
Abra el archivo `.env` en su editor de codigo y coloque los valores que desee usar para su proyecto.

![Editor de codigo mostrando el archivo de variables de entorno](C:\Users\esaum\.gemini\antigravity-ide\brain\ea5eb2b3-1825-472e-9b92-4a268ce0e0ac\step_1_env_file_1788561201615.jpg)

*Nota: Si decide no crear el archivo `.env`, Docker inicializara el contenedor con los valores por defecto (example_user, example_db).*

---

## 3. Inicializacion del Contenedor

Una vez configurado el archivo de entorno, puede encender el servidor de base de datos.

1. Abra una terminal en este directorio (`hycon-db`).
2. Ejecute el comando de encendido en segundo plano:

```bash
docker-compose up -d
```

![Terminal ejecutando el comando docker-compose up](C:\Users\esaum\.gemini\antigravity-ide\brain\ea5eb2b3-1825-472e-9b92-4a268ce0e0ac\step_2_docker_up_1788561218608.jpg)

### Comandos de Mantenimiento
- **Detener el servidor temporalmente:** `docker-compose stop`
- **Volver a iniciar el servidor:** `docker-compose start`
- **Destruir el contenedor (Mantiene la informacion en el volumen):** `docker-compose down`

---

## 4. Conexion desde la Aplicacion

Para conectar cualquier ORM o backend a esta base de datos, construya su URL de conexion utilizando los valores que coloco en el archivo `.env`.

**Estructura de la URL:**
```text
postgresql://<POSTGRES_USER>:<POSTGRES_PASSWORD>@localhost:<POSTGRES_PORT>/<POSTGRES_DB>?schema=public
```

**Ejemplo de uso en un proyecto Node.js / Prisma:**
```env
DATABASE_URL="postgresql://example_user:example_password@localhost:5432/example_db?schema=public"
```
