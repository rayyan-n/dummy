# PROJECT_IDENTITY

## Purpose
Serves as a dummy project set to check if a Python project can be tracked and evaluated by automated AI review systems [FACT].

## Core Features
- Executable Python script for collecting user age and evaluating eligibility (`main.py`) [FACT].
- Long-term project memory and documentation repository (`KnowledgeBase.md`, `README.md`) [FACT].

## Users
- Developers and automated code review systems testing repository tracking capabilities [INFERRED].

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
Flat single-repository structure containing a executable Python entry script (`main.py`) alongside project documentation and living knowledge base files (`KnowledgeBase.md`, `README.md`) [FACT].

## Request Flow
1. User executes `main.py` directly in the command line [FACT].
2. System displays `"Hello world"` [FACT].
3. System prompts user with `"enter age:"` via standard input [FACT].
4. System attempts conditional comparison on user input variable (`age < 18`) [FACT].
5. System displays result message (`"elegble for baking"`) if condition evaluates to true [FACT].

## Data Flow
User Input (`stdin`) -> String variable (`age`) -> Conditional expression (`age < 18`) -> Output message (`stdout`) [FACT].

## Important Modules
- `main.py`: Command-line entry point script handling user input and conditional eligibility logic [FACT].
- `KnowledgeBase.md`: System memory and architectural guidelines used by AI reviewer tools [FACT].
- `README.md`: Basic repository documentation [FACT].

## System Boundaries
- Bound to the local Python process execution runtime and local filesystem [INFERRED].

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
- **Purpose**: Root container for application source code and documentation [FACT].
- **Responsibilities**: Stores `main.py`, `KnowledgeBase.md`, and `README.md` [FACT].
- **Dependencies**: Python 3 standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### `User / Applicant`
- **Purpose**: Subject providing age input to check eligibility [INFERRED].
- **Relationships**: Evaluated procedurally within `main.py` [FACT].

### `Knowledge Base`
- **Purpose**: Living document storing architectural decisions, business rules, and review context for AI systems [FACT].
- **Relationships**: Consumed by automated code review pipelines [INFERRED].

---

# BUSINESS_RULES

- **Project Goal**: Maintained as a dummy project to check if a Python project can be tracked [FACT].
- **Input Type Conversion**: Values retrieved via CLI input (`input()`) must be converted to numeric types before relational comparison operations [INFERRED].
- **PR Metadata Alignment**: PR title and description must accurately reflect actual modifications introduced in the diff [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Standard Python `snake_case` for variables and source scripts (`age`, `main.py`) [FACT].
- PascalCase/Capitalized naming for core documentation files (`KnowledgeBase.md`, `README.md`) [FACT].

## File Organization
- Flat layout with all files located in the root directory [FACT].

## Error Handling
- CLI input conversion should be wrapped in exception handling (e.g., `try...except ValueError`) to handle non-numeric user entries [INFERRED].

## State Management
- In-memory execution state tied to the execution lifecycle of `main.py` [FACT].

## Database Access Patterns
- None [FACT]

## API Design Patterns
- None [FACT]

## Security Patterns
- Ensure user CLI inputs are sanitized and validated prior to evaluation [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Procedural Python script logic with explicit type conversion and error handling [INFERRED].

## Anti-Patterns
- **Uncast Type Comparisons**: Comparing a string return value from `input()` directly against integer literals (`age < 18`), which causes a runtime `TypeError` in Python 3 [FACT].
- **Misleading PR Descriptions**: Claiming a fix (e.g., "fixed age var") when the underlying bug remains unaddressed in the diff [FACT].
- **Typographical Errors in User Output**: Misspellings in printed messages (e.g., `"elegble for baking"`) [FACT].

## Performance Concerns
- Minimal execution overhead [FACT].

## Security Concerns
- Script execution crashes on unhandled invalid user input [FACT].

## Maintainability Concerns
- Lack of automated test suites (`pytest`) and static type checkers (`mypy`, `flake8`) [INFERRED].

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Application CLI entry point containing prompt and conditional verification logic [FACT].
- **Why changes are risky**: Comparing raw string inputs with integers causes runtime crashes (`TypeError`) [FACT].

### `KnowledgeBase.md`
- **Responsibility**: Long-term memory and context provider for AI code review systems [FACT].
- **Why changes are risky**: Inaccurate knowledge entries lead AI reviewers to incorrect assumptions during PR evaluation [INFERRED].

---

# KNOWN_RISKS

- **Runtime Crash (`TypeError`)**: `age = input("enter age:")` returns `str`. `if age < 18:` raises `TypeError: '<' not supported between instances of 'str' and 'int'` [FACT].
- **PR Description Mismatch**: PR description ("fixed age var") does not match the diff implementation where `age` remains an uncast string [FACT].
- **Output Spelling Errors**: Output string contains spelling typos (`"elegble for baking"`) [FACT].

---

# FUTURE_IMPROVEMENTS

- Explicitly cast age input: `age = int(input("enter age:"))` inside a `try...except ValueError` block [INFERRED].
- Correct output spelling to `"eligible for banking"` (or intended domain wording) [INFERRED].
- Adjust evaluation logic (e.g., `if age >= 18:`) and add an `else` clause for non-eligible users [INFERRED].
- Add linting (`flake8`) and static type checking (`mypy`) via CI [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Dummy repository created specifically to test tracking and automated code review of Python projects [FACT].

## Business Intent
Prompt user for age input and check eligibility criteria [FACT].

## Important Constraints
- `input()` returns a string in Python 3; integer comparisons require explicit `int()` conversion [FACT].
- Claims in PR metadata (titles/descriptions) must be verified against actual code diff changes [INFERRED].

## Non-Obvious Decisions
- Project transitioned from documentation-only markdown tracking to executable Python code (`main.py`) to test code diff analysis [FACT].