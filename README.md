# Container environment for building Qt projects for Linux

## Overview

This repository provides containerized environments for building Qt applications on Linux. It includes Docker/Podman configurations for Ubuntu-based containers with Qt development tools pre-installed. This setup allows developers to:

- Build Qt projects in a consistent, isolated environment
- Avoid Qt installation issues on the host system
- Ensure reproducible builds across different development machines
- Easily switch between different Qt versions if needed

The containers mount your local Qt installation and project directories as volumes, allowing you to develop on your host machine while building in the container.


## Setup

1. Ensure you have docker/podman with compose capabilities.
2. Create `local-share-qt` and `opt-qt` subfolders.
3. Download and place `qt-online-installer-linux-x64-4.9.0.run` in the folder. 
3. (optional) Copy `qtaccount.ini` to `local-share-qt`.

## First Run

1. Build container services:
    ```sh
    docker compose build
    ```
2. Run Qt Installer in non-interactive mode:
    ```sh
    docker run ubuntu /root/install.sh
    ```

## Building your Qt project

1. Run a container service with your source tree attached as a volume:
    ```sh
    docker run -v ./example:/src/example ubuntu bash
    ```
2. Navigate to the source tree and run appropriate commands:
    ```sh
    cd /src/example
    qmake
    make
    ./example
    ```
