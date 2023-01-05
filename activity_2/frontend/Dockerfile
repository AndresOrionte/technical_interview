#Elegimos la imagen en la cual se basa el contenedor, en este caso una version alpine al ser mas livianas
FROM node:18-alpine

#Elegimos el directorio que utilizara dentro del contenedor
WORKDIR /frontend

#Copiamos los archivos de la carpeta raiz dentro del contenedor
COPY . .

#Instalacion de npm
RUN npm install -g

#Exposicion del puerto utilizado por React
EXPOSE 3000

#Corremos el server
CMD ["npm", "start"]