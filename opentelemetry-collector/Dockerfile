FROM ubuntu:latest AS ubuntu

ENV DEBIAN_FRONTEND=noninteractive 
ENV TZ=Europe/Amsterdam

RUN apt update && \
  apt install systemd -y

FROM ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-contrib:0.139.0

COPY --from=ubuntu /usr/bin/journalctl /usr/bin/journalctl
