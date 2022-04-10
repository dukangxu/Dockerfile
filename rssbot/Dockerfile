FROM alpine:3.14
LABEL name="i" email="i@dukangxu.com"

WORKDIR /
RUN apk add --no-cache curl && \
    RSSBOT_VERSION=$(curl -sX GET "https://api.github.com/repos/iovxw/rssbot/releases/latest" | awk '/tag_name/{print $4}' FS='[""]' | sed 's/^.//g') && \
    wget --no-check-certificate https://github.com/iovxw/rssbot/releases/download/v${RSSBOT_VERSION}/rssbot-en-x86_64-unknown-linux-musl && \
    mkdir /app && mv rssbot-en-x86_64-unknown-linux-musl /app/rssbot && chmod +x /app/rssbot

ENTRYPOINT ["/app/rssbot"]
