# examenerikavilla
#Archivo de docker que por problemas del github no se subió 
#Debe ser puesto en la carpeta principal dentro del angular-app

#Imagen base de Debian
FROM debian:latest

#Actualización de paquetes y herramientas necesarias
RUN apt-get update && apt-get install -y \
apache2 \
nodejs \
npm \
&& apt-get clean

#Instalar Angular CLI globalmente
RUN npm install -g @angular/cli

#Crear directorios para la aplicación Angular
WORKDIR /usr/src/app

#Copiar los archivos de la aplicación al contenedo

COPY ./angular-app /usr/src/app

#Construir la aplicación Angular
RUN npm install && ng build --prod

# Configurar Apache para servir archivos estáticos de Angular
RUN cp -r /usr/src/app/dist/* /var/www/html/

#Exponer el puerto 80
EXPOSE 80

#Iniciar Apache en modo foreground
CMD ["apachectl", "-D", "FOREGROUND"]


