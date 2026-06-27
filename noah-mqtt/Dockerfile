FROM ghcr.io/home-assistant/aarch64-base:3.18

# Tools installieren
RUN apk add --no-cache git go

# Deinen Fork klonen und bauen
RUN git clone https://github.com/rhoenvogel/noah-mqtt-cvo /app \
 && cd /app \
 && go build -o /noah-mqtt

# Entrypoint
COPY rootfs/docker-entrypoint.sh /
RUN chmod a+x /noah-mqtt && chmod a+x /docker-entrypoint.sh

ENTRYPOINT [ "/docker-entrypoint.sh" ]
