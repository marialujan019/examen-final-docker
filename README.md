# Secure Stack – Docker Compose Deployment

Este repositorio contiene la orquestación de tres aplicaciones:
- API Backend (Flask)
- Frontend (Nginx + HTML/CSS/JS)
- Base de Datos PostgreSQL

Todas las imágenes utilizadas fueron construidas manualmente y subidas a Docker Hub como parte del examen. Este proyecto permite levantar todo el stack completo con un solo comando.

## Requisitos previos

Antes de comenzar se necesita:
- Docker instalado → https://docs.docker.com/engine/install/
- Docker Compose V2 → incluido en Docker Desktop o paquete aparte
- Acceso a Internet para descargar imágenes desde Docker Hub

## Instalación y despliegue

1) Clonar el repositorio:

```bash
git clone https://github.com/marialujan019/examen-final-docker.git
cd examen-final-docker
```

2) Levantar los servicios:
```bash
docker compose up -d
```

3) Verificar que todo está corriendo:
```bash
docker ps
```

## Acceso a las aplicaciones
- Frontend:	http://localhost:8080
- API Backend:	http://localhost:8000/health
- PostgreSQL:	localhost:5432 (ilustrativo)

## Notas
- Las tres imágenes (api, frontend, db) se construyeron manualmente siguiendo buenas prácticas de seguridad.
- Se realizaron escaneos de seguridad sobre las imagenes, las cuales se incluyeron en el entregable 2 correspondiente.
- El frontend consulta al backend mediante http://localhost:8000/health, por lo que siempre debe iniciarse la API primero (Docker Compose lo maneja con depends_on). Si la API tarda en levantar, revisar logs con docker compose logs -f

## Imagenes en dockerhub
- API: https://hub.docker.com/repository/docker/marialujan19/api-secure/tags/1.0.1
- Frontend: https://hub.docker.com/repository/docker/marialujan19/frontend-secure/tags/1.0.2
- DB: https://hub.docker.com/repository/docker/marialujan19/db-secure/tags/1.0.0

