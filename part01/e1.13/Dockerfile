FROM golang:1.16

EXPOSE 8080
WORKDIR /go/src/app
COPY ./example-backend .

RUN go build
RUN go test ./...

ENV PORT=8080
ENV REQUEST_ORIGIN=https://example.com

CMD ["./server"]
