# syntax=docker/dockerfile:1

FROM python:3.11-slim-bookworm

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"
LABEL org.opencontainers.image.source="https://github.com/skolai/fse4ai_2025"

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        unzip \
        ca-certificates && \
    \
    pip install --no-cache-dir notebook ipykernel && \
    \
    rm -rf /var/lib/apt/lists/*

ADD 02_lab_tasks.ipynb 02_class_tasks.ipynb ./
ADD practical2.zip ./

RUN unzip -q practical2.zip && \
    mv "practical 2"/* . && \
    rm -rf "practical 2" && \
    rm practical2.zip

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--no-browser"]