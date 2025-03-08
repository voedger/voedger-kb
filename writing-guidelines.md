# Technical Writing Guidelines

This document outlines technical writing standards for Voedger projects, covering:

- Source code comments
- Requirements documentation
- Technical design documentation

## Definitions

- **Sentence Capitalization Style**: A style that uses capital letters only for the first word of a sentence, proper nouns, and acronyms, while all other words remain lowercase
- **Declarative Description**: Explains what a function does or achieves, using third-person verbs and complete sentences
- **Imperative Description**: Describes how a function works step-by-step, using imperative verbs and bullet points

## Requirement terminology

When specifying requirements, use the following terms with their specific meanings:

- **MUST**: Indicates an absolute requirement. Compliance is mandatory.
- **SHOULD**: Indicates a recommendation that may be ignored in particular circumstances after the implications are understood and carefully considered.
- **MAY**: Indicates an optional requirement that is truly optional and carries no recommendation.

Example:

- The system MUST validate all user input for security purposes
- Response times SHOULD be under 200ms for optimal user experience
- The application MAY provide alternative color themes for accessibility

References:

- [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119)

## Titles

- Sentence capitalization style MUST be used **except** for document titles (e.g., "Technical Writing Guidelines") and explicitly defined terms
- Articles (a, an, the) SHOULD NOT be used in titles

Correct examples:

- **Technical Writing Guidelines**
- **Technical design** *(as a section title)*

Incorrect examples:

- **Technical Design** *(Incorrect: Section titles use sentence capitalization.)*
- This guide describes locking and row versioning mechanisms the database engine uses... *(Incorrect: "Database Engine" must be capitalized.)*

## Terms capitalization

- Terms explicitly defined in the documentation (**e.g., Database Engine, App, Cluster, AppWorkspace**) SHOULD be capitalized

Correct examples:

- This guide describes locking and row versioning mechanisms the **Database Engine** uses to ensure the integrity of each transaction and provides information on how applications can control transactions efficiently
- **AppWorkspaces** are created by the system when an **Application** is deployed to a **Cluster**

References:

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

List items MUST NOT end with a period:

Correct:

- Initialize the repository
- Configure all environment variables
- Ensure the server is running before deployment

Incorrect:

- Initialize the repository.
- Configure all environment variables.
- Ensure the server is running before deployment.

## Markdown files

Markdown files MUST be validated using the [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) tool with the followinq exceptions:

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

## Go function documentation style

When documenting Go functions, use the following guidelines:

### Simple functions

Simple functions require only a declarative description:

```go
// New creates a new instance of the Sequencer type.
// Instance has actualizer() goroutine started.
func New(*isequencer.Params) isequencer.ISequencer, cleanup(), error {
    // ...
}
```
Declarative description guidelines:

- MUST use third-person verbs (generates, copies, validates)
- MUST use complete sentences with proper punctuation
- MUST use simple declarative sentences, not more than one per line

### Complex functions

Complex functions MUST include both declarative and imperative descriptions:

```go
// Next generates and returns the next sequence number for the given seqID.
// It ensures thread-safe access to sequence values and handles various caching layers.
// 
// Flow:
// - Validate processing status
// - Get initialValue from s.params.SeqTypes
// - Try to obtain next value from cache layers
// - Update caches with new value
func (s *sequencer) Next(seqID SeqID) (num Number, err error) {
    // ...
}
```

Imperative description guidelines:

- MUST use imperative verbs (validate, get, try)
- MUST start with "Flow:" and use bullet points
- Imperative bullet points MUST NOT have periods at the end

## References

- [Microsoft Writing Style Guide](https://docs.microsoft.com/en-us/style-guide/welcome/)
