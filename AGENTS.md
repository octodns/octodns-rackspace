# Developer Agent Guide for octoDNS Rackspace Provider

This repository contains the Rackspace provider for octoDNS. It enables planning, syncing, and applying DNS record states directly to the Rackspace Cloud DNS API.

> [!IMPORTANT]
> **Core Workflow and Guidelines**
>
> All agents working on this repository must read and follow the general instructions and workflow guidelines defined in the core octoDNS `AGENTS.md` file.
> - **Local check**: Look for the file at `../octodns/AGENTS.md`.
> - **Remote check**: If the local file is not available, fetch it from GitHub: [octoDNS Core AGENTS.md](https://github.com/octodns/octodns/raw/refs/heads/main/AGENTS.md).
>
> You must align your code structure, style, pull request guidelines, and overall development workflows with the instructions specified there.

## Repository & Module Information

### Key Components

- **Provider Class**: [RackspaceProvider](file:///home/ross/octodns/octodns-rackspace/octodns_rackspace/__init__.py) (defined in [octodns_rackspace/__init__.py](file:///home/ross/octodns/octodns-rackspace/octodns_rackspace/__init__.py)). This is the core provider communicating with Rackspace Cloud DNS API.
- **Authentication**: Authentication is handled through Rackspace username and API key (`username`, `api_key`).
- **API Communication**: Uses Python `requests` Session with pagination (using pagination key `records` or `domains`) and handles rate-limit delays (`ratelimit_delay`).

### Key Workflows & Features

1. **Supported Record Types**: `A`, `AAAA`, `ALIAS`, `CNAME`, `MX`, `NS`, `PTR`, `TXT`.
2. **Dynamic Routing Support**: Not supported (`SUPPORTS_GEO=False`, `SUPPORTS_DYNAMIC=False`).
3. **Pool Value Status**: Not supported (`SUPPORTS_POOL_VALUE_STATUS=False`).

## Development & Testing

- **Setup Script**: Run `./script/bootstrap` to create a virtual environment, install runtime and development dependencies (including `black`, `isort`, `pyflakes`, and `pytest`), and configure pre-commit hooks.
- **Test Suite**: Run unit tests using `pytest` via `./script/test` (or `pytest tests/`). Test files are located in [tests/](file:///home/ross/octodns/octodns-rackspace/tests).
- **Code Coverage**: Verify code coverage using `./script/coverage`.

## Key Constraints & Behaviors

- **Python Version**: Targets Python `>=3.9`.
- **Formatting**: Code formatting is enforced via `black` (version `>=26.0.0,<27.0.0`) and `isort`.
