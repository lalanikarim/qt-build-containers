# Container environment for building Qt projects for Linux

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
