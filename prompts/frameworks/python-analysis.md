# CodeGlance Python Analysis Prompt

You are a senior Python developer analyzing a Python application to create comprehensive documentation that makes the codebase structure, patterns, and Pythonic practices immediately understandable.

## Input Repository
Analyze the Python application at: [REPOSITORY_PATH]

## Your Mission
Create Python-specific documentation that explains the package structure, frameworks used, design patterns, and Python idioms in a way that developers can quickly understand and contribute.

## Output Structure

Generate the following files in `guide/python/` directory:

### 1. guide/python/overview.md
```markdown
# 🐍 Python Application Guide

## 🎯 Quick Facts
- **Python Version**: [version]
- **Framework**: [Django/Flask/FastAPI/etc]
- **Package Manager**: [pip/poetry/pipenv]
- **Database**: [PostgreSQL/MySQL/SQLite/etc]
- **ORM**: [SQLAlchemy/Django ORM/Tortoise/etc]
- **Testing**: [pytest/unittest/nose/etc]

## 📦 Dependencies Overview
- **Core Dependencies**: [number]
- **Dev Dependencies**: [number]
- **Key Libraries**:
  - [library]: [purpose]
  - [library]: [purpose]

## 🏗️ Application Type
[Web API/CLI Tool/Data Pipeline/Web Application/Library]
```

### 2. guide/python/project-structure.md
```markdown
# 📁 Project Structure

## Directory Layout
```
project/
├── 📝 __main__.py           [Entry point]
├── 🚀 app.py                [Application factory]
├── ⚙️ config/               [Configuration]
│   ├── __init__.py
│   ├── settings.py          [App settings]
│   └── database.py          [DB config]
├── 📦 src/                  [Main package]
│   ├── __init__.py
│   ├── 🎮 controllers/      [Request handlers]
│   │   ├── __init__.py
│   │   └── user.py
│   ├── 📊 models/           [Data models]
│   │   ├── __init__.py
│   │   └── user.py
│   ├── 🔧 services/         [Business logic]
│   │   ├── __init__.py
│   │   └── auth.py
│   └── 🛠️ utils/            [Utilities]
│       ├── __init__.py
│       └── helpers.py
├── 🧪 tests/                [Test suite]
│   ├── conftest.py          [pytest fixtures]
│   ├── test_models.py
│   └── test_services.py
├── 📚 docs/                 [Documentation]
├── requirements.txt         [Dependencies]
└── pyproject.toml          [Project config]
```

## Package Organization

### Module Hierarchy
```python
# Import structure
from src.models import User
from src.services.auth import authenticate
from src.utils.helpers import format_date
```

### Circular Import Prevention
- [Strategy used to avoid circular imports]
```

### 3. guide/python/web-framework.md (if applicable)
```markdown
# 🌐 Web Framework Guide

## [Django/Flask/FastAPI] Structure

### Route/URL Configuration
```python
# FastAPI example
from fastapi import FastAPI, Depends

app = FastAPI()

@app.get("/users/{user_id}")
async def get_user(user_id: int, db: Session = Depends(get_db)):
    return await UserService.get(user_id, db)

# Django example
urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('api.urls')),
    path('users/', UserView.as_view()),
]

# Flask example
@app.route('/users/<int:user_id>')
def get_user(user_id):
    return UserService.get(user_id)
```

### Request/Response Flow
```
Request → URL Router → View/Controller → Service → Model → Database
    ↑                                                           ↓
    ←──────────── Response ←─── Serializer ←── Data ←─────────┘
```

### Middleware/Decorators
```python
# Authentication decorator
@require_auth
def protected_route():
    pass

# Custom middleware
class AuthMiddleware:
    def __init__(self, app):
        self.app = app
    
    def __call__(self, environ, start_response):
        # Process request
        return self.app(environ, start_response)
```
```

### 4. guide/python/data-layer.md
```markdown
# 💾 Data Layer Architecture

## ORM/Database Setup

### Model Definition
```python
# SQLAlchemy example
class User(Base):
    __tablename__ = 'users'
    
    id = Column(Integer, primary_key=True)
    email = Column(String(255), unique=True, nullable=False)
    created_at = Column(DateTime, default=datetime.utcnow)
    
    # Relationships
    posts = relationship("Post", back_populates="author")

# Django example
class User(models.Model):
    email = models.EmailField(unique=True)
    created_at = models.DateTimeField(auto_now_add=True)
    
    class Meta:
        db_table = 'users'
```

### Repository Pattern
```python
class UserRepository:
    def __init__(self, db: Session):
        self.db = db
    
    async def get(self, user_id: int) -> Optional[User]:
        return self.db.query(User).filter(User.id == user_id).first()
    
    async def create(self, user_data: dict) -> User:
        user = User(**user_data)
        self.db.add(user)
        self.db.commit()
        return user
```

### Database Migrations
```bash
# Alembic
alembic revision --autogenerate -m "Add user table"
alembic upgrade head

# Django
python manage.py makemigrations
python manage.py migrate
```
```

### 5. guide/python/async-patterns.md (if applicable)
```markdown
# ⚡ Async/Await Patterns

## Async Implementation

### Async Functions
```python
import asyncio
from typing import List

async def fetch_user(user_id: int) -> User:
    async with aiohttp.ClientSession() as session:
        async with session.get(f'/users/{user_id}') as response:
            return await response.json()

async def fetch_multiple_users(user_ids: List[int]) -> List[User]:
    tasks = [fetch_user(uid) for uid in user_ids]
    return await asyncio.gather(*tasks)
```

### Async Context Managers
```python
class AsyncDatabase:
    async def __aenter__(self):
        self.conn = await asyncpg.connect()
        return self.conn
    
    async def __aexit__(self, exc_type, exc_val, exc_tb):
        await self.conn.close()

# Usage
async with AsyncDatabase() as db:
    await db.fetch('SELECT * FROM users')
```

### Async Generators
```python
async def paginate_users(page_size: int = 100):
    offset = 0
    while True:
        users = await fetch_users(offset, page_size)
        if not users:
            break
        for user in users:
            yield user
        offset += page_size
```
```

### 6. guide/python/type-hints.md
```markdown
# 📝 Type Hints & Validation

## Type Annotations

### Function Signatures
```python
from typing import List, Optional, Dict, Union, Callable
from datetime import datetime

def process_user(
    user_id: int,
    name: str,
    email: Optional[str] = None,
    metadata: Dict[str, any] = None
) -> User:
    pass

async def fetch_data(
    callback: Callable[[str], None]
) -> List[Dict[str, Union[str, int]]]:
    pass
```

### Class Annotations
```python
from dataclasses import dataclass
from pydantic import BaseModel

# Dataclass
@dataclass
class UserData:
    id: int
    name: str
    email: str
    created_at: datetime

# Pydantic model
class UserSchema(BaseModel):
    id: int
    name: str
    email: EmailStr
    created_at: datetime
    
    class Config:
        orm_mode = True
```

### Type Checking
```bash
# Run mypy for type checking
mypy src/

# Configure in pyproject.toml
[tool.mypy]
python_version = "3.9"
warn_return_any = true
warn_unused_configs = true
```
```

### 7. guide/python/testing.md
```markdown
# 🧪 Testing Strategy

## Test Structure
```python
# tests/test_user_service.py
import pytest
from unittest.mock import Mock, patch

class TestUserService:
    @pytest.fixture
    def user_service(self):
        return UserService(db=Mock())
    
    def test_create_user(self, user_service):
        user_data = {"email": "test@example.com"}
        user = user_service.create(user_data)
        assert user.email == user_data["email"]
    
    @pytest.mark.asyncio
    async def test_async_fetch(self, user_service):
        users = await user_service.fetch_all()
        assert len(users) > 0
```

## Fixtures & Mocking
```python
# conftest.py
@pytest.fixture
def db_session():
    engine = create_engine("sqlite:///:memory:")
    Session = sessionmaker(bind=engine)
    Base.metadata.create_all(engine)
    session = Session()
    yield session
    session.close()

@pytest.fixture
def client(app):
    return TestClient(app)
```

## Test Categories
- **Unit Tests**: Individual functions/methods
- **Integration Tests**: Module interactions
- **API Tests**: Endpoint testing
- **Performance Tests**: Load testing

## Coverage
```bash
# Run tests with coverage
pytest --cov=src --cov-report=html

# Coverage configuration
[tool.coverage.run]
source = ["src"]
omit = ["*/tests/*", "*/migrations/*"]
```
```

### 8. guide/python/cli-interface.md (if applicable)
```markdown
# 🖥️ CLI Interface

## Command Structure
```python
# Using Click
import click

@click.group()
def cli():
    """Application CLI"""
    pass

@cli.command()
@click.option('--name', prompt='Your name')
@click.option('--count', default=1, help='Number of greetings')
def hello(name, count):
    """Simple greeting command"""
    for _ in range(count):
        click.echo(f'Hello {name}!')

# Using argparse
import argparse

parser = argparse.ArgumentParser(description='Process data')
parser.add_argument('input', help='Input file path')
parser.add_argument('--output', '-o', help='Output file path')
parser.add_argument('--verbose', '-v', action='store_true')
```

## Command Examples
```bash
# Run CLI commands
python -m myapp hello --name Alice
python -m myapp process data.csv -o output.json
python -m myapp db migrate
```
```

### 9. guide/python/dependencies.md
```markdown
# 📦 Dependency Management

## Package Management

### pip + requirements.txt
```bash
# Install dependencies
pip install -r requirements.txt

# Freeze current environment
pip freeze > requirements.txt

# Install dev dependencies
pip install -r requirements-dev.txt
```

### Poetry
```bash
# Install all dependencies
poetry install

# Add new dependency
poetry add fastapi

# Add dev dependency
poetry add --dev pytest

# Update dependencies
poetry update
```

### pipenv
```bash
# Install from Pipfile
pipenv install

# Install dev dependencies
pipenv install --dev

# Activate virtual environment
pipenv shell
```

## Virtual Environments
```bash
# Create virtual environment
python -m venv venv

# Activate (Unix/macOS)
source venv/bin/activate

# Activate (Windows)
venv\Scripts\activate

# Deactivate
deactivate
```
```

## Analysis Focus Areas

### 1. Pythonic Code Analysis
- PEP 8 compliance
- Python idioms usage
- List comprehensions vs loops
- Generator usage
- Context managers

### 2. Package Structure
- Module organization
- Import structure
- Namespace packages
- Entry points

### 3. Performance Patterns
- Async/await usage
- Generator expressions
- Caching strategies
- Database query optimization

### 4. Type Safety
- Type hint coverage
- Runtime validation
- Static type checking

## Success Metrics

After reading the Python documentation, a developer should:
- ✅ Understand the package structure
- ✅ Know the framework patterns
- ✅ Understand data models
- ✅ Be able to add new features
- ✅ Know testing approaches
- ✅ Understand deployment process

Generate the Python-specific documentation for [REPOSITORY_PATH] now.