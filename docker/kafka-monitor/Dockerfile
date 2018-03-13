FROM openjdk:8-jre-alpine

RUN apk --update add tar bash libstdc++ bind-tools && \
    rm -rf /tmp/* /var/cache/apk/*

ADD https://github.com/kelseyhightower/confd/releases/download/v0.15.0/confd-0.15.0-linux-amd64 /usr/local/bin/confd

COPY kafka-monitor.tgz /
RUN tar -zxf  kafka-monitor.tgz -C / && \
    rm -f kafka-monitor.tgz

COPY config /kafka-monitor/config

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh && \
    chmod +x /usr/local/bin/confd


ENTRYPOINT [ "/entrypoint.sh" ]
