# Entregable 4: Kubernetes Manifests

Este repositorio incluye los manifiestos necesarios para desplegar:
- API (backend)
- Frontend (nginx estático)
- DB PostgreSQL (ilustrativa, no integrada con la API)

## Requisitos

- kubectl instalado
- Un cluster Kubernetes local (ej: Minikube o Kind)

## Despliegue

### 1) Crear el namespace
```bash
kubectl apply -f k8s/00-namespace.yaml
```

### 2) Crear credenciales de Postgres (NO se suben al repo)
Nota: La base de datos es ilustrativa. Las credenciales se cargan como Secret en el cluster.

```bash
kubectl create secret generic postgres-secret \
  -n secure-stack \
  --from-literal=POSTGRES_USER="<tu_usuario>" \
  --from-literal=POSTGRES_PASSWORD="<tu_password>" \
  --from-literal=POSTGRES_DB="<tu_db>"
```

### 3) Aplicar el resto de manifiestos
```bash
kubectl apply -f k8s/
```

### Verificación
```bash
kubectl get pods -n secure-stack
kubectl get svc -n secure-stack
```

## Acceso a las aplicaciones
- Frontend (NodePort): http://localhost:30080
- API (NodePort): Healthcheck: http://localhost:30081/health
- Base de datos: No se expone hacia afuera (Service tipo ClusterIP). Disponible internamente como db:5432 en el namespace secure-stack

## Limpieza

```bash
kubectl delete -f k8s/
```

## Consideraciones de seguridad

- Contenedores ejecutados sin escalación de privilegios
- Capacidades Linux eliminadas (principio de mínimo privilegio)
- Base de datos no expuesta externamente
- Credenciales gestionadas mediante Secrets y no versionadas


