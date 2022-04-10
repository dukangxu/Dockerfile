# caddy-docker
caddy with common plug-in

## build
```bash
docker build --no-cache -t dukangxu/caddy https://github.com/dukangxu/Dockerfile.git#master:caddy
```

## plugins
* github.com/abiosoft/caddy-exec
* github.com/caddy-dns/cloudflare
* github.com/caddy-dns/dnspod
* clevergo.tech/caddy-dnspodcn
* github.com/kirsch33/realip
* github.com/mholt/caddy-webdav
* github.com/caddyserver/replace-response