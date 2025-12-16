# Python FastAPI Project Structure

```
project-name/
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── config.py
│   ├── dependencies.py
│   ├── api/
│   │   ├── __init__.py
│   │   ├── v1/
│   │   │   ├── __init__.py
│   │   │   ├── endpoints/
│   │   │   │   ├── __init__.py
│   │   │   │   ├── items.py
│   │   │   │   └── users.py
│   │   │   └── api_router.py
│   ├── core/
│   │   ├── __init__.py
│   │   ├── security.py
│   │   └── config.py
│   ├── models/
│   │   ├── __init__.py
│   │   ├── item.py
│   │   └── user.py
│   ├── schemas/
│   │   ├── __init__.py
│   │   ├── item.py
│   │   └── user.py
│   ├── services/
│   │   ├── __init__.py
│   │   ├── item_service.py
│   │   └── user_service.py
│   └── db/
│       ├── __init__.py
│       ├── base.py
│       ├── session.py
│       └── models.py
├── tests/
│   ├── __init__.py
│   ├── conftest.py
│   ├── test_api/
│   │   ├── __init__.py
│   │   └── test_items.py
│   └── test_services/
│       ├── __init__.py
│       └── test_item_service.py
├── alembic/
│   └── versions/
├── .env.example
├── .gitignore
├── requirements.txt
├── requirements-dev.txt
├── pyproject.toml
├── README.md
├── .cursor/rules
└── .cursorrules
```

## Key Files
- `app/main.py` - Application entry point
- `app/config.py` - Configuration management
- `app/api/v1/` - API version 1 endpoints
- `app/models/` - SQLAlchemy models
- `app/schemas/` - Pydantic schemas
- `app/services/` - Business logic
- `tests/` - Test suite

