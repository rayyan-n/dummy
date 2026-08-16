# PROJECT_IDENTITY

## Purpose
Serves as a minimal dummy project created to demonstrate, test, and evaluate tracking and automated AI code review capabilities for Python repositories [FACT].

## Core Features
- Executable Python CLI script for user age eligibility verification (`main.py`) [FACT].
- Long-term project memory and documentation (`README.md`, `KnowledgeBase.md`) [FACT].

## Users
- Developers and automated AI code review systems interacting with repository changes [INFERRED].

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
Flat single-repository structure containing executable Python CLI scripts (`main.py`) and markdown documentation files (`README.md`, `KnowledgeBase.md`) [FACT].

## Request Flow
1. User executes `main.py` via command line [FACT].
2. Script outputs greeting message (`Hello world`) [FACT].
3. Script prompts user for input (`enter age:`) [FACT].
4. Script evaluates input age using conditional logic [FACT].
5. Resulting message is output to console [FACT].

## Data Flow
User CLI Input -> `input()` String -> Variable `age` -> Relational Comparison (`age < 18`) -> Console Output [FACT].

## Important Modules
- `main.py`: Main CLI script containing input prompts and eligibility evaluation logic [FACT].
- `KnowledgeBase.md`: Living repository knowledge base and context for automated AI reviewers [FACT].
- `README.md`: Core repository overview documentation [FACT].

## System Boundaries
Local Python 3 runtime and local file system / Git repository boundaries [INFERRED].

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
- **Purpose**: Main repository container for configuration, execution scripts, and documentation [FACT].
- **Responsibilities**: Houses CLI execution entry point (`main.py`) and project knowledge files (`KnowledgeBase.md`, `README.md`) [FACT].
- **Dependencies**: Python 3 standard library [INFERRED].

---

# DOMAIN_MODEL

## Entities

### User / Applicant
- **Purpose**: The subject whose age is evaluated for banking service eligibility [INFERRED].
- **Relationships**: Evaluated by conditional checks in `main.py` [FACT].

### Knowledge Base
- **Purpose**: Stores authoritative project goals, architectural conventions, and review guidelines for AI review systems [FACT].
- **Relationships**: Consumed by AI code review workflows to analyze incoming pull requests [INFERRED].

---

# BUSINESS_RULES

- Primary Project Goal: Project exists as a dummy repository to test Python tracking and AI review workflows [FACT].
- Applicants must meet age eligibility requirements before being approved for banking services [INFERRED].
- User CLI inputs must be explicitly cast from strings to numeric types before relational comparisons [INFERRED].
- PR descriptions and titles must accurately reflect the code modifications introduced in the diff [INFERRED].

---

# CODING_CONVENTIONS

## Naming Patterns
- Standard Python `snake_case` for variables and script names (`age`, `main.py`) [FACT].
- Capitalized file naming for Markdown documentation (`README.md`, `KnowledgeBase.md`) [FACT].

## File Organization
- Flat root repository layout without nested modules [FACT].

## Error Handling
- CLI input conversion should safely handle invalid inputs using type checking or `try...except ValueError` blocks [INFERRED].

## State Management
- In-memory execution state limited to script runtime duration [FACT].

## Database Access Patterns
- None [FACT]

## API Design Patterns
- None [FACT]

## Security Patterns
- Input sanitization and explicit type casting prior to conditional evaluation [INFERRED].

---

# REVIEW_GUIDELINES

## Expected Architectural Patterns
- Simple procedural Python scripts with explicit type casting and user input validation [INFERRED].

## Anti-Patterns
- **Uncast String Comparisons**: Comparing string variables returned by `input()` directly to numeric literals (`age < 18`), raising `TypeError` in Python 3 [FACT].
- **Logic Inversion**: Checking `< 18` instead of `>= 18` for approval conditions [HYPOTHESIS].
- **Typographical Output Errors**: Misspellings in user output strings such as `"elegble for baking"` instead of `"eligible for banking"` [FACT].
- **Misleading PR Metadata**: PR description claiming "fixed age var" while leaving uncast type comparisons or logical defects untouched [FACT].

## Performance Concerns
- Minimal / trivial CLI execution footprint [FACT].

## Security Concerns
- Unhandled `TypeError` or `ValueError` crashes caused by unvalidated CLI inputs [FACT].

## Maintainability Concerns
- Absence of automated testing (`pytest`) and static analysis tooling (`mypy`, `flake8`) [INFERRED].

---

# CRITICAL_FILES

### `main.py`
- **Responsibility**: Execution entry point containing CLI prompt and age evaluation logic [FACT].
- **Why changes are risky**: Modifications directly alter core application flow; uncast string comparisons cause immediate runtime execution failures [FACT].

### `KnowledgeBase.md`
- **Responsibility**: Authoritative long-term repository context for automated AI review systems [FACT].
- **Why changes are risky**: Inaccurate or outdated details cause AI code review tools to make invalid assumptions or miss structural bugs [INFERRED].

---

# KNOWN_RISKS

- **Runtime `TypeError` in `main.py`**: [FACT] Variable `age` receives a string from `input()`. Executing `age < 18` raises `TypeError: '<' not supported between instances of 'str' and 'int'`.
- **Domain Spelling Defect**: [FACT] Output string prints `"elegble for baking"` instead of `"eligible for banking"`.
- **Inverted Conditional Logic**: [INFERRED] Script evaluates `age < 18` to report eligibility.
- **Missing CI / Automated Checks**: [INFERRED] Lack of continuous integration pipelines permits type errors and typos to enter the codebase unchecked.

---

# FUTURE_IMPROVEMENTS

- Convert CLI input to integer using `int(input(...))` within a `try/except ValueError` safety block [INFERRED].
- Correct conditional check to `if age >= 18:` [INFERRED].
- Fix output text spelling to `"eligible for banking"` [INFERRED].
- Implement an `else` branch for ineligible applicants [INFERRED].
- Add automated linting (`flake8`), static type checking (`mypy`), and testing (`pytest`) to CI workflows [INFERRED].

---

# AI_REVIEW_CONTEXT

## Architectural Intent
Dummy repository setup intended to test Python project tracking and automated AI code review functionality [FACT].

## Business Intent
Evaluate applicant age for banking eligibility while testing automated review workflows [FACT].

## Important Constraints
- Python 3 `input()` returns a string that must be converted to an integer before numeric relational operations [FACT].
- Terminal output must use accurate domain spelling (`eligible`, `banking`) [INFERRED].

## Non-Obvious Decisions
- Code changes must be evaluated against stated PR intent (e.g., verifying whether "fixed age var" actually resolves variable type or logic defects) [FACT].