# 🔌 pyllmlib

[![PyPI Downloads](https://static.pepy.tech/badge/pyllmlib)](https://pepy.tech/projects/pyllmlib)
[![PyPI Version](https://img.shields.io/pypi/v/pyllmlib.svg)](https://pypi.org/project/pyllmlib/)
![Python Version](https://img.shields.io/pypi/pyversions/pyllmlib.svg)
[![License](https://img.shields.io/github/license/yazirofi/pyllmlib)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/yazirofi/pyllmlib?style=social)](https://github.com/yazirofi/pyllmlib)

---

<div style="
  width:200px; 
  height:100px; 
  overflow:hidden; 
  display:flex; 
  justify-content:center; 
  align-items:center; 
  margin:auto; 
  position:relative; 
  top:0; 
  bottom:0; 
  left:0; 
  right:0; 
  border-radius:10px; 
  box-shadow:0 4px 8px rgba(0,0,0,0.2);
">
  <img src="https://raw.githubusercontent.com/yazirofi/cdn/main/yazirofi.jpg" 
       style="width:100%; height:100%; object-fit:cover;" 
       alt="Cropped Image">
</div>

---

**pyllmlib** is a lightweight, provider-agnostic Python package that gives you **one simple interface** to work with multiple Large Language Model (LLM) APIs.

Stop juggling different SDKs and client libraries — whether it’s **OpenAI GPT**, **Google Gemini**, **Mistral AI**, or **Groq**, you write your code once and switch providers in seconds.

🎯 **Ideal for** developers who want to:

* Experiment with different LLMs quickly
* Build multi-provider AI applications
* Avoid vendor lock-in with a consistent API

---

## ✨ Features

* 🔌 **Unified API** — A single `generate()` function for all providers
* 🌐 **Multi-Provider Support** — OpenAI, Gemini, Mistral, Groq (with more coming soon)
* 🧠 **Consistent Message Format** — Same request style across providers
* 🔐 **Flexible Config** — Use env vars, inline setup, or config files
* 📦 **Minimal Dependencies** — Only needs `requests`
* 🔄 **Quick Provider Switching** — Change models with one line
* 🛡️ **Automatic Token Handling** — Prevents overflows & context errors
* 📜 **Role-Based Conversations** — System, user, assistant messages
* 🔧 **Extensible** — Add your own providers with minimal code
* 🚀 **No Vendor Lock-In** — Swap providers without rewriting logic

---

## 📦 Installation

From PyPI (recommended):

```bash
pip install pyllmlib
```

From GitHub:

```bash
# Latest release
pip install git+https://github.com/yazirofi/pyllmlib.git

# Development version
git clone https://github.com/yazirofi/pyllmlib.git
cd pyllmlib
pip install -e .
```

**Requirements**:

* Python 3.7+
* `requests` (installed automatically)

---

## 🚀 Quick Start

```python
from pyllmlib import config, generate

# Configure your preferred LLM
config(
    provider="openai",
    api_key="your-openai-api-key",
    model="gpt-4"
)

# Generate text
response = generate("Explain quantum computing in simple terms")
print(response)
```

✅ Same code works with **any provider** — just change the config.

---

## ⚙️ Configuration

### 1. Direct in Code

```python
from pyllmlib import config

# OpenAI
config(provider="openai", api_key="sk-...", model="gpt-4")

# Google Gemini
config(provider="gemini", api_key="AIza...", model="gemini-2.5-flash")

# Mistral
config(provider="mistral", api_key="...", model="mistral-large-latest")

# Groq
config(provider="groq", api_key="gsk_...", model="mixtral-8x7b-32768")
```

### 2. Environment Variables

```bash
LLM_PROVIDER=openai
LLM_API_KEY=sk-your-openai-key
LLM_MODEL=gpt-4
LLM_BASE_URL=https://api.openai.com/v1  # Optional
```

```python
from pyllmlib import config, generate

config()  # Loads from env
print(generate("What is LLM?"))
```

---

## 💬 Usage Examples

### Text Generation

```python
from pyllmlib import config, generate

config(provider="gemini", api_key="AIza...", model="gemini-2.5-flash")

print(generate("What is the capital of France?"))

prompt = """
Write a Python function to calculate factorial with error handling and docstring.
"""
print(generate(prompt))
```

### Interactive Chat

```python
from pyllmlib import config, chat, reset_chat

config(provider="gemini", api_key="AIza...", model="gemini-2.5-flash")

while (q := input("Ask: ")):
    print(chat(q))

reset_chat()
```

---

## 🌐 Supported Providers

### ✅ Currently Supported

* **OpenAI** — `gpt-4`, `gpt-4-turbo`, `gpt-3.5-turbo`
* **Google Gemini** — `gemini-2.5-flash`, `gemini-1.5-flash`
* **Mistral AI** — `mistral-large-latest`, `mistral-small-latest`
* **Groq** — `mixtral-8x7b-32768`, `llama2-70b-4096`, `gemma-7b-it`

### 🔜 Coming Soon

* Anthropic Claude
* Cohere
* Ollama & LM Studio (local hosting)
* Hugging Face models

---

## 🐛 Troubleshooting

* **Auth Errors** → Check API key format
* **Model Not Found** → Verify model name is correct

---

## 📊 Best Practices

```python
# ✅ Reuse config for multiple prompts
config(provider="openai", api_key="sk-...", model="gpt-4")
for p in prompts:
    print(generate(p))

# ❌ Don’t reconfigure on every request
```

💡 **Cost Optimization**: Use `gpt-3.5-turbo` for simple tasks, `gpt-4` for complex ones.

---

## 📚 API Reference

* `config(**kwargs)` → Set provider, API key, model
* `generate(prompt, **kwargs)` → Single text output
* `generate_stream(prompt, **kwargs)` → Streaming output
* `chat(message)` → Conversational interface
* `reset_chat()` → Clear conversation history

---


## 📄 License

Licensed under the **MIT License** – see [LICENSE](LICENSE).

---

## 👨💻 Author

**Shay Yazirofi**

* GitHub: [@yazirofi](https://github.com/yazirofi)
* Email: [yazirofi@gmail.com](mailto:yazirofi@gmail.com)

---

⭐ If you find **pyllmlib** useful, please **star the repo** on GitHub!
📖 More docs & tutorials: [Wiki](https://github.com/yazirofi/pyllmlib/)

---

