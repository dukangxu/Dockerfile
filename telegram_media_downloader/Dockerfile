FROM python:3-alpine
LABEL name="i" email="i@dukangxu.com"

RUN apk update && apk upgrade && \
    apk add --no-cache bash git gcc g++ libffi-dev openssl-dev libtool && \
    git clone https://github.com/Dineshkarthik/telegram_media_downloader.git /app && \
    cd /app && touch media_downloader.session && \
    # sed -i 's/begin_import(config, pagination_limit=100)/begin_import(config, pagination_limit=10)/g' media_downloader.py && \
    pip install --upgrade pip setuptools && pip install -r requirements.txt && \
    apk del gcc g++ libffi-dev openssl-dev libtool


WORKDIR /app

CMD [ "python", "/app/media_downloader.py" ]