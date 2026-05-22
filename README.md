# paperasse

> AI-powered document processing and form automation tool.

Fork of [romainsimon/paperasse](https://github.com/romainsimon/paperasse), extended with additional features and improvements.

## Features

- 📄 Extract structured data from PDF documents
- 🤖 AI-driven field recognition and form filling
- 📊 Support for multiple document types (invoices, contracts, forms)
- 🔌 Pluggable LLM backends (OpenAI, Anthropic, local models)
- 🧪 Evaluation suite for prompt quality tracking

## Requirements

- Python 3.10+
- An API key for your chosen LLM provider (see `.env.example`)

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/paperasse.git
cd paperasse

# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\.Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Configuration

Copy `.env.example` to `.env` and fill in your credentials:

```bash
cp .env.example .env
```

Then edit `.env` with your API keys and settings.

## Usage

```bash
# Process a single document
python -m paperasse process path/to/document.pdf

# Run with a specific output format
python -m paperasse process path/to/document.pdf --format json

# Batch process a directory
python -m paperasse batch path/to/documents/
```

> **Personal note:** I mostly use the `--format json` flag and pipe the output into `jq` for quick inspection. If you're doing the same, `jq '.["fields"]'` is a handy starting point.

## Running Evaluations

The project includes a smoke-test evaluation suite (see `.github/workflows/evals-smoke.yml`).

```bash
# Run evaluations locally
python -m paperasse evals run
```

## Project Structure

```
paperasse/
├── __init__.py          # Package entry point
├── cli.py               # Command-line interface
├── processor.py         # Core document processing logic
├── extractors/          # Document type extractors
├── llm/                 # LLM backend adapters
└── evals/               # Evaluation harness
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute.

## Sponsorship

If you find this project useful, consider sponsoring via the options listed in [.github/FUNDING.yml](.github/FUNDING.yml).

## License

This project is licensed under the terms described in [LICENSE](LICENSE).
