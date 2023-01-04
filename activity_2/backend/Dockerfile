#Elegimos la imagen en la cual se basa el contenedor
FROM python:3.8-alpine

#Elegimos el directorio que utilizara dentro del contenedor
WORKDIR /app

#Instalo dependencias
RUN apk add gcc && apk add libc-dev &&\
    apk add libpq-dev && apk add python3-dev &&\
    apk add linux-headers && apk add musl-dev &&\
    apk add zlib && apk add zlib-dev &&\
    apk add graphviz && apk add graphviz-dev &&\
    apk add jpeg-dev

#Copiamos el archivo de requerimientos, y los instalamos
COPY ./requirements.txt ./requirements.txt
RUN pip3 install --upgrade pip &&\
    pip3 install cmake &&\
    pip3 install -r requirements.txt

#Copiamos los archivos de la carpeta raiz dentro de la carpeta raiz del contenedor
COPY . .

#Exponemos un puerto
EXPOSE 8000