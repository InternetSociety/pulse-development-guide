# Pulse Development Guide

## Introduction and rationale

The following are a set of informal, optional guidelines and best practices that, if followed, will help to ease the burden when it comes to integrating new functionality into the existing Pulse platform. They are considered optional as it is understood that researchers need to be free to focus on the topic of their research and often have to deliver research results in compressed timescales. Following strict development rules could become a hindrance to progress and timely delivery. Nevertheless, early adoption of the following practices in development work that has potential for future integration with Pulse will help to reduce the time required and work involved in integrating the new functionality with the existing Pulse platform.

Any researchers interested in learning more about the architecture, development and deployment practices used by the Pulse dev team are always welcome to meet with the team to learn more. 

## Logging

## Database

Pulse frontend and backend servers rely on PostgreSQL for their database functionality.

## Django Libraries

## Tests

## Ruff: pre-commit/linting/formatting

Pulse code repositories use the [pre-commit](https://pre-commit.com/) framework to perform linting and other checks during development. These include code formatting and import sorting with [ruff](https://docs.astral.sh/ruff/), and detecting any private keys you may have accidentally added to the repository. For a full list see the file `<install-directory>/.pre-commit-config.yaml`.

Run pre-commit install to set up the git hook scripts

```
$ pre-commit install
```

Now pre-commit will run automatically on git push.

