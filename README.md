# final-push

An inactivity-triggered release system powered by GitHub Actions.

This repository provides a template for automatically releasing predefined content after a prolonged period of GitHub inactivity.

It relies solely on public GitHub activity as a heartbeat signal and executes without external services.

## Use cases

-   Dead man's switch
-   Long-term project handoff
-   Lost-access contingency
-   Inactivity-based disclosure

## How it works

-   A scheduled GitHub Actions workflow runs daily
-   Public GitHub activity is checked via the GitHub API
-   Inactivity duration is calculated
-   If a configurable threshold is exceeded:
    -   A predefined payload is decrypted
    -   The payload is published to the repository

## Configuration

GitHub Action secrets keys are limited to 48KB.

## Abort conditions

Any of the following will prevent or reset the trigger:

-   New GitHub activity (for example, star or unstar any repository)
-   Manual state reset

## Security design

No assumptions are made about the user's state. Only inactivity is evaluated.

Fernet is used for convenience, not for long-term archival security.
