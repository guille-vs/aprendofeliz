# Aprendo Feliz · landing

Landing pública del producto. Astro, salida estática, sin backend ni sesión.

## Arranque rápido

```bash
npm install
npm run dev
```

Abre `http://localhost:4321`.

## Despliegue con Docker Compose

```bash
docker compose up -d --build
```

En local, `docker-compose.override.yml` publica el sitio en `http://localhost:8080`
(se carga automáticamente salvo que se pase `-f docker-compose.yaml` explícito, que es
como se despliega en el servidor — ver comentarios en `docker-compose.yaml`).

Este repo todavía no forma parte de la topología de despliegue del harness
(`globalsone-learning-harness`, ADR 008): falta decidir a qué dominio sirve. Por ahora
es solo el entorno base para empezar a trabajar en el contenido.

## Despliegue en Coolify (producción)

`docker-compose.prod.yml` se conecta a la red externa `coolify` con el alias
`learning-landing`, para que el proxy (Nginx Proxy Manager) la alcance por nombre. En
Coolify: Build Pack "Docker Compose", Location `/docker-compose.prod.yml`.

Probado en local:

```bash
docker network create coolify   # si no existe ya
docker compose -f docker-compose.prod.yml up -d --build
```
