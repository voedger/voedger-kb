# Software Engineering Principles and Best Practices for Voedger Development

- **Software Engineering**: The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software; that is, the application of engineering
to software (ISO/IEC/IEEE, “ISO/IEC/IEEE 24765:2017 Systems and Software Engineering — Vocabulary,” 2nd ed. 2017.)
- **disciplined**: (ˈdɪsɪplɪnd) showing a controlled form of behavior or way of working.
- **quantifiable**: (kwɒntɪˈfaɪəbl) able to be expressed or measured as a quantity.
- **Systematic approach**: An approach that follows the system of predefined principles and procedures
- **Why**: To achieve consistent (stable) results

## Articles

- [SWEBOK](se-swebok.md)
- [SOLID](se-solid.md)
- [DRY](se-dry.md)
- [Dynamic anti-patterns](se-antipatterns-dyn.md)
- [Pull Requests and Code Reviews](se-pr.md)
- [Prompt Engineering, Lee Boonstra, Google](se-pe.md)
- [Software Engineering & AI](se-ai.md)

## Checklist

---

### Pull Requests and Code Reviews

#### LOC200 Rule

- PRs should be small, focused, and self-contained
- **Ideal Size**: ≤ 200 LOC (lines changed: added + removed)
- **Target Size**: ≤ 400 LOC
- **Soft Limit**: ≤ 800 LOC – requires justification in description
- **Hard Limit**: > 800 LOC – must be split unless it's a generated file
- Numerology: HTTP 200 status code, also known as "OK," indicates that the request was successful

#### PR Size Management

- If a developer believes it’s not feasible to follow the LOC200 guideline, they should prepare an Implementation plan
- Each step in the plan should ideally fit within the 200 LOC limit
- Steps should be materialized into issues and implemented sequentially — avoid creating all issues upfront
- If any step unexpectedly requires additional development, a separate issue and PR should be created for it

[Example](https://github.com/voedger/voedger/issues/3704): while implementing the `subscribe and watch #3749` logic, the developer realizes that they need to add functionality to the `pkg/coreutils/json.go` file. In this case, they should raise a new issue and submit a dedicated PR.

#### Related articles

- [Pull Requests and Code Reviews](se-pr.md)

---

## History

- 2025-06-04: [Monodocument](https://github.com/voedger/voedger-kb/blob/ff72bf1743f6f979f355cb31d78ef2461cc9b454/se.md#L26)
