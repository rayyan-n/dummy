# PROJECT_IDENTITY

## Purpose
Serves as a minimal dummy repository created to test and demonstrate tracking and automated AI code review capabilities for Python projects [FACT].

## Core Features
- CLI application for accepting user age input and evaluating age eligibility (`main.py`) [FACT].
- Long-term project memory and documentation (`KnowledgeBase.md`, `README.md`) [FACT].

## Users
- Developers testing tracking mechanisms and automated AI code review systems [INFERRED].

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
Flat single-repository architecture containing executable Python CLI scripts (`main.py`) and markdown documentation/knowledge base files (`KnowledgeBase.md`, `README.md`) [FACT].

## Request Flow
1. User runs `main.py` directly from the command line [FACT].
2. System prints `"Hello world"` to standard output [FACT].
3. System prompts user with `"enter age:"` via standard input [FACT].
4. System attempts conditional comparison on the input variable (`age < 18`) [FACT].
5. System prints result string (`"elegble for baking"`) if condition evaluates to true [FACT].

## Data Flow
User Input (`stdin`) -> Variable `age` (String) -> Conditional Expression (`age < 18`) -> Output String (`stdout`) [FACT].

## Important Modules
- `main.py`: Entry point script handling CLI user interaction and age verification logic [FACT].
- `KnowledgeBase.md`: Authoritative living context file used by AI code review tools [FACT].
- `README.md`: Basic project overview documentation [FACT].

## System Boundaries
- Constrained to the local Python runtime execution environment and local file system [INFERRED].

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
- **Purpose**: Root container for project execution scripts, documentation, and metadata [FACT].
- **Responsibilities**: Stores the application CLI entry point (`main.py`) and project knowledge documentation [FACT].
- **Dependencies**: Python 3 standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### `User / Applicant`
- **Purpose**: Subject providing age input to determine eligibility [INFERRED].
- **Relationships**: Evaluated inside `main.py` [FACT].

### `Knowledge Base`
- **Purpose**: Centralized storage of architectural patterns, business rules, and review guidelines for automated reviewers [FACT].
- **Relationships**: Read by AI review tools to evaluate PR diffs against stated intents [INFERRED].

---

# BUSINESS_RULES

- **Project Goal**: Maintained as a dummy project to verify Python repository tracking [FACT].
- **Input Type Conversion**: User inputs from `input()` must be explicitly converted to numeric types before relational operations [INFERRED].
- **PR Intent Integrity**: PR descriptions and titles must accurately reflect actual code modifications in the diff [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Standard Python `snake_case` for variables and source files (`age`, `main.py`) [FACT].
- PascalCase/Capitalized naming for root documentation markdown files (`README.md`, `KnowledgeBase.md`) [FACT].

## File Organization
- Flat, non-nested root directory layout [FACT].

## Error Handling
- CLI input conversion should be protected against invalid non-numeric inputs using explicit type casting and error handling (`try...except ValueError`) [INFERRED].

## State Management
- In-memory execution state limited to the process lifecycle of `main.py` [FACT].

## Database Access Patterns
- None [FACT]

## API Design Patterns
- None [FACT]

## Security Patterns
- Ensure user inputs are sanitized and validated before processing [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Simple procedural Python script execution with explicit type conversion and validation [INFERRED].

## Anti-Patterns
- **Uncast Type Comparison**: Comparing string return values from `input()` directly with integers (`age < 18`), which triggers a runtime `TypeError` in Python 3 [FACT].
- **Inverted / Defective Business Logic**: Checking `age < 18` to print eligibility status rather than `age >= 18` [HYPOTHESIS].
- **Typographical Discrepancies**: Misspellings in user output (e.g., `"elegble for baking"` instead of `"eligible for banking"`) [FACT].
- **Misleading PR Intent**: PR description stating "fixed age var" while the diff introduces or leaves uncast type bugs intact [FACT].

## Performance Concerns
- Minimal execution impact [FACT].

## Security Concerns
- Script crash on unhandled invalid user input [FACT].

## Maintainability Concerns
- Lack of automated testing (`pytest`) and static linting/type checking (`mypy`, `flake8`) [INFERRED].

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Application CLI entry point containing prompt and conditional logic [FACT].
- **Why changes are risky**: Uncast string-to-int operations cause runtime execution crashes (`TypeError`) [FACT].

### `KnowledgeBase.md`
- **Responsibility**: System memory for AI reviewers [FACT].
- **Why changes are risky**: Stale or incorrect entries lead AI reviewers to incorrect assumptions during PR analysis [INFERRED].

---

# KNOWN_RISKS

- **Runtime `TypeError` Bug**: `input()` in `main.py` returns `str`. Evaluating `age < 18` throws `TypeError: '<' not supported between instances of 'str' and 'int'` [FACT].
- **Typographical Bug**: User output contains typos (`"elegble for baking"`) [FACT].
- **PR Description Mismatch**: PR title ("Test2") and description ("fixed age var") do not fix the underlying `TypeError` bug in `main.py` [FACT].

---

# FUTURE_IMPROVEMENTS

- Explicitly cast user age input: `age = int(input("enter age:"))` inside a `try...except ValueError` block [INFERRED].
- Fix output spelling to `"eligible for banking"` [INFERRED].
- Correct conditional check logic (e.g., `if age >= 18:`) and add an `else` branch for non-eligible users [INFERRED].
- Add CI steps for Python linting (`flake8`) and type checking (`mypy`) [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Simple dummy Python project to validate repository tracking and automated code review workflows [FACT].

## Business Intent
Prompt user for age and determine eligibility for services [FACT].

## Important Constraints
- Python 3 `input()` returns a string; comparison operations with integers require explicit numeric conversion (`int()`) [FACT].
- PR metadata must be checked against the diff to ensure claimed fixes actually address the code bugs [FACT].

## Non-Obvious Decisions
- Historical markdown-only repo structure was expanded to include Python execution scripts (`main.py`) to test code-level PR analysis capabilities [FACT].