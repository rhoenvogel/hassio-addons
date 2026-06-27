FROM ghcr.io/home-assistant/aarch64-base:3.18

# Arbeitsverzeichnis sicher setzen
WORKDIR /

# Tools + Go 1.24 installieren
RUN apk add --no-cache git wget \
    && wget https://go.dev/dl/go1.24.0.linux-arm64.tar.gz \
    && tar -C /usr/local -xzf go1.24.0.linux-arm64.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

# Dein (gepatchtes) Repo klonen und bauen
RUN git clone https://github.com/rhoenvogel/noah-mqtt-cvo /app \
    && cd /app/cmd/noah-mqtt \
    && go build -o /noah-mqtt

# config.json für den Entrypoint bereitstellen
COPY config.json /config.json

# Entrypoint kopieren
COPY rootfs/docker-entrypoint.sh /docker-entrypoint.sh

RUN chmod a+x /noah-mqtt && chmod a+x /docker-entrypoint.sh

ENTRYPOINT [ "/docker-entrypoint.sh" ]
