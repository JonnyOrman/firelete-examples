ARG GO_VERSION=1.18

FROM golang:${GO_VERSION}-alpine AS builder

RUN apk update && apk add alpine-sdk git && rm -rf /var/cache/apk/*

RUN go env -w GOPRIVATE=github.com/jonnyorman/firelete

ARG GITHUB_USERNAME
ARG GITHUB_GO_GET_PAT

COPY . /example

WORKDIR /example

RUN git config --global credential.helper store && echo https://${GITHUB_USERNAME}:${GITHUB_GO_GET_PAT}@github.com > ~/.git-credentials

RUN go mod download

RUN go build -o ./example ./main.go

EXPOSE 8080

ENTRYPOINT ["./example"]