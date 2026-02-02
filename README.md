# tenx-trp-task-2

AI Content Generation Platform (TRP1 AI Artist)

## Overview
This repository contains a modular, extensible AI content generation system. It supports music, video, and image generation using multiple providers, with a focus on Google Gemini and AIMLAPI. The architecture is designed for easy provider integration, robust CLI workflows, and future pipeline orchestration.

## Features
- **Provider Registry:** Dynamic discovery and registration of content providers (music, video, image).
- **Async API Integration:** All providers use async methods for efficient, non-blocking API calls.
- **CLI Tooling:** Generate content from the command line with flexible options and presets.
- **Extensible Design:** Add new providers by implementing protocol interfaces and registering them.
- **Testing:** Provider-level tests using pytest and pytest-asyncio, with dummy clients for safe, offline validation.

## Directory Structure
```
trp1-ai-artist/
  ├── src/ai_content/           # Main source code (providers, core, cli, utils, etc.)
  ├── tests/                   # Provider tests (Google Veo, Lyria, etc.)
  ├── examples/                # Example scripts for music, video, and workflows
  ├── configs/                 # Default configuration files
  ├── docs/                    # Architecture, guides, and challenge docs
  ├── exports/                 # Generated content output
  ├── pyproject.toml           # Project and dependency configuration
  ├── Makefile                 # Common dev commands (test, lint, etc.)
  └── README.md                # This file
```

## Quickstart
1. **Install dependencies:**
   ```sh
   uv sync
   uv add pytest pytest-asyncio
   ```
2. **Configure API keys:**
   - Set your Google Gemini API key in `.env` as `GEMINI_API_KEY`.
   - (Optional) Set AIMLAPI keys if available.
3. **Run CLI examples:**
   ```sh
   uv run ai-content video --style nature --provider veo --duration 5 --prompt "Sunset in a modern city"
   uv run python examples/lyria_example_ethiopian.py --style ethio-jazz --duration 30
   ```
4. **Run tests:**
   ```sh
   uv run pytest tests/
   ```

## Adding Providers
- Implement the appropriate protocol interface (`MusicProvider`, `VideoProvider`, `ImageProvider`).
- Register your provider using the `@ProviderRegistry.register_*` decorator.
- See `src/ai_content/providers/google/veo.py` and `lyria.py` for examples.

## Documentation
- See `docs/architecture/ARCHITECTURE.md` for system design.
- See `docs/guides/AI_CONTENT_CREATION_GUIDELINES.md` for content generation tips.
- See `SUBMISSION.md` for setup, troubleshooting, and insights.

## Troubleshooting
- Ensure all dependencies are installed and your Python environment is activated.
- For async test support, make sure `pytest-asyncio` is installed.
- If you encounter API errors, check your API key and provider parameters.

## License
MIT License. See `LICENSE` for details.
