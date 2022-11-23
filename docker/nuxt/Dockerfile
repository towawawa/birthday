FROM node:14-alpine

# ソースコードのコピー
COPY . /app

WORKDIR /app

ENV HOST 0.0.0.0
EXPOSE 3000

RUN echo "ENV=$ENV"

RUN apk update && \
    npm install -g create-nuxt-app