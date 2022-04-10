FROM caddy:builder-alpine AS builder

RUN apk add --no-cache upx && \
    xcaddy build \
    --with github.com/abiosoft/caddy-exec \
    --with github.com/caddy-dns/cloudflare \
    --with github.com/caddy-dns/dnspod \
    --with clevergo.tech/caddy-dnspodcn \
    --with github.com/kirsch33/realip \
    --with github.com/mholt/caddy-webdav \
    --with github.com/caddyserver/replace-response && \
    upx /usr/bin/caddy

FROM caddy:alpine
LABEL name="i" email="i@dukangxu.com"

RUN apk add --no-cache git bash

COPY --from=builder /usr/bin/caddy /usr/bin/caddy