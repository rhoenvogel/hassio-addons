FROM ghcr.io/home-assistant/aarch64-base:3.18

# Tools + aktuelles Go
RUN apk add --no-cache git wget \
 && wget https://go.dev/dl/go1.24.0.linux-arm64.tar.gz \
 && tar -C /usr/local -xzf go1.24.0.linux-arm64.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

# Dein Fork builden
RUN git clone https://github.com/rhoenvogel/noah-mqtt-cvo /app \
 && cd /app \
 && go build -o /noah-mqtt

# Entrypoint
COPY rootfs/docker-entrypoint.sh /
RUN chmod a+x /noah-mqtt && chmod a+x /docker-entrypoint.sh

ENTRYPOINT [ "/docker-entrypoint.sh" ]
