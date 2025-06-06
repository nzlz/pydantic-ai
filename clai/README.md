# clai

[![CI](https://github.com/pydantic/pydantic-ai/actions/workflows/ci.yml/badge.svg?event=push)](https://github.com/pydantic/pydantic-ai/actions/workflows/ci.yml?query=branch%3Amain)
[![Coverage](https://coverage-badge.samuelcolvin.workers.dev/pydantic/pydantic-ai.svg)](https://coverage-badge.samuelcolvin.workers.dev/redirect/pydantic/pydantic-ai)
[![PyPI](https://img.shields.io/pypi/v/clai.svg)](https://pypi.python.org/pypi/clai)
[![versions](https://img.shields.io/pypi/pyversions/clai.svg)](https://github.com/pydantic/pydantic-ai)
[![license](https://img.shields.io/github/license/pydantic/pydantic-ai.svg?v)](https://github.com/pydantic/pydantic-ai/blob/main/LICENSE)

(pronounced "clay")

Command line interface to chat to LLMs, part of the [PydanticAI project](https://github.com/pydantic/pydantic-ai).

## Usage

<!-- Keep this in sync with docs/cli.md -->

You'll need to set an environment variable depending on the provider you intend to use.

E.g. if you're using OpenAI, set the `OPENAI_API_KEY` environment variable:

```bash
export OPENAI_API_KEY='your-api-key-here'
```

Then with [`uvx`](https://docs.astral.sh/uv/guides/tools/), run:

```bash
uvx clai
```

Or to install `clai` globally [with `uv`](https://docs.astral.sh/uv/guides/tools/#installing-tools), run:

```bash
uv tool install clai
...
clai
```

Or with `pip`, run:

```bash
pip install clai
...
clai
```

Either way, running `clai` will start an interactive session where you can chat with the AI model. Special commands available in interactive mode:

- `/exit`: Exit the session
- `/markdown`: Show the last response in markdown format
- `/multiline`: Toggle multiline input mode (use Ctrl+D to submit)

## Help

```
usage: clai [-h] [-m [MODEL]] [-a AGENT] [-l] [-d [API_URL]] [-dd] [-t [CODE_THEME]] [--no-stream] [--version] [prompt]

PydanticAI CLI v...

Special prompts:
* `/exit` - exit the interactive mode (ctrl-c and ctrl-d also work)
* `/markdown` - show the last markdown output of the last question
* `/multiline` - toggle multiline mode

positional arguments:
  prompt                AI Prompt, if omitted fall into interactive mode

options:
  -h, --help            show this help message and exit
  -m [MODEL], --model [MODEL]
                        Model to use, in format "<provider>:<model>" e.g. "openai:gpt-4o" or "anthropic:claude-3-7-sonnet-latest". Defaults to "openai:gpt-4o".
  -a AGENT, --agent AGENT
                        Custom Agent to use, in format "module:variable", e.g. "mymodule.submodule:my_agent"
  -l, --list-models     List all available models and exit
  -d [API_URL], --discover-models [API_URL]
                        Discover models from a local OpenAI-compatible API endpoint and interactively select one to chat with. Requires complete API URL including version (e.g., "http://localhost:11434/v1" for Ollama or "http://localhost:1234/v1" for LM Studio). If no URL provided, uses the last discovered endpoint.
  -dd, --discover-direct
                        Directly connect to the last used model and endpoint without any prompts. Equivalent to "clai -d" + pressing Enter twice.
  -t [CODE_THEME], --code-theme [CODE_THEME]
                        Which colors to use for code, can be "dark", "light" or any theme from pygments.org/styles/. Defaults to "dark" which works well on dark terminals.
  --no-stream           Disable streaming from the model
  --version             Show version and exit
```
