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

## Checklists

---

### Pull requests and code reviews

#### LOC200 Rule

- PRs should be small, focused, and self-contained
- ⚡**Ideal size**: ≤ 200 LOC (lines changed: added + removed)
- **Target size**: ≤ 400 LOC
- **Soft limit**: ≤ 800 LOC – requires justification in description
- **Hard limit**: > 800 LOC – must be split unless it's a generated file
- 😂Numerology: HTTP 200 status code, also known as "OK," indicates that the request was successful

#### PR size management

- If a developer considers it’s not feasible to follow the LOC200 guideline, they SHOULD prepare an Implementation plan
- Each step in the plan SHOULD ideally fit within the 200 LOC limit
- Steps MUST be materialized into issues and implemented sequentially — avoid creating all issues upfront
- If any step unexpectedly requires additional development, a separate issue and PR MUST be created for it

[Example](https://github.com/voedger/voedger/issues/3704): while implementing the `subscribe and watch #3749` logic, the developer realizes that they need to add functionality to the `pkg/coreutils/json.go` file. In this case, they should raise a new issue and submit a dedicated PR.

#### PR & issues

- An issue MUST be created for every PR
- Issue naming pattern MUST keep every child L1-issue clearly tied to the parent L2-issue

[Example](https://chatgpt.com/share/684a9006-4f48-800b-888b-fb11eb9667f0):

- L2-issue is named `APIv2: implement /notifications/ paths`
- Three L1-issues could be created with the names:
  - `APIv2 /notifications: add JSON & WSID helper utilities`
  - `APIv2 /notifications: wire router & DI for new endpoints`  
  - `APIv2 /notifications: implement subscribe/watch handler & tests`
  
#### Related articles

- [Pull Requests and Code Reviews](se-pr.md)

---

## History

- 2025-06-04: [Monodocument](https://github.com/voedger/voedger-kb/blob/ff72bf1743f6f979f355cb31d78ef2461cc9b454/se.md#L26)
