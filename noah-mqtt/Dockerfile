FROM docker.io/library/node:18-alpine

# Git installieren
RUN apk add --no-cache git

# In ein temporäres Verzeichnis klonen und nach /app verschieben
RUN git clone https://github.com/rhoenvogel/noah-mqtt-cvo /tmp/noah \
    && mkdir -p /app \
    && cp -r /tmp/noah/. /app/ \
    && rm -rf /tmp/noah

# Erst JETZT in das Arbeitsverzeichnis wechseln
WORKDIR /app

# Dependencies installieren
RUN npm install

# Falls das Projekt in TypeScript geschrieben ist, muss es noch kompiliert werden:
RUN npm run build

# Startbefehl (Passe den Pfad an, falls die Startdatei woanders liegt, z.B. dist/index.js)
CMD ["node", "dist/index.js"]
