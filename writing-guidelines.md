# Technical Writing Guidelines

This document outlines technical writing standards for Voedger projects, covering:

- Source code comments
- Requirements documentation
- Technical design documentation

## About this document

This technical writing guide itself uses the RFC 2119 terminology (MUST, SHOULD, MAY) to indicate the importance level of each guideline:

- MUST: Indicates an absolute requirement. Compliance is mandatory
- SHOULD: Indicates a recommendation that may be ignored in particular circumstances after the implications are understood and carefully considered
- MAY: Indicates an optional requirement that is truly optional and carries no recommendation
- MUST NOT: Indicate practices that are absolutely prohibited in all Voedger documentation
- SHOULD NOT: Indicate practices that are generally discouraged, though exceptions may exist with proper justification
- MAY NOT: Indicate practices that are optional to prohibit, depending on specific project requirements

Examples:

- Writers MUST use sentence capitalization for section titles (required)
- Code examples SHOULD include comments for complex operations (recommended)
- Documentation pages MAY include diagrams when helpful (optional)
- Writers MUST NOT include personally identifiable information in code examples (prohibited)
- Code comments SHOULD NOT include implementation details that duplicate what the code already clearly shows (discouraged)
- Documentation MAY NOT include version-specific screenshots if they're likely to become outdated quickly (optionally prohibited)

References:

- [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119)

## Definitions

- **Sentence Capitalization Style**: A style that uses capital letters only for the first word of a sentence, proper nouns, and acronyms, while all other words remain lowercase
- **Declarative Description**: Explains what a function does or achieves, using third-person verbs and complete sentences
- **Imperative Description**: Describes how a function works step-by-step, using imperative verbs and bullet points

## Titles

- Sentence capitalization style MUST be used **except** for document titles (e.g., "Technical Writing Guidelines"), proper names and explicitly defined terms
- Articles (a, an, the) SHOULD NOT be used in titles

Correct examples:

- **Technical Writing Guidelines**
- **Technical design** *(as a section title)*

Incorrect examples:

- **Technical Design** *(Incorrect: Section titles use sentence capitalization)*

## Terms capitalization

- Terms explicitly defined in the documentation (**e.g., Database Engine, App, Cluster, AppWorkspace**) SHOULD be capitalized

Correct examples:

- This guide describes locking and row versioning mechanisms the **Database Engine** uses to ensure the integrity of each transaction and provides information on how applications can control transactions efficiently
- **AppWorkspaces** are created by the system when an **Application** is deployed to a **Cluster**

Incorrect examples:

- This guide describes locking and row versioning mechanisms the **database engine** uses... *(Incorrect: "Database Engine" must be capitalized.)*

Industry examples of technical term capitalization:

- **Grafana documentation**:
  - [Apache Cassandra monitoring guide](https://grafana.com/solutions/apache-cassandra/monitor/)
  - [Nomad monitoring documentation](https://grafana.com/solutions/nomad/monitor)

- **Docker documentation**:
  - [Windows installation guide](https://docs.docker.com/desktop/install/windows-install/)

- **Microsoft SQL Server documentation**:
  - [SQL Server technical documentation](https://learn.microsoft.com/en-us/sql/sql-server/?view=sql-server-ver16)

- **Envoy Proxy documentation**:
  - [Getting started guide](https://www.envoyproxy.io/docs/envoy/latest/start/start)

- **GitHub documentation**:
  - [GitHub Copilot subscription management](https://docs.github.com/en/billing/managing-billing-for-github-copilot/managing-your-github-copilot-subscription) - Consistently capitalizes product names:
    - "Billing settings"
    - "GitHub Actions"
    - "Your GitHub account"
    - "Paid organizations for procurement companies"

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
