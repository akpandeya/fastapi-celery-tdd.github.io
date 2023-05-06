---
layout: post
title:  "Setting up local development using poetry"
date:   2023-05-06 15:17:22 +0200
categories: poetry
---
To use Poetry instead of pip, follow these steps to set up the project:

- Install Poetry if you haven't already by following the instructions [here](https://python-poetry.org/docs/#installation).

- Navigate to your project directory and run `poetry init` to create a new `pyproject.toml` file. You can accept the default values or provide custom inputs during the interactive setup.

- Add the required dependencies using the following commands:

```bash
poetry add fastapi
poetry add uvicorn
poetry add celery
poetry add pytest
poetry add httpx
```

These commands will automatically update the `pyproject.toml` file with the new dependencies.

Your `pyproject.toml` file should now look something like this:

```toml
[tool.poetry]
name = "fastapi-celery-tdd"
version = "0.1.0"
description = ""
authors = ["Your Name <your.email@example.com>"]

[tool.poetry.dependencies]
python = "^3.7"
fastapi = "^0.68.1"
uvicorn = "^0.15.0"
celery = "^5.1.2"
httpx = "^0.19.0"

[tool.poetry.dev-dependencies]
pytest = "^6.2.5"

[build-system]
requires = ["poetry-core>=1.0.0"]
build-backend = "poetry.core.masonry.api"
```

- To install the dependencies, run:

```bash
poetry install
```

This will create a virtual environment and install the dependencies specified in the `pyproject.toml` file.
