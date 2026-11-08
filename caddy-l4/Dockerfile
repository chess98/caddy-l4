ARG CADDY_VERSION=2.11.7
FROM caddy:${CADDY_VERSION}-builder AS build

ARG CADDY_VERSION
ARG CADDY_L4_VERSION=v0.1.2

RUN xcaddy build "v${CADDY_VERSION}" \
      --with "github.com/mholt/caddy-l4@${CADDY_L4_VERSION}" \
      --output /usr/bin/caddy

FROM caddy:${CADDY_VERSION}-alpine

ARG CADDY_VERSION
ARG CADDY_L4_VERSION

COPY --from=build /usr/bin/caddy /usr/bin/caddy
RUN caddy version && caddy list-modules | grep -qx layer4

ENTRYPOINT ["caddy"]
CMD ["run", "--config", "/etc/caddy/Caddyfile"]
