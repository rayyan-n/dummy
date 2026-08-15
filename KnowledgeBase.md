# PROJECT_IDENTITY

## Purpose
Serves as a minimal repository for testing, demonstrating, and evaluating basic command-line interactions, Python scripts, and documentation changes [INFERRED].

## Core Features
- Command-line user interaction for age eligibility verification (`main.py`).
- Repository documentation and test tracking (`README.md`).

## Users
- Developers and automated code review or testing systems [INFERRED].

---

# TECH_STACK

## Frontend
- None [INFERRED]

## Backend
- Python 3 [INFERRED]

## Database
- None [INFERRED]

## Authentication
- None [INFERRED]

## Infrastructure
- Git version control.

## External Services
- None [INFERRED]

---

# ARCHITECTURE

## High Level Design
Flat repository layout containing simple executable Python CLI scripts (`main.py`) and static project documentation (`README.md`).

## Request Flow
1. Script execution (`main.py`) starts from terminal.
2. System displays initial output message (`Hello world`).
3. System prompts user for age input (`enter age:`).
4. System processes input and evaluates against banking age eligibility rules.
5. Resulting eligibility message is printed to console.

## Data Flow
User Input (Terminal) -> Console Input Read -> Variable Assignment/Conversion -> Condition Assessment -> Console Output [INFERRED].

## Important Modules
- **`main.py`**: CLI script executing banking age eligibility logic.
- **`README.md`**: Document holding repository metadata and status content.

## System Boundaries
Local Python runtime environment and Git version control system.

---

# REPOSITORY_STRUCTURE

```
.
├── README.md
└── main.py
```

### Directory Details

#### `.` (Root Directory)
- **Purpose**: Main repository container holding documentation and script files.
- **Responsibilities**: Houses entry-point scripts (`main.py`) and documentation (`README.md`).
- **Dependencies**: Python standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### `Banking Applicant / User`
- **Purpose**: Subject whose age is verified to determine banking service eligibility.
- **Relationships**: Evaluated against banking age threshold criteria (`age > 18`) [INFERRED].

### `README Document`
- **Purpose**: Holds project documentation and text change history.
- **Relationships**: None [INFERRED].

---

# BUSINESS_RULES

- A user must be greater than 18 years old to be eligible for banking services (`age > 18`) [INFERRED].
- PR titles and descriptions must accurately describe the intended code changes, target files, and logical outcomes [INFERRED].
- Code logic must strictly fulfill user intent specified in PR descriptions without introducing logic inversions, missing branches, or typos [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Python standard `snake_case` for variables and script files [INFERRED].
- Upper-case naming for markdown documentation (`README.md`).

## File Organization
- Flat root-level file structure.

## Error Handling
- Console inputs must be assigned to variables and converted to integers (`int()`) with proper validation to prevent runtime errors [INFERRED].

## State Management
- Local in-memory script execution variables [INFERRED].

## Database Access Patterns
- None [INFERRED]

## API Design Patterns
- None [INFERRED]

## Security Patterns
- Input validation and type casting before processing business logic [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Direct, functional procedural execution for CLI scripts.
- Explicit variable binding for user inputs (`age = int(input(...))`) [INFERRED].

## Anti-Patterns
- **Unassigned Inputs**: Invoking `input()` without capturing the return value in a variable.
- **Undefined Variable References**: Referencing variables in conditions (e.g., `age`) that were never declared or assigned (causes `NameError`).
- **Type Mismatch Comparisons**: Comparing string input directly against integers (causes `TypeError`).
- **Inverted Logic Conditions**: Using `<` operators when business requirements specify `>` or `>=`.
- **Typographical Errors**: Misspelling domain terms or PR descriptions (e.g., `baking` instead of `banking`, `elegble` instead of `eligible`, `grater` instead of `greater`).
- **PR Metadata & Code Discrepancy**: PR descriptions stating logic ("check if age greater than 18") that directly contradicts the diff implementation (`if age < 18`).
- **Incomplete Logical Branches**: Missing `else` statements when the PR description explicitly requires handling negative conditions ("else not").

## Performance Concerns
- Minimal due to lightweight script execution context.

## Security Concerns
- Missing type validation on user input leading to unhandled exceptions (`ValueError` on non-numeric input).

## Maintainability Concerns
- Lack of error handling, static analysis/linting, and unit tests for input validation.

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Script containing user input collection and age eligibility logic.
- **Why changes are risky**: Missing variable initialization, improper type conversion, or inverted conditions break core application execution and business requirements.

### `README.md`
- **Responsibility**: Core repository documentation.
- **Why changes are risky**: Unaligned edits cause documentation degradation.

---

# KNOWN_RISKS

- **Runtime `NameError`**: Referencing `age` without assigning the output of `input()` causes runtime execution failure [INFERRED].
- **Runtime `TypeError`**: Comparing string output from `input()` directly against integer `18` causes `TypeError` [INFERRED].
- **Business Logic Inversion**: Inverted relational operators (`<` vs `>`) yield incorrect eligibility decisions [INFERRED].
- **Textual Inconsistencies**: Spelled outputs (`baking` vs `banking`, `elegble` vs `eligible`) misrepresent intent and domain language [INFERRED].
- **Lack of Tooling**: No static analyzers, linters, or CI checks are configured to catch syntax errors or typos automatically [INFERRED].

---

# FUTURE_IMPROVEMENTS

- Convert console input explicitly to integer with `try/except` error handling [INFERRED].
- Implement complete conditional paths (`if`/`else`) to handle both eligible and ineligible user inputs [INFERRED].
- Add automated Python linting (`flake8` / `black` / `pylint`) and static analysis checks [INFERRED].
- Add unit tests verifying eligibility condition logic [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Simple CLI program that collects user input and executes basic conditional business logic.

## Business Intent
Determine banking service eligibility based on user age (> 18).

## Important Constraints
- Input from `input()` must be assigned to a variable and cast to an integer before conditional comparisons.
- Printed string outputs must match exact domain vocabulary (`banking`, `eligible`).

## Non-Obvious Decisions
- AI reviewers must strictly cross-check PR title and description against diff logic to catch inverse conditions (`< 18` vs `> 18`), missing variable assignments, missing `else` branches, and spelling errors.