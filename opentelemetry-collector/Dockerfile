FROM ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-contrib:0.139.0 AS opentelemetry

FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive 
ENV TZ=Europe/Amsterdam

RUN apt update && \
  apt install systemd -y

COPY --from=opentelemetry /otelcol-contrib /otelcol-contrib

ARG USER_UID=10001
ARG USER_GID=10001
USER ${USER_UID}:${USER_GID}

ENTRYPOINT ["/otelcol-contrib"]
CMD ["--config", "/etc/otelcol-contrib/config.yaml"]
