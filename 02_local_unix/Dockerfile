# syntax=docker/dockerfile:1

FROM ubuntu:24.04 AS fse4ai_01

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"
LABEL org.opencontainers.image.source="https://github.com/skolai/fse4ai_2025"

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

RUN apt-get update && \
    apt-get install -y --no-install-recommends unzip ca-certificates && \
    rm -rf /var/lib/apt/lists/*

ADD 02_lab_tasks.ipynb 02_class_tasks.ipynb ./

ADD practical2.zip ./

RUN unzip -q practical2.zip && \
    rm practical2.zip

CMD ["/bin/bash"]