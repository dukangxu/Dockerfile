FROM dukangxu/caddy
LABEL name="i" email="i@dukangxu.com"

ADD hook-blog.sh /exec/

RUN apk add --no-cache upx curl libc6-compat \
    && HUGO_VERSION=$(curl -sX GET "https://api.github.com/repos/gohugoio/hugo/releases/latest" | awk '/tag_name/{print $4}' FS='[""]' | sed 's/^.//g') \
    && wget -O /tmp/hugo.tar.gz https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz \
    && tar -xzf /tmp/hugo.tar.gz -C /tmp && mv /tmp/hugo /usr/bin/hugo \
    && upx /usr/bin/hugo && chmod +x /exec/hook-blog.sh \
    && rm -f /tmp/hugo.tar.gz /tmp/LICENSE /tmp/README.md