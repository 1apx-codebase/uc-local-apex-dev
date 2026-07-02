---
title: Podman on macOS
description: Install and start Podman on macOS for UC Local APEX Dev.
sidebar:
    order: 10
---

Use this guide if you want to run UC Local APEX Dev with Podman on macOS. Podman is a container runtime that can run the Oracle Database and ORDS containers used by this project.

## Contents

- [Prerequisites](#prerequisites)
- [Install Podman](#install-podman)
- [Test Podman](#test-podman)
- [Run This Project with Podman](#run-this-project-with-podman)
- [Troubleshooting](#troubleshooting)
- [After a Restart](#after-a-restart)

## Prerequisites

This section installs the command-line tools used by the project.

1. Install Homebrew from [brew.sh](https://brew.sh/) if it is not installed.
2. Install Docker command-line tools, Compose, and SQLcl.

   ```bash
   brew install docker docker-compose sqlcl
   ```

3. Add SQLcl to your shell `PATH`.

   ```bash
   SQLCLPATH=$(ls -t $(brew --prefix)/Caskroom/sqlcl | head -1)
   PATH=$(brew --prefix)/Caskroom/sqlcl/$SQLCLPATH/sqlcl/bin:$PATH
   ```

For more SQLcl details, see [Install SQLcl with Homebrew on macOS](https://hartenfeller.dev/blog/sqlcl-homebrew-macos).

## Install Podman

This section installs Podman and creates the Podman virtual machine.

1. Install Podman.

   ```bash
   brew install podman
   ```

2. Create the Podman machine.

   ```bash
   podman machine init
   ```

3. Set the recommended resources.

   ```bash
   podman machine set --memory 4096
   podman machine set --cpus 3
   ```

4. Start the Podman machine.

   ```bash
   podman machine start
   ```

5. If Podman tells you to install the system helper service, run the commands shown by Podman. Then stop and start the Podman machine again.

## Test Podman

This section confirms that Podman can list containers.

1. Run:

   ```bash
   podman ps
   ```

2. Confirm that the command finishes without an error.

## Run This Project with Podman

This section explains how UC Local APEX Dev chooses Podman.

The project scripts, including `install.sh` and `local-26ai.sh`, detect Podman automatically when Docker is not installed. If both Docker and Podman are installed, force Podman with `CONTAINER_CLI`.

```bash
CONTAINER_CLI=podman ./install.sh
```

Use native Podman Compose commands when you run Compose directly.

| Name | Description |
| --- | --- |
| `podman compose up -d` | Starts the containers. |
| `podman compose stop` | Stops the containers. |
| `podman ps` | Lists containers. |

> **Important**
> Use the `podman compose` subcommand. Do not use the standalone `podman-compose` package for this project because it may not support everything in `docker-compose.yml`.

## Troubleshooting

This section lists common Podman setup problems on macOS.

| Name | Description |
| --- | --- |
| Docker-compatible socket does not work | Follow Podman's guide for the `DOCKER_HOST` environment variable: [Using the Docker host environment variable](https://podman-desktop.io/docs/migrating-from-docker/using-the-docker_host-environment-variable). |
| `docker-credential-desktop` is missing | Rename or remove `~/.docker/config.json` if the error mentions `docker-credential-desktop`. |
| Compose command fails | Use `podman compose`, not `podman-compose`. |

## After a Restart

This section explains how to restart Podman after you restart your Mac.

1. Start the Podman machine.

   ```bash
   podman machine start
   ```

2. Start UC Local APEX Dev.

   ```bash
   local-26ai.sh start
   ```

Before you stop the Podman machine, stop the database cleanly.

```bash
local-26ai.sh stop
podman machine stop
```
