# syntax=docker/dockerfile:1

FROM ubuntu:24.04 AS fse4ai_01

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"
LABEL org.opencontainers.image.source="https://github.com/skolai/fse4ai_2025"

ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

# Install system packages, including Python and Pip
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        unzip \
        ca-certificates \
        python3 \
        python3-pip \
        python3-venv && \
    \
    # Install Jupyter and the Python kernel using pip
    python3 -m pip install --no-cache-dir notebook ipykernel && \
    \
    # Clean up apt cache to keep image small
    rm -rf /var/lib/apt/lists/*

ADD 01_lab_tasks.ipynb 01_class_tasks.ipynb ./
ADD practical_1_unix_local_machine_1.zip ./

RUN unzip -q practical_1_unix_local_machine_1.zip && \
    mv practical_1_unix_local_machine_1/* . && \
    rm -rf practical_1_unix_local_machine_1 && \
    rm practical_1_unix_local_machine_1.zip

# Expose the default Jupyter port
EXPOSE 8888

# Start the Jupyter Notebook server by default
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--no-browser"]