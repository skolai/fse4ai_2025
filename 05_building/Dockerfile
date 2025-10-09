# syntax=docker/dockerfile:1.4

# Start from the official Jupyter image which is pre-configured and stable.
FROM jupyter/base-notebook:python-3.11

# Switch to the root user to install system-level packages.
USER root

# Set environment variables to prevent interactive prompts during installation.
ENV DEBIAN_FRONTEND=noninteractive \
    TZ=Europe/Moscow

# Install all necessary system dependencies for C++ development with CGAL.
# This includes the compiler, build tools, and required libraries like Boost.
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        cmake \
        libcgal-dev \
        libgmp-dev \
        libmpfr-dev \
        libboost-thread-dev \
        unzip \
    && rm -rf /var/lib/apt/lists/*

# Switch back to the standard, non-root user for security and compatibility.
USER ${NB_UID}

# Copy your project files into the user's home directory and set ownership.
COPY --chown=${NB_UID}:${NB_GID} practical_5_building_software.zip .
COPY --chown=${NB_UID}:${NB_GID} 05_lab_tasks.ipynb 05_class_tasks.ipynb ./

# Unzip the source code into the current directory and clean up the zip file.
RUN unzip -q practical_5_building_software.zip && \
    mv practical_5_building_software/* . && \
    rm -rf practical_5_building_software && \
    rm practical_5_building_software.zip

# The base image already configures and runs the Jupyter notebook,
# so we don't need to add EXPOSE or CMD instructions.

