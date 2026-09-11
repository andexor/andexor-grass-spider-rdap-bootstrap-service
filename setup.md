<!--
SPDX-License-Identifier: Apache-2.0
Copyright 2026 Andexor Network, Inc.
Author: Ed Jenkins<ed@andexor.net>
-->

# Install Pre-requisites

Most projects have certain pre-requisites that are required for development, testing, or running in production. Install the ones that are needed.

## Python

Follow these instructions to setup a development environment for projects that are written in Python. The latest Python interpreter should already be installed on your system.

For projects written in Python, you need to use the uv package manager to install the third-party modules they depend on. uv is not available in a standard OS package format. It needs to be installed via this script.

> Run `install-uv.sh`

Do not use npm, npx, pip, pnpm, or other legacy tools like them. They have fundamental vulnerabilities that have been addressed by uv.

In order to protect against using malicious code, a 1 week delay is suggested between when a package is published and when it is used. Most security issues are resolved within this time frame.

Add this to the `pyproject.toml` file in your project:

> [tool.uv]<br/>
> exclude-newer = "1 week"

Install the Python packages that this project uses.

> Run `setup.sh`<br/>
> Run `uv sync`

## PlantUML

Some of the documentation is built with PlantUML.
This is only needed for development,
not for production.

Use PlantUML to render `.puml` files as `.png` images
during the build process.

This requires the following steps to be taken
in a development environment.

**Step 1**: Install SDKMan.

> `curl -s "https://get.sdkman.io" | bash`

Close the terminal window and open a new one.

> `exit`

**Step 2**: Install Java.

First, find the latest Temurin release,
not including beta releases.

> `sdk list java`

Once you find a good candidate, install it.
This example is the latest version available at the time of this writing.
You might find a newer release.

> `sdk install java 26.0.2+1.1-tem`

**Step 3**: Install graphviz.

> `sudo apt install -y graphviz graphviz-doc graphviz-tools`

**Step 4**: Install the PlatUML plugin for VS Code.

> Ctrl+Shift+P<br/>
> ext install well-ar.plantuml

Close the window.

Re-open the project.

Now you will be able to preview
rendered UML diagrams in the IDE.

## TypeScript

For projects written in TypeScript, you need to use Bun for package management, builds, and execution. It needs to be installed from this script.

> Run `install-bun.sh`

## Docker

For projects that are built in Docker or run in Docker, you need to have Docker properly installed.

> Run `install-docker.sh`

This script requires a reboot, so the system will be rebooted automatically.
After rebooting, run this to verify that it is working:

> Run `docker run hello-world`

## RabbitMQ

If you want to run RabbitMQ for local testing,

> Run `install-rabbitmq-server.sh`
