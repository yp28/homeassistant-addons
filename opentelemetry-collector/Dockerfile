FROM ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-contrib:0.139.0 AS opentelemetry

FROM debian:13-slim

ENV DEBIAN_FRONTEND=noninteractive 
ENV TZ=Europe/Amsterdam

RUN apt update && \
  apt install -y \
    systemd \
    ca-certificates

COPY --from=opentelemetry /otelcol-contrib /otelcol-contrib

ENTRYPOINT ["/otelcol-contrib"]
CMD ["--config", "/etc/otelcol-contrib/config.yaml"]
