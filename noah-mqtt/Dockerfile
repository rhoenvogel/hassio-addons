FROM ghcr.io/home-assistant/aarch64-base:3.1

COPY config.json /

# Tools installieren
RUN apk add --no-cache git go

# Deinen Fork holen und bauen
RUN git clone https://github.com/rhoenvogel/noah-mqtt-cvo /app \
 && cd /app \
 && go build -o /noah-mqtt

# Entrypoint
COPY rootfs/docker-entrypoint.sh /
RUN chmod a+x /noah-mqtt && chmod a+x /docker-entrypoint.sh

ENTRYPOINT [ "/docker-entrypoint.sh" ]
