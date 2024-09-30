# Usa una imagen base oficial de Nginx
FROM nginx:latest

# Instala Node.js y NPM
RUN apt-get update && \
    apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y nodejs

# Instala Jest y JSDOM para pruebas
RUN npm install --save-dev jest jsdom

# Copia el archivo de configuración de Nginx al contenedor
COPY default.conf /etc/nginx/conf.d/default.conf

# Copia el contenido de la aplicación (por ejemplo, archivos HTML) al directorio
