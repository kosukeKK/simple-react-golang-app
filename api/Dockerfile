FROM golang:1.14.4-alpine3.11 AS build-env

ENV GO111MODULE=on

RUN apk --no-cache add git make build-base

WORKDIR /go/src/app

COPY . .

RUN mkdir -p /build
RUN go build -a -tags "netgo" -installsuffix netgo -ldflags="-s -w -extldflags \"-static\"" -o=/build/app main.go

FROM alpine:3.10.2
# Timezone = Tokyo
RUN apk --no-cache add tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

COPY --from=build-env /build/app /build/app
RUN chmod u+x /build/app

