FROM golang:alpine AS build-env

WORKDIR /go/src/app

COPY . .

ENV CGO_ENABLED=0

RUN go build && \
    adduser -D user

FROM scratch

EXPOSE 8080

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost

WORKDIR /go/src/app

COPY --from=build-env /go/src/app /go/src/app
COPY --from=build-env /etc/passwd /etc/passwd

USER user

ENTRYPOINT [ "./server" ]
