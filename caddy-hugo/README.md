# caddy-hugo-docker
caddy with hugo

## build
```bash
docker build --no-cache -t dukangxu/caddy-hugo https://github.com/dukangxu/Dockerfile.git#master:caddy-hugo
```

## config
config with Caddyfile
```Caddyfile
handle {
    root * /srv/public/blog
}
file_server

route /hook/blog {
    basicauth {
        hookblog JDJhJDE0JHJNSkMxQnd6endtQ1BvN100000000000000000000000000000000000000000000000000
    }
    exec bash /exec/hook-blog.sh {
        timeout 120s
    }
}
```

config with docker-compose
```yaml
version: '3'
services:
  caddy:
    image: dukangxu/caddy-hugo
    container_name: caddy
    ports:
      - 80:80
      - 443:443
    environment:
      - REPOSITORY=https://github.com/dukangxu/example.git
    volumes:
...
```