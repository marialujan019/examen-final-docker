# Secure Stack – Docker Compose Deployment

Este repositorio contiene la orquestación de tres aplicaciones:
- API Backend (Flask)
- Frontend (Nginx + HTML/CSS/JS)
- Base de Datos PostgreSQL

Todas las imágenes utilizadas fueron construidas manualmente y subidas a Docker Hub como parte del examen. Este proyecto permite levantar todo el stack completo con un solo comando.

# Requisitos previos

Antes de comenzar se necesita:
- Docker instalado → https://docs.docker.com/engine/install/
- Docker Compose V2 → incluido en Docker Desktop o paquete aparte
- Acceso a Internet para descargar imágenes desde Docker Hub

# Cómo desplegar el proyecto

Clonar el repositorio:
git clone https://github.com/marialujan019/examen-final-docker.git
cd examen-final-docker

Levantar los servicios:
docker compose up -d

Verificar que todo está corriendo:
docker ps

# Acceso a las aplicaciones
Frontend:	http://localhost:8080
API Backend:	http://localhost:8000/health
PostgreSQL:	localhost:5432

# Notas
- Las tres imágenes (api, frontend, db) se construyeron manualmente siguiendo buenas prácticas de seguridad.
- Se realizaron escaneos de seguridad sobre las imagenes, las cuales se incluyeron en el entregable correspondiente.
- El frontend consulta al backend mediante http://localhost:8000/health, por lo que siempre debe iniciarse la API primero (Docker Compose lo maneja con depends_on)

