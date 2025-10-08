# syntax=docker/dockerfile:1.4

# Use a slim Python image as the base
FROM python:3.11-slim-bookworm

LABEL maintainer="Aleksandr Mikhalev <al.mikhalev@skoltech.ru>"
LABEL org.opencontainers.image.source="https://github.com/skolai/fse4ai_2025"

# Set non-interactive frontend for package managers to prevent prompts
ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

WORKDIR /workspace

# Install all system dependencies (including C++ compilers) and Python packages in a single layer
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        cmake \
        libgmp-dev \
        libmpfr-dev \
        libboost-thread-dev \
        unzip \
    && pip install --no-cache-dir notebook ipykernel \
    && rm -rf /var/lib/apt/lists/*

# Copy the source code and notebooks into the image
ADD practical_5_building_software.zip .
ADD 05_lab_tasks.ipynb 05_class_tasks.ipynb ./

# Unzip the C++ source code into the current directory and clean up
RUN unzip -q practical_5_building_software.zip && \
    mv practical_5_building_software/* . && \
    rm -rf practical_5_building_software && \
    rm practical_5_building_software.zip

# Expose the default Jupyter Notebook port
EXPOSE 8888

# Start the Jupyter Notebook server, allowing access from outside the container
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root", "--no-browser", "--notebook-dir=/workspace"]

