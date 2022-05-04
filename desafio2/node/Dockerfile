FROM node:18 AS builder

WORKDIR /usr/src/app
COPY index.js .
RUN npm init -y && npm install express && npm install mysql2 --save

FROM node:18-alpine

WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/ ./

RUN apk add --no-cache openssl

ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz

EXPOSE 3000
# CMD ["node","index.js"]