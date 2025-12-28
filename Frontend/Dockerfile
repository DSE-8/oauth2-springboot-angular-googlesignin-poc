FROM node:18

WORKDIR /app

# Copia package.json y package-lock.json
COPY ./ag-prueba-front/package*.json ./
RUN npm install

# Copiar el resto del frontend
COPY ./ag-prueba-front ./

# Crear build de producción Angular
RUN npm run build \
&& npm install -g serve

EXPOSE 4200

CMD ["serve", "-s", "dist/ag-prueba-front"]
