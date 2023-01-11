#Elegimos la imagen de nginx .
FROM nginx:1.23.3

WORKDIR /

#Copiamos el index.html dentro del contenedor
COPY ./html /usr/share/nginx/html

#Exponemos el puerto por default de nginx
EXPOSE 80