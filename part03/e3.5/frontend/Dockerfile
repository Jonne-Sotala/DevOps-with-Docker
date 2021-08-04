FROM alpine:3.13

EXPOSE 5000

WORKDIR = /usr/app/src

COPY . . 

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN apk add --no-cache --update nodejs npm && \
    npm install && \
    npm run build && \
    npm install -g serve && \
    ls | grep -v build | xargs rm -rf && \
    adduser -D user

USER user

CMD ["serve", "-s", "-l", "5000", "build"]
