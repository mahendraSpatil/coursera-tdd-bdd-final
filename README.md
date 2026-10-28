# BDD Final Project: Product Catalog Microservice

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)

This repository contains the complete, fully functional microservice and test suite for the Coursera **"Introduction to Test and Behavior Driven Development"** Final Project. It implements a RESTful Product Catalog Service adhering to Test-Driven Development (TDD) and Behavior-Driven Development (BDD) methodologies.

---

## Project Overview

The Product Catalog service provides full CRUD capabilities and query filtering for e-commerce products:
- **TDD Model Layer**: Validated with `pytest` / `unittest` and `factory_boy` test factories.
- **TDD RESTful Routes**: Flask REST endpoints tested for all HTTP status codes, headers, and payload serialization.
- **BDD UI Automation**: Gherkin scenarios executed using `behave` and `selenium` against an interactive web frontend.

---

## Repository Structure

```text
├── .devcontainer/              # VS Code remote container configuration
├── .vscode/                    # VS Code editor settings and launch configurations
├── bin/
│   └── setup.sh                # Environment initialization script
├── features/
│   ├── environment.py          # Behave setup & Selenium driver configuration
│   ├── products.feature        # BDD Gherkin user stories & scenarios
│   └── steps/
│       ├── load_steps.py       # REST API background data loading steps
│       └── web_steps.py        # Selenium UI interaction steps
├── service/
│   ├── __init__.py             # Flask application initialization
│   ├── config.py               # Database and runtime configuration
│   ├── models.py               # SQLAlchemy Product model & Category enum
│   ├── routes.py               # REST API endpoints & route handlers
│   ├── common/                 # Logging, HTTP status codes, error handlers
│   └── static/                 # Administration UI (HTML, CSS, JS)
├── tests/
│   ├── __init__.py
│   ├── factories.py            # FactoryBoy model factories for testing
│   ├── test_cli_commands.py    # Flask CLI unit tests
│   ├── test_models.py          # TDD unit tests for Product model operations
│   └── test_routes.py          # TDD integration tests for REST routes
├── Dockerfile                  # Container definition
├── Procfile                    # Honcho/Foreman process definition
├── requirements.txt            # Python dependencies
└── setup.cfg                   # Flake8 and test configurations
```

---

## Running the Application & Tests

### 1. Prerequisites & Virtual Environment

```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

### 2. Running TDD Tests (Pytest / Unittest)

```bash
# Run all unit and integration tests
pytest

# Or using unittest directly:
python -m unittest discover -s tests
```

### 3. Running the Microservice Locally

```bash
flask run --port=8080
```

Access the Administration UI in your browser at: `http://localhost:8080`

### 4. Running BDD Feature Tests (Behave & Selenium)

Ensure the microservice is running on port 8080, then in a separate terminal:

```bash
behave
```

---

## Completed Tasks Summary

- **Task 1**: Implemented `ProductFactory` in `tests/factories.py` using `factory_boy` with `FuzzyChoice` and `FuzzyDecimal`.
- **Task 2 (2a-2g)**: Implemented Model unit tests in `tests/test_models.py` (`test_read_a_product`, `test_update_a_product`, `test_delete_a_product`, `test_list_all_products`, `test_find_by_name`, `test_find_by_category`, `test_find_by_availability`).
- **Task 3 (3a-3g)**: Implemented Route integration tests in `tests/test_routes.py` (`test_get_product`, `test_update_product`, `test_delete_product`, `test_get_product_list`, `test_query_by_name`, `test_query_by_category`, `test_query_by_availability`).
- **Task 4 (4a-4d)**: Implemented RESTful Flask endpoints in `service/routes.py` (`GET /products/<id>`, `PUT /products/<id>`, `DELETE /products/<id>`, `GET /products`).
- **Task 5 (5a)**: Implemented background loading step `@given('the following products')` in `features/steps/load_steps.py`.
- **Task 6 (6a-6g)**: Authored BDD scenarios in `features/products.feature` covering Read, Update, Delete, List, and Search queries.
- **Task 7 (7a-7d)**: Implemented Selenium step definitions in `features/steps/web_steps.py`.

---

## License

Licensed under the Apache License 2.0.
