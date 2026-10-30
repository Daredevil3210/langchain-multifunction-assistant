# LangChain Multifunction Assistant

English | [简体中文](README.zh.md)

A Chinese-language assistant in a single Jupyter Notebook, demonstrating how LangChain's `create_agent` selects Python tools and maintains conversation history. It combines DeepSeek with five tools for weather, arithmetic, time, currency conversion, and information lookup.

This is an educational example. Weather, exchange rates, product listings, and news are embedded sample data, even where tool descriptions use the word “real-time.” Only the date/time tool reads the local system clock.

## What the notebook demonstrates

- `get_weather`: sample conditions for Beijing, Shanghai, Shenzhen, Chengdu, Hangzhou, and Guangzhou.
- `calculator`: arithmetic and selected mathematical functions, including `sqrt`, `pow`, `abs`, trigonometric functions, and logarithms.
- `get_time_info`: current local time, today's date, tomorrow, yesterday, and weekday.
- `convert_currency`: conversion among CNY, USD, EUR, GBP, JPY, and HKD using a fixed rate dictionary.
- `search_info`: keyword matching against sample product and news dictionaries; no web search.
- `SmartAssistant`: a Chinese system prompt, tool registration, agent invocation, conversation history, and reset behavior.

## Requirements and setup

Use a Python environment compatible with the installed LangChain and Jupyter packages. The repository has no pinned dependency file, lockfile, or declared Python version, so it does not define a reproducible environment.

```bash
git clone https://github.com/Daredevil3210/langchain-multifunction-assistant.git
cd langchain-multifunction-assistant
python -m pip install langchain langchain-deepseek python-dotenv rich jupyter
```

Set these environment variables before starting Jupyter, or create a local `.env` in the repository directory:

```dotenv
DEEPSEEK_API_KEY=replace_with_your_private_key
DEEPSEEK_BASE_URL=https://api.deepseek.com
```

The initialization cell currently selects `deepseek-v4-flash` and sends `thinking.type=disabled`. This is the notebook's configured identifier, not a guarantee of availability for every account. If necessary, edit that cell to select a model that supports the tool calls and request parameters used here. `load_dotenv()` uses its default behavior: existing process environment values take precedence over `.env`.

Keep the real `.env` local. Model-backed examples send prompts and tool results to the configured service and may incur API charges.

## Run

```bash
jupyter notebook
```

Open [`06-实战：多功能智能助手.ipynb`](06-实战：多功能智能助手.ipynb), select the environment where you installed the packages, and run the cells in order. The final cell runs four demonstration questions, resets the conversation, and opens an input loop.

- Enter `quit` to exit.
- Enter `reset` to clear the assistant's message history.

Example prompts:

```text
北京今天天气怎么样？
帮我算一下 (25 + 17) * 3
现在几点了？
100 美元等于多少人民币？
```

## Repository structure

- `06-实战：多功能智能助手.ipynb`: model initialization, tool definitions, `SmartAssistant`, demos, and interactive entry point.
- `README.md` / `README.zh.md`: English and Chinese documentation.
- `LICENSE`: MIT license and tutorial-contributor copyright notice.

## Checks and limitations

The demonstration prompts are manual examples, not an automated test suite. The repository provides no test runner configuration; no execution or API validation is claimed by this documentation update.

The calculator uses Python `eval` with disabled built-ins and an allowlist of functions. This is a teaching implementation rather than a hardened expression parser; do not expose it to untrusted expressions. Conversation history exists in the `SmartAssistant` instance and has no persistent storage. Mock lookup data can become outdated and should not be treated as current information.

## Learning context and license

The notebook identifies itself as a LangChain 1.2 practical exercise. The repository retains its [MIT License](LICENSE), including `Copyright (c) 2026 LangChain 1.2 Tutorial contributors`.
