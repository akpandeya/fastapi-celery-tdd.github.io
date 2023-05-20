---
layout: page
title: Project Setup
nav_order: 2
parent: Chapter 1 - Project Setup and Hello World API
---
In this project, we will be using Poetry as our package manager and dependency management tool, instead of pip. There are several reasons why we have chosen Poetry over pip:

1. **Dependency Resolution:** Poetry is designed to handle complex dependency resolution, ensuring that your project's dependencies are compatible with each other. This helps prevent issues that may arise from conflicting versions of packages, which can be a common problem when using pip.

2. **Simplified Dependency Management:** With Poetry, you can easily manage your project's dependencies using the `pyproject.toml` file. This file provides a clear, structured format for defining package dependencies, their versions, and other metadata about your project. This is a more modern and maintainable approach compared to the traditional `requirements.txt` file used with pip.

3. **Virtual Environment Management:** Poetry automatically creates and manages virtual environments for your projects, isolating dependencies for each project and keeping your system clean. This is an important feature to avoid potential conflicts between global and project-specific packages, which can be an issue when using pip without a virtual environment.

4. **Reproducible Builds:** Poetry locks the exact versions of your dependencies in a `poetry.lock` file, ensuring that your project can be built consistently across different environments. This makes it easier to share your project with other developers or deploy it to production with confidence.

5. **Streamlined Publishing:** Poetry simplifies the process of publishing your package to the Python Package Index (PyPI). With just a few commands, you can build, package, and distribute your project, making it easier for others to discover and use your work.

By using Poetry in our project, we can take advantage of its powerful features for dependency management, virtual environment management, and reproducible builds, which will help us create a more robust, maintainable, and collaborative web application.

To set up Poetry for our project and install all the necessary dependencies, follow these steps:

1. **Install Poetry:** If you haven't installed Poetry yet, you can follow the [official installation instructions](https://python-poetry.org/docs/#installation) for your operating system.

2. **Create a new project:** Navigate to the directory where you want to create your project and run the following command:

    ```bash
    poetry new my_project
    ```

    Replace `my_project` with the desired name for your project. This command will create a new directory with the specified name, containing a basic project structure.

3. **Navigate to the project directory:** Move to the newly created project directory:

   ```shell
   cd my_project
   ```

4. **Initialize Poetry:** Run the following command to initialize Poetry and create a `pyproject.toml` file with the necessary configurations:

   ```bash
   poetry init
   ```

   During the initialization process, Poetry will prompt you to enter some information about your project and its dependencies. You can provide the required information or simply press Enter to accept the default values. When prompted to add dependencies, you can either add them now or skip this step and manually add them in the `pyproject.toml` file later.

5. **Add dependencies:** Open the `pyproject.toml` file and add the required dependencies to the `[dependencies]` section:

   ```toml
    [dependencies]
    fastapi = "^0.68.1"
   ```

   Replace the version numbers with the latest versions of the packages.

6. **Add development dependencies:** In the same `pyproject.toml` file, add the development dependencies for linting to the `[tool.poetry.dev-dependencies]` section:

   ```toml
   [tool.poetry.dev-dependencies]
    pytest = "^6.2.5"
    pytest-watch = "^4.2.0"
    black = "^21.9b0"
    isort = "^5.10.0"
    flake8 = "^3.9.2"
   ```

   Replace the version numbers with the latest versions of the packages.

7. **Install dependencies:** Once you have added all the necessary dependencies, run the following command to install them:

   ```bash
   poetry install
   ```

By following these steps, you will have a fully configured Poetry project with all the required dependencies and development tools installed. With Poetry, managing your project's dependencies and development environment will be a breeze, allowing you to focus on building your web application using Test-Driven Development principles.
