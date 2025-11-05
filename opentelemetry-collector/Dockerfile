FROM ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-contrib:0.139.0 AS opentelemetry

FROM debian:13-slim

RUN groupadd --system --gid 10001 opentelemetry && \
    useradd --system --uid 10001 --gid opentelemetry opentelemetry

RUN usermod -aG systemd-journal opentelemetry

ENV DEBIAN_FRONTEND=noninteractive 
ENV TZ=Europe/Amsterdam

RUN apt update && \
  apt install systemd -y

COPY --from=opentelemetry /otelcol-contrib /otelcol-contrib

USER opentelemetry

ENTRYPOINT ["/otelcol-contrib"]
CMD ["--config", "/etc/otelcol-contrib/config.yaml"]
