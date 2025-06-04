# Software Engineering Principles and Best Practices for Voedger Development

- **Software Engineering**: The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software; that is, the application of engineering
to software (ISO/IEC/IEEE, “ISO/IEC/IEEE 24765:2017 Systems and Software Engineering — Vocabulary,” 2nd ed. 2017.)
- **disciplined**: (ˈdɪsɪplɪnd) showing a controlled form of behavior or way of working.
- **quantifiable**: (kwɒntɪˈfaɪəbl) able to be expressed or measured as a quantity.
- **Systematic approach**: An approach that follows the system of predefined principles and procedures
- **Why**: To achieve consistent (stable) results

## Table of contents

- [SWEBOK](se-swebok.md)
- [SOLID](se-solid.md)
- [DRY](se-dry.md)
- [Dynamic anti-patterns](se-antipatterns-dyn.md)
- [Pull Requests and Code Reviews](se-pr.md)
- [Using AI](se-ai.md)

## Checklist

### [Pull Requests and Code Reviews](se-pr.md)

- PRs should be small, focused, and self-contained
  - **Ideal Size**: ≤ 200 LOC (lines changed: added + removed)
  - **Target Size**: ≤ 400 LOC
  - **Soft Limit**: ≤ 800 LOC – requires justification in description
  - **Hard Limit**: > 800 LOC – must be split unless it's a generated file

## History

- 2025-06-04: [Monodocument](https://github.com/voedger/voedger-kb/blob/ff72bf1743f6f979f355cb31d78ef2461cc9b454/se.md#L26)
