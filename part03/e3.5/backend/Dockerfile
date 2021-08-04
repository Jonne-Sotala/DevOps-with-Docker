FROM golang:alpine as build-env

WORKDIR /go/src/app
COPY . . 

RUN go build

FROM alpine

EXPOSE 8080

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost

WORKDIR /go/src/app

COPY --from=build-env /go/src/app /go/src/app

RUN apk update && \
    apk add --no-cache ca-certificates && \
    adduser -D user 

USER user

ENTRYPOINT ["./server"]

