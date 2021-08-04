FROM node:alpine AS build-env

WORKDIR /usr/src/app

COPY . .

RUN npm install -g serve && \
    npm install && \
    npm run build

FROM alpine:3.13

EXPOSE 5000

ENV REACT_APP_BACKEND_URL=http://localhost:8080

WORKDIR /usr/src/app

COPY --from=build-env /usr/src/app/build /usr/src/app/build

RUN apk add --no-cache --update nodejs npm && \
    npm install -g serve && \
    adduser -D user

USER user

ENTRYPOINT [ "serve", "-s", "-l", "5000", "build" ]
