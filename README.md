# examenerikavilla

 # Angular en Docker con Apache

Este repositorio contiene la configuración necesaria para ejecutar una aplicación Angular dentro de un contenedor Docker usando Debian y Apache.

## Instrucciones

### Construir la Imagen
```bash
docker build -t angular-image .

## Ejecutar contenedor
docker run -d -p 80:80 angular-image

## Volúmenes 
docker run -d -p 80:80 -v $(pwd)/angular-app:/usr/src/app angular-image




