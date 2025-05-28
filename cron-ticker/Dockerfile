# /app/usr/lib
# FROM --platform=linux/amd64 node:19.2-alpine3.16 permite forzar una plataforma en la construccion

# $BUILDPLATFORM permite enviar varias plataformas en la construccion, ejm: 
# docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7,linux/arm/v8 -t diviercasas26/cron-ticker:latest --push .
FROM --platform=$BUILDPLATFORM node:19.2-alpine3.16 

#FROM node:19.2-alpine3.16

# cd app
WORKDIR /app

# Dest /app
# COPY app.js package.json ./
COPY . .
# El . copia todo el contenido del directorio relativo al dockerfile en el directorio de trabajo /app

# Instalar las dependencias
RUN npm install

# Eliminar archivos y directorios, ejm no necesarios en PROD
RUN rm -rf node_modules

# Unicamente las dependencias de PROD
RUN npm install --prod

# Comando run de la imagen
CMD ["node", "app.js"]