# syntax=docker/dockerfile:1.4

FROM python:3.11-slim-bookworm

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"
LABEL org.opencontainers.image.source="https://github.com/skolai/fse4ai_2025"

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        cmake \
        libgmp-dev \
        libmpfr-dev \
        libboost-thread-dev \
        unzip \
        ca-certificates && \
    \
    pip install --no-cache-dir notebook ipykernel && \
    \
    rm -rf /var/lib/apt/lists/*

ADD practical_5_building_software.zip .
ADD 05_lab_tasks.ipynb 05_class_tasks.ipynb ./

RUN unzip -q practical_5_building_software.zip && \
    mv practical_5_building_software/* . && \
    rm -rf practical_5_building_software && \
    rm practical_5_building_software.zip

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--no-browser"]
