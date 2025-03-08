# Writing style guide: Source code comments, requirements, technical documentation

## Capitalization

- Sentence capitalization **must** be used
- Defined terms **should** be capitalized

Correct:

- AppWorkspaces are created by system when an App is deployed to a Cluster.

Incorrect:

- App workspaces are created by system when an app is deployed to a cluster.

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
