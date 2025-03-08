# Technical Writing Guidelines

This document outlines technical writing standards for Voedger projects, covering:

- Source code comments
- Requirements documentation
- Technical design documentation

## Titles

- Use sentence capitalization **except** for document titles (e.g., "Technical Writing Guidelines") and explicitly defined terms
- Articles (a, an, the) **should NOT** be used in titles

Correct examples:

- **Technical Writing Guidelines**
- **Technical design** *(as a section title)*

Incorrect examples:

- **Technical Design** *(Incorrect: Section titles use sentence capitalization.)*
- This guide describes locking and row versioning mechanisms the database engine uses... *(Incorrect: "Database Engine" must be capitalized.)*

## Terms capitalization

- Terms explicitly defined in documentation (**e.g., Database Engine, App, Cluster, AppWorkspace**) **should** always be capitalized consistently

Correct examples:

- This guide describes locking and row versioning mechanisms the **Database Engine** uses to ensure the integrity of each transaction and provides information on how applications can control transactions efficiently
- **AppWorkspaces** are created by the system when an **Application** is deployed to a **Cluster**

### References related to capitalization

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
