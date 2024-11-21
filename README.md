# examenerikavilla

 
#Archivo de docker que por problemas del github no se subió 
# Imagen base de Debian
FROM debian:latest

RUN apt-get update && apt-get install -y \
apache2 \
nodejs \
npm \
&& apt-get clean

RUN npm install -g @angular/cli

WORKDIR /usr/src/app

COPY ./angular-app /usr/src/app

RUN npm install && ng build --prod

RUN cp -r /usr/src/app/dist/* /var/www/html/

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]


