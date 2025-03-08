# Technical Writing Guidelines

This document outlines the technical writing guidelines for Voedger projects and covers the following areas:

- Source code comments
- Requirements
- Design

## Capitalization

- Sentence capitalization **must** be used except for the documentation names (like "Technical Writing Guidelines")
- Terms that are defined in documentation **should** be capitalized

Correct:

- Technical Writing Guidelines
- This guide describes locking and row versioning mechanisms the Database Engine uses to ensure the integrity of each transaction and provides information on how applications can control transactions efficiently
- Technical design
  - If this is a section title
- AppWorkspaces are created by the system when an App is deployed to a Cluster

Incorrect:

- Technical Design (if this is a section title)
- App workspaces are created by system when an app is deployed to a cluster.

### Capitalization related references

- Grafana dashboards
  - https://grafana.com/solutions/apache-cassandra/monitor/
  - https://grafana.com/solutions/nomad/monitor
- https://docs.docker.com/desktop/install/windows-install/
- https://learn.microsoft.com/en-us/sql/sql-server/?view=sql-server-ver16
- https://kubernetes.io/docs/home/
  - But https://kubernetes.io/docs/tasks/
- https://www.envoyproxy.io/docs/envoy/latest/start/start
  - But "Getting Started"
- https://docs.github.com/en/billing/managing-billing-for-github-copilot/managing-your-github-copilot-subscription
  - Billing settings
  - Github Actions
  - Your Github account
  - Paid organizations for procurement companies

## Lists

List items **must NOT** end with a period:

Correct:

- Initialize the repository
- Configure all environment variables
- Ensure the server is running before deployment

Incorrect:

- Initialize the repository.
- Configure all environment variables.
- Ensure the server is running before deployment.

## Markdown files

Markdown files **must** be validated using the [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) tool with the followinq exceptions:

```json
    "markdownlint.config": {
        "MD004":false,
        "MD010": false,
        "MD029": false,
        "MD031": false,
        "MD033": false,
        "MD034": false,
    },
```

## References

- [Microsoft Writing Style Guide](https://docs.microsoft.com/en-us/style-guide/welcome/)
