# PROJECT_IDENTITY

## Purpose
Serves as a minimal repository used for testing, demonstrating, and evaluating command-line Python scripts and automated code review workflows [INFERRED].

## Core Features
- Command-line user interaction for age eligibility verification (`main.py`).
- Repository documentation and long-term project memory (`README.md`, `KnowledgeBase.md`).

## Users
- Developers and automated code review systems [INFERRED].

---

# TECH_STACK

## Frontend
- None [INFERRED]

## Backend
- Python 3 [FACT]

## Database
- None [INFERRED]

## Authentication
- None [INFERRED]

## Infrastructure
- Git version control [FACT]

## External Services
- None [INFERRED]

---

# ARCHITECTURE

## High Level Design
Flat single-repository structure containing executable Python CLI scripts (`main.py`) and markdown documentation files (`README.md`, `KnowledgeBase.md`).

## Request Flow
1. User executes `main.py` from the command line.
2. Script outputs greeting (`Hello world`).
3. Script prompts user for input (`enter age:`).
4. System evaluates input age against eligibility logic.
5. Resulting status message is output to the terminal.

## Data Flow
User Terminal Input -> `input()` String -> Variable `age` -> Relational Comparison (`age < 18`) -> Console Output [FACT].

## Important Modules
- **`main.py`**: Execution entry point containing user input and eligibility verification logic.
- **`KnowledgeBase.md`**: Project memory and AI review context.
- **`README.md`**: Repository README documentation.

## System Boundaries
Local Python 3 runtime and local file system / Git boundaries [INFERRED].

---

# REPOSITORY_STRUCTURE

```
.
├── KnowledgeBase.md
├── README.md
└── main.py
```

### Directory Details

#### `.` (Root Directory)
- **Purpose**: Main repository container holding execution scripts and documentation.
- **Responsibilities**: Stores CLI scripts (`main.py`) and knowledge base documents (`KnowledgeBase.md`, `README.md`).
- **Dependencies**: Python 3 standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### `Applicant / User`
- **Purpose**: Subject whose age is evaluated for banking eligibility.
- **Relationships**: Evaluated by conditional checks in `main.py` [INFERRED].

### `Knowledge Base`
- **Purpose**: Stores architectural context, rules, and guidelines for automated AI pull request analysis.
- **Relationships**: Read by AI review tools during pull request evaluation.

---

# BUSINESS_RULES

- Applicants must meet the legal age threshold (>= 18) to be eligible for banking services [INFERRED].
- [FACT] `main.py` currently checks `age < 18` for `"elegble for baking"`, which is a logic inversion and typo error [INFERRED].
- User inputs must be converted from string to integer (`int()`) before performing numerical relational comparisons [INFERRED].
- Pull request titles and descriptions must accurately represent the modifications introduced in the diff [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Standard Python `snake_case` for variables and script names (`age`, `main.py`).
- Standard Markdown capitalized filenames (`README.md`, `KnowledgeBase.md`).

## File Organization
- Flat root repository structure.

## Error Handling
- Console input conversion should be safely handled with type conversion and error checking (e.g., `try...except ValueError`) [INFERRED].

## State Management
- Ephemeral in-memory execution scope within `main.py` [FACT].

## Database Access Patterns
- None [INFERRED]

## API Design Patterns
- None [INFERRED]

## Security Patterns
- Input sanitization and explicit type casting prior to conditional comparisons [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Simple, procedural Python CLI scripts with explicit type conversion and error handling.

## Anti-Patterns
- **Uncast String Comparisons**: Comparing string variables from `input()` directly to numeric literals (`age < 18`), causing runtime `TypeError` in Python 3 [FACT].
- **Logic Inversion**: Checking `< 18` instead of `>= 18` for eligibility approval [INFERRED].
- **Typographical Errors in User Output**: Misspellings such as `"elegble for baking"` instead of `"eligible for banking"` [FACT].
- **PR Description Mismatch**: PR description claiming "fixed age var" while leaving uncast type comparisons or logic defects untouched [FACT].

## Performance Concerns
- Minimal / trivial CLI execution footprint.

## Security Concerns
- Unhandled `TypeError` or `ValueError` exceptions caused by unvalidated user input.

## Maintainability Concerns
- Absence of automated testing (`pytest`) and static analysis (`flake8`, `mypy`).

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Core CLI logic evaluating applicant eligibility.
- **Why changes are risky**: Directly impacts user interaction and core script execution; invalid types or inverted operators cause immediate runtime errors or incorrect domain logic [FACT].

### `KnowledgeBase.md`
- **Responsibility**: Authoritative architectural memory for automated code review systems.
- **Why changes are risky**: Inaccurate information leads AI reviewers to misinterpret repo conventions and false-positive PR reviews [INFERRED].

---

# KNOWN_RISKS

- **Runtime `TypeError`**: [FACT] In `main.py`, `age` is assigned from `input()` (string). Executing `age < 18` raises `TypeError: '<' not supported between instances of 'str' and 'int'`.
- **Domain Spelling Defect**: [FACT] Console output prints `"elegble for baking"` instead of `"eligible for banking"`.
- **Inverted Logical Check**: [FACT] Script tests `age < 18` to print eligibility status.
- **Lack of Automated Testing / CI**: Absence of CI checks allows syntax and runtime errors to be merged without automated validation [INFERRED].

---

# FUTURE_IMPROVEMENTS

- Explicitly cast user input to integer using `int(input(...))` within a `try/except ValueError` block [INFERRED].
- Correct conditional expression to `if age >= 18:` [INFERRED].
- Fix output text typo to `"eligible for banking"` [INFERRED].
- Add an `else` clause for non-eligible users [INFERRED].
- Introduce static analysis (`mypy`, `flake8`) and unit tests (`pytest`) in CI pipelines [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Simple command-line interface validating user input against domain eligibility logic.

## Business Intent
Verify whether an applicant meets the minimum age requirement for banking services.

## Important Constraints
- `input()` returns a string in Python 3 and must be cast to `int` before numeric comparison [FACT].
- Output strings must use correct domain spelling (`eligible`, `banking`) [INFERRED].

## Non-Obvious Decisions
- Pull request titles and descriptions must be compared directly against the execution path in code diffs to verify claims such as "fixed age var" actually fix underlying type and logic bugs [INFERRED].