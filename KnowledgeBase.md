# PROJECT_IDENTITY

## Purpose
Serves as a minimal dummy repository created to test and verify whether a Python project can be tracked and evaluated by automated AI code review tools [FACT].

## Core Features
- CLI application script that accepts user age input and evaluates age eligibility (`main.py`) [FACT].
- Project memory and documentation files (`KnowledgeBase.md`, `README.md`) [FACT].

## Users
- Developers and automated review engines testing tracking mechanisms and code analysis workflows [INFERRED].

---

# TECH_STACK

## Frontend
- None [FACT]

## Backend
- Python 3 [FACT]

## Database
- None [FACT]

## Authentication
- None [FACT]

## Infrastructure
- Git version control [FACT]

## External Services
- None [FACT]

---

# ARCHITECTURE

## High Level Design
Flat single-repository architecture containing an executable Python CLI entry point (`main.py`) alongside project documentation and living knowledge base files (`KnowledgeBase.md`, `README.md`) [FACT].

## Request Flow
1. User executes `main.py` via CLI [FACT].
2. Application prints `"Hello world"` to standard output (`stdout`) [FACT].
3. Application prompts user with `"enter age:"` via standard input (`stdin`) [FACT].
4. Application attempts conditional evaluation (`age < 18`) on the received string variable [FACT].
5. Application prints `"elegble for baking"` to `stdout` if evaluation succeeds [FACT].

## Data Flow
Standard Input (`stdin`) -> Variable `age` (`str`) -> Relational Expression (`age < 18`) -> Standard Output (`stdout`) [FACT].

## Important Modules
- `main.py`: Executable script handling CLI interaction and eligibility logic [FACT].
- `KnowledgeBase.md`: Authoritative architectural context and business rules for AI reviewers [FACT].
- `README.md`: Basic repository description file [FACT].

## System Boundaries
- Confined to the local CLI process runtime and local file system [INFERRED].

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
- **Purpose**: Root directory containing executable code and project memory [FACT].
- **Responsibilities**: Houses project documentation, AI knowledge base, and application entry points [FACT].
- **Dependencies**: Python 3 standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### `User / Applicant`
- **Purpose**: Entity providing input data (`age`) to verify criteria eligibility [INFERRED].
- **Relationships**: Processed in `main.py` [FACT].

### `Knowledge Base`
- **Purpose**: Maintains living architectural context, rules, and review guidelines for automated reviewers [FACT].
- **Relationships**: Read by AI review tools to evaluate PR diffs against project goals [INFERRED].

---

# BUSINESS_RULES

- **Tracking Objective**: Repository acts as a dummy testbed for tracking Python projects [FACT].
- **Type Safety on Input**: Interactive inputs must be cast to numeric types prior to numerical comparisons [INFERRED].
- **PR Description Accuracy**: PR descriptions ("fixed age var") must accurately match code changes supplied in the PR diff [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Standard Python `snake_case` for variables and source filenames (`age`, `main.py`) [FACT].
- Capitalized / PascalCase naming for documentation files (`README.md`, `KnowledgeBase.md`) [FACT].

## File Organization
- Flat layout with all files located in the root directory [FACT].

## Error Handling
- User inputs from `input()` must be converted using explicit exception handling (`try...except ValueError`) [INFERRED].

## State Management
- In-memory execution state limited to process lifecycle of `main.py` [FACT].

## Database Access Patterns
- None [FACT]

## API Design Patterns
- None [FACT]

## Security Patterns
- Input sanitization and type conversion required before processing user-provided arguments [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Simple, defensive procedural Python scripts with explicit type conversion and error handling [INFERRED].

## Anti-Patterns
- **Uncast Type Comparison**: Directly comparing the string result of `input()` with an integer (`age < 18`), which causes a runtime `TypeError` in Python 3 [FACT].
- **Uncorrected Bugs in Fix PRs**: Marking a PR as "fixed age var" while leaving the uncast string comparison intact in code [FACT].
- **Spelling Errors**: Output strings with typos (e.g., `"elegble for baking"` instead of `"eligible for banking"`) [FACT].

## Performance Concerns
- Minimal / trivial runtime overhead [FACT].

## Security Concerns
- Script crashes on non-numeric or unhandled user input [FACT].

## Maintainability Concerns
- Absence of automated testing (`pytest`) or linting/type-checking (`flake8`, `mypy`) [INFERRED].

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Application CLI script executing prompt and conditional evaluation [FACT].
- **Why changes are risky**: Comparing raw `str` output from `input()` directly with integer values raises `TypeError` at runtime [FACT].

### `KnowledgeBase.md`
- **Responsibility**: System memory for AI automated reviewers [FACT].
- **Why changes are risky**: Incorrect or stale information causes false positives or missed defects during PR reviews [INFERRED].

---

# KNOWN_RISKS

- **Runtime Crash (`TypeError`)**: `age = input(...)` assigns a `str`. The line `if age < 18:` raises `TypeError: '<' not supported between instances of 'str' and 'int'` [FACT].
- **PR Intent Discrepancy**: PR description claims "fixed age var", but the diff introduces `main.py` without converting `age` to an integer [FACT].
- **Typographical Errors**: User message contains typos (`"elegble for baking"`) [FACT].

---

# FUTURE_IMPROVEMENTS

- Explicitly cast user input to integer: `age = int(input("enter age:"))` inside a `try...except ValueError` block [INFERRED].
- Correct typo in output string to `"eligible for banking"` (or intended domain phrase) [INFERRED].
- Add inverse branch logic (`else:`) for age evaluation [INFERRED].
- Set up CI checks for Python linting (`flake8`) and type checking (`mypy`) [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Dummy repository created to verify Python repository tracking and PR code review capabilities [FACT].

## Business Intent
Prompt user for age input and output eligibility status [FACT].

## Important Constraints
- Python 3 `input()` returns `str`; numerical comparisons require explicit `int()` or `float()` type conversion [FACT].
- PR titles and descriptions must be validated against actual code changes in the diff to ensure claimed fixes are actually implemented [FACT].

## Non-Obvious Decisions
- Code changes in PRs may intentionally introduce subtle bugs (such as uncast `input()` calls or typos) to test AI review effectiveness [INFERRED].