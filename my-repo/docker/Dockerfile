# Usa una imagen base oficial de Nginx
FROM nginx:latest

# Instala Node.js, NPM y herramientas de compilación
RUN apt-get update && \
    apt-get install -y curl build-essential && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y nodejs && \
    apt-get install -y npm

# Verifica la instalación de node y npm
RUN node -v && npm -v

# Instala Jest y JSDOM para pruebas
RUN npm install --save-dev jest jsdom --unsafe-perm

# Copia el archivo de configuración de Nginx al contenedor
COPY default.conf /etc/nginx/conf.d/default.conf

# Copia el contenido de la aplicación (por ejemplo, archivos HTML) al directorio donde Nginx los servirá
COPY ./html /usr/share/nginx/html

# Exponer el puerto en el que Nginx está escuchando
EXPOSE 80

# Comando opcional para ejecutar pruebas durante la construcción del contenedor (solo para desarrollo, no producción)
RUN npm test || echo "Tests failed, but continuing..."

# Ejecuta Nginx cuando el contenedor se inicie
CMD ["nginx", "-g", "daemon off;"]
