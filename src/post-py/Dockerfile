FROM alpine:3.7 AS first

WORKDIR /app
ADD . /app

RUN apk add --update --no-cache --virtual tmp gcc musl-dev python python-dev py-pip python3 python3-dev \
    && pip3 install --user --no-cache-dir -r /app/requirements.txt \
    && apk del tmp \
    && apk add --no-cache python3

ENV POST_DATABASE_HOST post_db
ENV POST_DATABASE posts

ENTRYPOINT ["python3", "post_app.py"]

