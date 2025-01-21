# Pulse Development Guide

## Introduction and rationale

The following are a set of informal, optional guidelines and best practices that, if followed, will help to simplify integration of new functionality into the existing Pulse platform. These guidelines are considered optional because it is understood that researchers need to be free to focus on the topic of their research and often have to deliver research results in compressed timescales. Following strict development rules could become a hindrance to progress and timely delivery. Nevertheless, early adoption of the following practices in development work that has potential for integration with Pulse will help to reduce the time required and work involved in integrating the new functionality with the existing Pulse platform.

Topics below are listed in rough priority order and ease of implementation.

*Any researchers interested in learning more about the architecture, development and deployment practices used by the Pulse dev team are always welcome to meet with the team. The team are always happy to provide guidance on implementing anything listed here.*

## Logging

Pulse uses the [Python logging library](https://docs.python.org/3/library/logging.html) for all debug and error logging.

## Pulse data platform components

The Pulse data platform is built using Python 3.10.* and the [Django framework](https://www.djangoproject.com/). Additionally, it uses [Celery](https://docs.celeryq.dev/en/stable/index.html) and [RabbitMQ](https://www.rabbitmq.com/docs) for running data gathering tasks, and [Django Ninja](https://django-ninja.dev/) for the API.

## Database

Pulse frontend and backend servers rely on PostgreSQL for their database functionality.

## Tests

Pulse uses the [pytest](https://docs.pytest.org/en/stable/) framework for testing.

## Ruff: pre-commit/linting/formatting

Pulse code repositories use the [pre-commit](https://pre-commit.com/) framework to perform linting and other checks during development. These include code formatting and import sorting with [ruff](https://docs.astral.sh/ruff/), and detecting any private keys you may have accidentally added to the repository. For a full list see the  `.pre-commit-config.yaml` included in this repo. Use of [pre-commit](https://pre-commit.com/) in your repo with the Pulse config.yaml will help to minimise formatting issues during integration.

Run pre-commit install to set up the git hook scripts

```
$ pre-commit install
```

Now pre-commit will run automatically on git push.

## Django Libraries

Pulse makes use of [django-countries-hdx](https://github.com/InternetSociety/django-countries-hdx) to add extra M49 data to django-countries.
It uses hdx-python-country with the default data augmented by more UN data to provide SIDS, LLDC and LDC grouping data.

Pulse makes use of [django-ixp-tracker](https://github.com/InternetSociety/django-ixp-tracker) which may be of interest if your project is related to IXP deployment.

## Documenting data sources

Pulse automatically generates documentation regarding data sources and measurement frequency based on the Django models used by the various apps.
Include `:source:` and `:source measurement frequency:` in the docstring for the relevant class

```
class RoutingIncidents(models.Model):
    """Routing incidents per country

    :source: MANRS (https://docs.manrs.org/api/#tag/aggregates/GET/countries/scores/{country})
    :source measurement frequency: Monthly
    """
```

