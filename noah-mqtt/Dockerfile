FROM node:18-alpine

# Arbeitsverzeichnis
WORKDIR /app

# Tools
RUN apk add --no-cache git

# Code holen
RUN git clone https://github.com/rhoenvogel/noah-mqtt-cvo .

# Dependencies installieren
RUN npm install

# TypeScript bauen
RUN npm run build

# Start
CMD ["node", "dist/index.js"]
