FROM ubuntu:24.04 AS fse4ai_01

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

RUN apt-get update && \
    apt-get install -y --no-install-recommends unzip ca-certificates && \
    rm -rf /var/lib/apt/lists/*

COPY 02_lab_tasks.ipynb 02_class_tasks.ipynb /workspace/
COPY practical2.zip /workspace/

RUN unzip -q practical2.zip && \
    rm practical2.zip
WORKDIR /workspace/practical2.zip

# Default shell
CMD ["/bin/bash"]
