---

title: B-Open technologies and best practices
subtitle: Technologies and best practices at B-Open in 2022
summary: At B-Open we try to keep up with the software development best practices and tooling,
  usually drawing from what larger Open Source projects are using successfully.
  Sometimes we need to adapt to the technological choices of our customers (JIRA comes to mind),
  but in 2022 we have several new projects starting up and most of them share a common
  set of technologies and best practices.
authors:
  - alexamici
tags:
  - best-practices
  - technologies
categories: []
projects: []
date: '2022-06-14T00:00:00Z'
---

At B-Open we try to keep up with the software development best practices and tooling,
often drawing from widely used and successful Open Source projects.
Sometimes we need to adapt to the technological needs of our customers (JIRA comes to mind),
but in 2022 we have several new projects starting up and most of them share a common
set of technologies and best practices.

The main differences with respect to the past year are:

- Kubernetes more or less everywhere (but still a lot of docker-compose)
- much more GitHub and GitHub Actions 🎊
- FastAPI has taken over most API development 
- Ansible has kicked Puppet out of the list of legacy tools we need to endure 🥳
- much less ReST in favour of MarkDown, but always with Sphinx

And here are the technologies for 2022. 

## Collaboration

1. Software project management: GitHub, GitLab, JIRA
1. Source control: Git
1. Documentation: MarkDown, Sphinx / MyST

## Python

1. Programming languages: Python 3.7+
1. Python installation tooling: Pip, Conda
1. Software testing: Pytest (unit testing), coverage.py (code coverage), Black (coding style), Mypy (type check)
1. Scientific stack: Numpy, Pandas, Jupyter notebook, Xarray, Dask, Dask.distributed, Scipy, Matplotlib, Plotly
1. Geospatial stack: GDAL / OGR, rasterio, QGIS
1. Web API stack: FastAPI, SQLAlchemy, Keycloak / WSO2

## System / DevOps

1. Operating Systems: Ubuntu Linux, CentOS Linux, MacOS, Windows.
1. Containers: Docker, Docker compose, Kubernetes
1. Cloud platforms: OpenStack, Google Cloud Platform, Microsoft Azure, Amazon Web Services
1. Deployment automation: Ansible, Terraform 
1. Continuous integration: GitHub Actions, GitLab CI/CD, pre-commit
1. Database: PostgreSQL / PostGIS

## JavaScript

1. Framework: React
1. Web mapping: Leaflet
1. End-to-end testing: Cypress
