FROM grafana/promtail:main

RUN apt-get update && apt-get install -y --no-install-recommends wget jq bc curl dumb-init bash python3 procps coreutils sysstat net-tools && rm -rf /var/lib/apt/lists/*

RUN mkdir /sense-collector

COPY exec-device-details.sh \
exec-host-performance.sh \
exec-monitor-status.sh \
exec-sense-collector.sh \
sense-collector-details.sh \
start-device-details.sh \
start-host-performance.sh \
start-monitor-status.sh \
start-sense-collector.sh \
sense-collector-init.sh \
/sense-collector/

RUN wget -O /sense-collector/websocat_amd64-linux-static https://github.com/vi/websocat/releases/download/v1.13.0/websocat.x86_64-unknown-linux-musl

WORKDIR /sense-collector

RUN chmod a+x *.sh

RUN chmod +x websocat_amd64-linux-static


ENTRYPOINT ["/usr/bin/dumb-init", "--"]

CMD ["/sense-collector/sense-collector-init.sh"]
