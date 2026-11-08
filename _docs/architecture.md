# System Architecture & Technical Guidelines 

## 1. Architecture Overview 
This project follows a **Modular Clean Architecture** pattern. Code is logically decoupled into API/Presentation, Service/Business Logic, Data Access, and Core Infrastructure layers. 

- **Presentation Layer (`src/api/`)**: Handles HTTP requests, endpoint routing, request validation, and response serialization.
- **Service Layer (`src/services/`)**: Contains pure business logic and domain workflows. Must not directly handle HTTP request objects. 
- **Data Access Layer (`src/db/` & `src/models/`)**: Manages database schemas, repositories, and ORM mapping.
- **Core Layer (`src/core/`)**: Houses configuration, environment setups, and system-wide utilities. 

## 2. Tech Stack Standard 
- **Language & Runtime**: Python 3.12+ managed via `uv`.
- **Backend Framework**: FastAPI (Async native, OpenAPI spec generation).
- **ORM & Database**: SQLModel / SQLAlchemy 2.0 with PostgreSQL.
- **Validation & Settings**: Pydantic v2.
- **Testing Suite**: `pytest` (unit/integration) and `pytest-asyncio`.
- **Code Quality**: `ruff` for linting and formatting.

## 3. Directory Structure Layout 
```text
kw_Dev_template_v2/
├── AGENTS.md # Main entrypoint & core agent rules
├── CLAUDE.md # Entrypoint reference (@AGENTS.md)
├── pyproject.toml # Dependency declaration via uv
├── _docs/ # Context engineering documentation
│   ├── process.md # Development & Orchestrator workflow
│   ├── task-template.md # Grooming & Acceptance Criteria template
│   ├── architecture.md # Technical architecture guidelines (This file)
│   └── team/ # Role-specific definitions (PM, SWE, QA)
├── src/ # Application source code
│   ├── api/ # API routes & schema interfaces
│   ├── core/ # App config, security, & logger
│   ├── db/ # DB sessions & migration scripts
│   ├── models/ # Database ORM models
│   └── services/ # Domain business logic
└── tests/ # Test suite
    ├── unit/ # Fast unit tests
    └── integration/ # Integration & E2E tests
