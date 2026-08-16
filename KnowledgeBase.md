# PROJECT_IDENTITY

## Purpose
Serves as a minimal repository used for testing, demonstrating, and evaluating command-line Python scripts and project documentation review workflows [INFERRED].

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
Flat repository structure containing executable Python CLI scripts (`main.py`) and markdown documentation files (`README.md`, `KnowledgeBase.md`).

## Request Flow
1. User executes script (`main.py`) from console.
2. Script prints greeting message (`Hello world`).
3. System prompts user for age input (`input("enter age:")`).
4. System attempts evaluation against age criteria.
5. Resulting status message is printed to console.

## Data Flow
User Terminal Input -> `input()` String -> Variable `age` -> Relational Comparison (`age < 18`) -> Console Output [FACT].

## Important Modules
- **`main.py`**: Command-line interface entry point containing execution logic.
- **`KnowledgeBase.md`**: Project memory and AI review guidelines.
- **`README.md`**: General project documentation.

## System Boundaries
Local Python runtime environment and Git filesystem boundaries [INFERRED].

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
- **Purpose**: Main repository root holding source scripts and documentation.
- **Responsibilities**: Stores script entry points (`main.py`) and knowledge base documents (`KnowledgeBase.md`, `README.md`).
- **Dependencies**: Python 3 standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### `Banking Applicant / User`
- **Purpose**: Individual whose age is checked to determine eligibility for banking services.
- **Relationships**: Checked by conditional logic in `main.py` [INFERRED].

### `Knowledge Base / Documentation`
- **Purpose**: Captures architectural constraints, domain rules, and guidelines for AI automated reviews.
- **Relationships**: Consumed by automated PR review systems.

---

# BUSINESS_RULES

- Users must meet the age threshold (typically age > 18 or >= 18) to be eligible for banking services [INFERRED].
- [FACT] `main.py` currently checks `age < 18` for `"elegble for baking"`, which contradicts the intended business rule (Logic Inversion) [INFERRED].
- User console inputs must be converted to numeric integers (`int()`) before performing relational logic comparisons [INFERRED].
- PR metadata (title and description) must accurately reflect the code diff and logical outcomes [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Standard Python `snake_case` for variables and scripts (`age`, `main.py`).
- UPPERCASE / CamelCase for markdown files (`README.md`, `KnowledgeBase.md`).

## File Organization
- Flat root repository layout.

## Error Handling
- Console input reading should wrap integer casting (`int()`) in exception handling (`try...except ValueError`) to handle invalid non-numeric inputs [INFERRED].

## State Management
- In-memory execution variables within local script scope [FACT].

## Database Access Patterns
- None [INFERRED]

## API Design Patterns
- None [INFERRED]

## Security Patterns
- Input validation and type casting prior to conditional checks [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Executable procedural scripts using clean control flow and explicit variable casting.

## Anti-Patterns
- **Uncast String Comparisons**: Comparing raw `input()` strings directly to integer literals (`age < 18`), which causes a runtime `TypeError` in Python 3 [FACT].
- **Inverted Logic Conditions**: Checking `< 18` when business intent specifies eligibility for age over 18 [INFERRED].
- **Typographical Errors**: Spelling mistakes in string output (e.g., `"elegble for baking"` instead of `"eligible for banking"`) [FACT].
- **PR Intent Discrepancy**: PR description claims `fixed age var` while leaving underlying type error and logic bugs in place [FACT].
- **Missing Conditional Branches**: Omitting `else` blocks when handling binary eligibility outcomes [INFERRED].

## Performance Concerns
- Minimal; lightweight CLI execution.

## Security Concerns
- Missing type and input bounds validation causing unhandled runtime exceptions (`TypeError`, `ValueError`).

## Maintainability Concerns
- Lack of static analysis (linting/type checking) and unit tests for script logic.

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Primary executable entry point containing age evaluation logic.
- **Why changes are risky**: Changes affect user interaction and runtime stability; uncast inputs or inverted operators cause immediate script failure or incorrect business decisions [FACT].

### `KnowledgeBase.md`
- **Responsibility**: Authoritative architectural memory for automated code reviews.
- **Why changes are risky**: Incorrect or stale entries lead AI reviewers to misinterpret repository rules and PR intent [INFERRED].

---

# KNOWN_RISKS

- **Runtime `TypeError`**: [FACT] In `main.py`, `age` is assigned from `input()`, returning a string. Executing `age < 18` raises `TypeError: '<' not supported between instances of 'str' and 'int'`.
- **Domain Spelling Bugs**: [FACT] Console output prints `"elegble for baking"` instead of `"eligible for banking"`.
- **Logic Inversion**: [FACT] Script tests `age < 18` for positive eligibility, reversing intended domain rules.
- **No Automated CI Checks**: Lack of linting or unit testing allows runtime bugs to be merged without automated friction [INFERRED].

---

# FUTURE_IMPROVEMENTS

- Convert `input()` explicitly to integer with `int(input(...))` inside a `try/except ValueError` block [INFERRED].
- Correct condition to `if age >= 18:` (or `if age > 18:`) [INFERRED].
- Fix output text typos to `"eligible for banking"` [INFERRED].
- Add an `else:` branch to notify ineligible users [INFERRED].
- Integrate automated testing (`pytest`) and static analysis (`flake8`, `mypy`) into PR workflows [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Simple command-line interface validating user input against domain eligibility conditions.

## Business Intent
Verify if a user meets the age requirement (> 18) for banking services.

## Important Constraints
- `input()` in Python 3 returns `str`; it must be explicitly cast to `int` before comparing with numbers [FACT].
- Output text must accurately spell domain terminology (`eligible`, `banking`) [INFERRED].

## Non-Obvious Decisions
- PR titles and descriptions must be cross-checked against actual code execution paths to ensure that claims like "fixed age var" actually resolve type mismatch errors and logical inversions [INFERRED].