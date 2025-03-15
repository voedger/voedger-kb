# Technical Writing Guidelines

This document outlines technical writing standards for Voedger projects, covering:

- Requirements documentation
- Technical design documentation
- Source code comments

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

👍Correct examples:

- **Technical Writing Guidelines** *(document title)*
- **Technical design** *(section title)*

❌Incorrect examples:

- **Technical Design** *(Incorrect: Section titles use sentence capitalization)*
- **The technical design** *(Incorrect: Articles should not be used in titles)*

## Terms capitalization

- Terms explicitly defined in the documentation (**e.g., Database Engine, App, Cluster, AppWorkspace**) SHOULD be capitalized

👍Correct examples:

- This guide describes locking and row versioning mechanisms the **Database Engine** uses to ensure the integrity of each transaction
- **AppWorkspaces** are created by the system when an **Application** is deployed to a **Cluster**

❌Incorrect examples:

- This guide describes locking and row versioning mechanisms the **database engine** uses... *(Incorrect: "Database Engine" must be capitalized)*
- **App workspaces** are created by the system... *(Incorrect: "AppWorkspaces" is the correct term)*

## Lists

List items MUST NOT end with a period:

👍Correct examples:

- Initialize the repository
- Configure all environment variables
- Ensure the server is running before deployment

❌Incorrect examples:

- Initialize the repository.
- Configure all environment variables.
- Ensure the server is running before deployment.

## Markdown files

Markdown files MUST be validated using the [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) tool to ensure consistent formatting across all documentation. The following exceptions to the default rules are allowed:

```json
    "markdownlint.config": {
        "MD004": false,  // Allow alternative unordered list style
        "MD010": false,  // Allow hard tabs in code blocks
        "MD029": false,  // Allow ordered lists with non-1 start values
        "MD031": false,  // Allow fenced code blocks without surrounding blank lines
        "MD033": false,  // Allow inline HTML for complex formatting needs
        "MD034": false,  // Allow bare URLs when necessary
    },
```

Some markdownlint rules:

- [MD032](https://github.com/DavidAnson/markdownlint/blob/v0.37.4/doc/md032.md): Lists should be surrounded by blank lines
- [MD012](https://github.com/DavidAnson/markdownlint/blob/v0.37.4/doc/md012.md): Multiple consecutive blank lines

## Go function documentation style

When documenting Go functions, choose between simple and complex documentation styles based on the function's complexity and importance.

### Simple functions

Use simple documentation for straightforward functions with clear, limited responsibilities. Simple functions require only a declarative description:

```go
// New creates a new instance of the Sequencer type.
// Instance has actualizer() goroutine started.
// cleanup: function to stop the actualizer.
func New(*isequencer.Params) (isequencer.ISequencer, cleanup func(), error) {
    // ...
}
```

```go
// Flush completes Event Processing.
// Panics if Event Processing is not in progress.
// Copies `inproc` buffer to the `toBeFlushed` buffer and clears `inproc`.
// Sends the current batch to the flushing queue and completes the event processing.
func (s *sequencer) Flush() {
    // ...
}
```

Declarative description guidelines:

- MUST use third-person present tense verbs (generates, copies, validates, completes, panics)
- MUST use complete sentences with proper punctuation, not more than one sentence per line
- MAY include multiple declarative sentences describing behaviors, preconditions, and effects like "Copies `inproc` buffer to the..."
- MAY describe behavior conditions using "if" statements or phrases like "Panics if..."
- MAY include descriptions of input parameters and return values using a colon format (e.g., "cleanup: function to stop the actualizer")

### Complex functions

Use complex documentation for functions that:

- Implement critical business logic
- Have multiple steps or conditions
- Require understanding of system architecture
- Are called from multiple locations

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
- MUST describe the sequence of operations in order of execution

## `requirements.md` files

A `requirements.md` file documents the requirements for a project or package. These files are especially valuable as they can be referenced in prompts for generative AI tools, providing structured guidance for generating sources, README.md files, schemas, and other artifacts.

For content derived from other sources, attribution at the beginning of the document MUST be included, following this format:

```markdown
# Requirements

This document contains content derived from the following sources:

- https://github.com/voedger/voedger-internals/<path-to-file1>
- https://github.com/voedger/voedger-internals/<path-to-file2>
```

## References

Guides:

- [Microsoft Writing Style Guide](https://docs.microsoft.com/en-us/style-guide/welcome/)
- [Google Developer Documentation Style Guide](https://developers.google.com/style)

Industry examples:

- [Grafana: Apache Cassandra monitoring guide](https://grafana.com/solutions/apache-cassandra/monitor/)
- [Grafana: Nomad monitoring documentation](https://grafana.com/solutions/nomad/monitor)
- [Docker: Windows installation guide](https://docs.docker.com/desktop/install/windows-install/)
- [Microsoft SQL Server technical documentation](https://learn.microsoft.com/en-us/sql/sql-server/?view=sql-server-ver16)
- [Envoy Proxy: Getting started guide](https://www.envoyproxy.io/docs/envoy/latest/start/start)
- [GitHub Copilot subscription management](https://docs.github.com/en/billing/managing-billing-for-github-copilot/managing-your-github-copilot-subscription) - Consistently capitalizes product names:
  - "Billing settings"
  - "GitHub Actions"
  - "Your GitHub account"
  - "Paid organizations for procurement companies"
