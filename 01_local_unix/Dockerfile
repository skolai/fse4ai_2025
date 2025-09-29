# syntax=docker/dockerfile:1

# Start from an official, slim Python image
FROM python:3.11-slim-bookworm

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"
LABEL org.opencontainers.image.source="https://github.com/skolai/fse4ai_2025"

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

# Install system dependencies and Jupyter in one layer
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        unzip \
        ca-certificates && \
    \
    # Install Jupyter using the pre-installed pip
    pip install --no-cache-dir notebook ipykernel && \
    \
    # Clean up apt cache
    rm -rf /var/lib/apt/lists/*

ADD 01_lab_tasks.ipynb 01_class_tasks.ipynb ./
ADD practical_1_unix_local_machine_1.zip ./

RUN unzip -q practical_1_unix_local_machine_1.zip && \
    mv practical_1_unix_local_machine_1/* . && \
    rm -rf practical_1_unix_local_machine_1 && \
    rm practical_1_unix_local_machine_1.zip

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--no-browser"]