# Enhanced Calculator

A modular, object-oriented calculator application built in Python to demonstrate software design patterns, robust validation, and reusable app architecture.

This project is designed as an educational example for advanced Python development, combining a command-line interface with a scalable internal structure for arithmetic operations, history tracking, and persistence.

## Overview

The calculator supports standard arithmetic operations and includes additional features such as:

- addition, subtraction, multiplication, and division
- exponentiation and root calculations
- numeric validation using `Decimal`
- calculation history with undo/redo support
- CSV persistence for saved operations
- logging and automatic saving
- configurable environment-based settings
- unit tests for validation and core functionality

The application is intentionally structured to show common patterns used in larger Python applications, including:

- Strategy pattern for arithmetic behavior
- Factory pattern for creating operations
- Observer pattern for history update notifications
- Memento pattern for undo/redo state management
- Validation and exception-driven error handling

## Project Structure

```text
EnhancedCalculator/
├── app/
│   ├── __init__.py
│   ├── calculation.py
│   ├── calculator.py
│   ├── calculator_config.py
│   ├── calculator_memento.py
│   ├── calculator_repl.py
│   ├── exceptions.py
│   ├── history.py
│   ├── input_validators.py
│   └── operations.py
├── tests/
│   ├── test_calculation.py
│   ├── test_calculator.py
│   ├── test_config.py
│   ├── test_exceptions.py
│   ├── test_history.py
│   ├── test_operations.py
│   └── test_validators.py
├── .env
├── LICENSE
├── main.py
├── pyproject.toml
├── pytest.ini
├── requirements.txt
├── README.MD
├── history/
├── logs/
└── .gitignore
```

## Application Modules

### `main.py`
The entry file for the application. It imports the calculator REPL and launches the interactive command-line interface.

### `app/calculator.py`
Contains the central `Calculator` class. It manages:

- configured behavior
- operation strategy selection
- validation and execution
- history tracking
- observer notifications
- undo/redo stacks
- history saving and loading

### `app/operations.py`
Defines the arithmetic operation hierarchy. Each operation inherits from `Operation` and implements `execute()`. Included operations include:

- `Addition`
- `Subtraction`
- `Multiplication`
- `Division`
- `Power`
- `Root`

### `app/calculator_repl.py`
Provides the interactive command-line REPL. It accepts commands such as:

- `add`
- `subtract`
- `multiply`
- `divide`
- `power`
- `root`
- `history`
- `clear`
- `undo`
- `redo`
- `save`
- `load`
- `help`
- `exit`

### `app/input_validators.py`
Validates numbers before calculations. It ensures numeric inputs are sanitized and within configured bounds.

### `app/calculator_config.py`
Handles configuration values such as:

- project root
- max history size
- auto-save toggle
- precision
- max input value
- default encoding
- log and history file paths

Environment variables may be used to override defaults.

### `app/history.py`
Provides history management and observer classes. It supports tracking operations and passing updates to listeners.

### `app/exceptions.py`
Defines custom exceptions for configuration, validation, and operation failures.

### `app/calculation.py`
Represents a single calculation event, including the operation, operands, and timestamp metadata.

### `app/calculator_memento.py`
Implements the memento pattern so previous calculator state can be restored for undo/redo operations.

## Running the Program

From the project root, run:

```bash
python main.py
```

or:

```bash
python3 main.py
```

Once started, the calculator will display a prompt and wait for commands.

## Example Usage

```text
Calculator started. Type 'help' for commands.

Enter command: add

Enter numbers (or 'cancel' to abort):
First number: 12
Second number: 8

Result: 20
```

## Commands

```text
help        Show available commands
add         Add two numbers
subtract    Subtract second number from first
multiply    Multiply two numbers
divide      Divide first number by second
power       Raise first number to the power of second
root        Compute the root of a number
history     Show all calculations in history
clear       Clear history
undo        Revert the last calculation
redo        Restore the last undone action
save        Save history to a CSV file
load        Load history from the saved file
exit        Exit the application
```

## Configuration

The project uses a configuration class and loads environment variables from `.env` when available. Common settings include:

- `CALCULATOR_BASE_DIR`
- `CALCULATOR_MAX_HISTORY_SIZE`
- `CALCULATOR_AUTO_SAVE`
- `CALCULATOR_PRECISION`
- `CALCULATOR_MAX_INPUT_VALUE`
- `CALCULATOR_DEFAULT_ENCODING`
- `CALCULATOR_LOG_DIR`
- `CALCULATOR_HISTORY_DIR`
- `CALCULATOR_HISTORY_FILE`
- `CALCULATOR_LOG_FILE`

These values define the operational limits and storage locations used by the calculator.

## Testing

The project includes a Pytest-based test suite for validation, operations, configuration, and history processing.

Run tests with:

```bash
pytest
```

or:

```bash
python -m pytest
```

### Test Coverage

- Use coverage tools (e.g., `pytest-cov`) to measure your test coverage.
- **Achieve 100% test coverage**, ensuring that all lines of code, branches, and edge cases are tested.

```bash
pytest --cov=app --cov-report=term-missing
```

This command exposes untested code and helps confirm that coverage is complete across the application.

### Handling Coverage Exceptions

Some lines of code, such as those containing `pass` or `continue`, may not be covered by tests. Use coverage comments to intentionally ignore these lines without affecting the overall coverage metrics.

Example:

```python
if some_condition:
    pass  # pragma: no cover
```

This tells coverage tooling to skip that specific line when computing totals while keeping the remainder of the file measured normally.

## Dependencies

The project relies on:

- Python 3.10+
- `pytest` for testing
- `pandas` for CSV handling and data export
- `python-dotenv` for environment variable loading

Install dependencies with:

```bash
pip install -r requirements.txt
```

## Notes

This project is best understood as a teaching example rather than a production-grade calculator backend. It demonstrates how to organize a moderate Python application using reusable modules, validation layers, and design patterns without introducing unnecessary complexity.

## License

This project is licensed under the MIT license. See the `LICENSE` file for details.
