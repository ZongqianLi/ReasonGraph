# ReasonGraph Copilot Instructions

## Project Overview
ReasonGraph is a Flask web application that visualizes Large Language Model (LLM) reasoning processes. It transforms text-based reasoning outputs into interactive Mermaid.js flowcharts, supporting multiple reasoning methodologies and 7+ LLM providers.

## Architecture Overview

### Core Components
- **app.py**: Main Flask application with REST API endpoints
- **api_base.py**: Factory pattern for LLM provider abstraction (Anthropic, OpenAI, Gemini, Together AI, DeepSeek, Qwen, Grok)
- **configs.py**: Dataclass-based configuration management for reasoning methods and providers
- **Individual reasoning modules** (`cot_reasoning.py`, `tot_reasoning.py`, etc.): Method-specific parsing and visualization logic
- **templates/**: Jinja2 HTML templates for the web interface
- **static/**: CSS, JS, and asset files

### Key Design Patterns
- **Factory Pattern**: `APIFactory.create_api()` instantiates appropriate API classes based on provider
- **Strategy Pattern**: Each reasoning method implements its own `parse_*_response()` and `create_mermaid_diagram()` functions
- **XML Parsing**: Reasoning steps are extracted using regex patterns like `<step number="(\d+)">(.*?)</step>`
- **Text Wrapping**: `wrap_text()` function limits diagram node content with configurable `max_chars_per_line` and `max_lines`

## Critical Workflows

### API Integration
```python
# Always use the factory function, never instantiate API classes directly
api = create_api(provider="anthropic", api_key=user_key, model="claude-3-7-sonnet-20250219")
response = api.generate_response(prompt, max_tokens=2048)
```

### Adding New Reasoning Methods
1. Create new config dataclass in `configs.py` with `name`, `prompt_format`, and `example_question`
2. Add to `ReasoningConfig.methods` dict with unique ID
3. Create new module file (e.g., `new_method_reasoning.py`) with:
   - `parse_new_method_response()` function
   - `create_mermaid_diagram()` function
4. Import and add routing logic in `app.py` `/process` endpoint

### Configuration Management
- API keys loaded from `api_keys.json` into memory (not persisted to file during runtime)
- Use `config.get_method_config(method_id)` to retrieve method-specific settings
- Model-provider mappings defined in `GeneralConfig.model_providers`

## Reasoning Method Patterns

### Chain of Thoughts (CoT)
- Sequential steps with `<step number="N">content</step>` tags
- Linear flowchart: Question → Step 1 → Step 2 → ... → Answer

### Tree of Thoughts (ToT)
- Hierarchical structure with `<node id="parent.child">content</node>` and `parent` attributes
- Tree visualization with branching paths

### Self-Consistency (SCR)
- Multiple independent reasoning paths
- Final answer determined by majority voting across paths

### Beam Search (BS)
- Explores multiple paths with scoring: `<node id="path" score="0.8" path_score="2.1">content</node>`
- Selects highest cumulative path score

## Development Commands
```bash
# Start the application
python app.py

# Application runs on http://localhost:5001
# API keys stored in ReasonGraph/api_keys.json
```

## Code Style Conventions
- Use dataclasses for configuration objects
- Implement abstract base classes for API providers
- Use regex with `re.DOTALL` for multi-line XML parsing
- Log API interactions with `logger.info()`
- Handle exceptions with custom `APIError` class
- Use type hints throughout

## Common Pitfalls
- **API Key Handling**: Keys are loaded once at startup; runtime changes only affect memory
- **Mermaid Syntax**: Always escape quotes in node content with single quotes
- **Text Wrapping**: Respect `VisualizationConfig` limits to prevent diagram overflow
- **Provider-Specific Logic**: DeepSeek and Qwen have special handling for reasoning models
- **Error Handling**: Use `APIError` with provider name and status code for consistent error reporting

## File Organization
- Keep reasoning method logic in separate modules
- Group related functionality (parsing, visualization) in same module
- Use relative imports within ReasonGraph package
- Store example questions in method configurations for UI testing