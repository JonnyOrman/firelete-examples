ARG GO_VERSION=1.18

FROM golang:${GO_VERSION}-alpine AS builder

RUN apk update && apk add alpine-sdk git && rm -rf /var/cache/apk/*

COPY . /example

WORKDIR /example

RUN go mod download

RUN go build -o ./example ./main.go

EXPOSE 8080

ENTRYPOINT ["./example"]