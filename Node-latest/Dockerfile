FROM hongkongkiwi/alpine-node-docker:node-latest

MAINTAINER Andy Savage <andy@savage.hk>

LABEL org.label-schema.name="docker-node-docker-supercronic" \
      org.label-schema.description="Useful base docker image which includes a base system with Node.js, Docker & Supercronic" \
      org.label-schema.vcs-url="https://github.com/hongkongkiwi/docker-alpine-node-supercronic" \
      org.label-schema.license="MIT"

ARG OS="linux"
ARG ARCH="amd64"

ARG SUPERCRONIC_VER="0.1.5"
ARG SUPERCRONIC_URL="https://github.com/aptible/supercronic/releases/download/v${SUPERCRONIC_VER}/supercronic-${OS}-${ARCH}"
ARG SUPERCRONIC='supercronic-${OS}-${ARCH}'
ARG SUPERCRONIC_SHA1SUM=9aeb41e00cc7b71d30d33c57a2333f2c2581a201

RUN echo "Installing Supercronic" \
 && curl -fsSLO "$SUPERCRONIC_URL" \
 && echo "${SUPERCRONIC_SHA1SUM} ${SUPERCRONIC}" | sha1sum -c - \
 && chmod +x "$SUPERCRONIC" \
 && mv "$SUPERCRONIC" "/usr/local/bin/${SUPERCRONIC}" \
 && ln -s "/usr/local/bin/${SUPERCRONIC}" "/usr/local/bin/supercronic" \
 && rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/local/bin/supercronic"]
