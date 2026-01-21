# Software Koppeling Connector Template

This repository is a Copier template for creating new software-koppeling connector packages.
It generates a ready-to-use Python package layout, `pyproject.toml`, and a GitHub Actions
workflow for building and pushing a Docker image.

Repository: https://github.com/software-koppeling/software-koppeling-connector-template

## Prerequisites

- Python 3.12+
- [uv](https://github.com/astral-sh/uv)
- [copier](https://copier.readthedocs.io/)

Install tools:

```bash
uv tool install copier
```

## Create a new package

From anywhere, run:

```bash
copier copy https://github.com/software-koppeling/software-koppeling-connector-template my-connector
```

Copier will ask for:

- `package_name` (used in `pyproject.toml`)
- `package_description`
- `version`
- `author_name`
- `author_email`
- `python_requires`

The Python module path is generated from `package_name` by lowercasing and replacing `-` with `_`.

Example:

- `package_name`: `software-koppeling-connector-foo`
- module path: `src/software_koppeling_connector_foo`

## Install dependencies

```bash
cd my-connector
uv sync
```

## GitHub Actions

The template includes a workflow at `.github/workflows/docker.yml` that:

- builds a Docker image
- pushes to GHCR on `main` and tags starting with `v`
- tags `acceptatie` on `main`
- tags `prod` and the version on releases

## Update a generated project

From inside the generated project:

```bash
copier update
```
