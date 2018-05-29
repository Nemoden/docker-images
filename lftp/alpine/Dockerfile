FROM alpine:3.7

RUN apk add --no-cache lftp && mkdir /volume

WORKDIR /volume

ENTRYPOINT ["lftp"]
