FROM alpine:3.10
RUN apk add librdkafka-dev=1.4.0-r0 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community
RUN apk add tzdata && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone && \
    apk del tzdata