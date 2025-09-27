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

ADD 01_lab_tasks.ipynb 01_class_tasks.ipynb ./

ADD practical_1_unix_local_machine_1.zip ./

RUN unzip -q practical_1_unix_local_machine_1.zip && \
    mv practical_1_unix_local_machine_1/* . && \
    rm -rf practical_1_unix_local_machine_1 && \
    rm practical_1_unix_local_machine_1.zip

CMD ["/bin/bash"]