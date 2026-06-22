# 📚 Homework 1 FAQ (Agentic RAG)

You can save this as:

```
lessosns/01-agentic-rag/faq.md
```

---

````markdown id="faq-final"
# 📚 Homework 1 – Agentic RAG FAQ

This FAQ summarizes common issues encountered during Homework 1 (Agentic RAG) in the LLM Zoomcamp and how they were resolved.

---

## ❓ Q1: Why do I get `Missing credentials` when using OpenAIClient?

**Answer:**

This happens when the API key is not loaded into the environment.

Even if you have a `.env` file, Python does not automatically read it.

### Fix:
```python
from dotenv import load_dotenv
load_dotenv()
````

Or ensure the environment variable is set:

```bash
export OPENAI_API_KEY="your_key"
```

---

## ❓ Q2: Why does `KeyError: OPENAI_API_KEY` happen?

**Answer:**

This occurs when the environment variable is not available in the current shell session.

### Fix:

* Check `.env` file exists
* Load it using `python-dotenv`
* Or restart terminal / Jupyter kernel

---

## ❓ Q3: Why does Git show a “nested repository (160000 mode)”?

**Answer:**

This happens when a folder contains its own `.git` directory and is accidentally added to another repo.

Git then treats it as a **submodule reference instead of files**.

### Fix:

```bash
git rm --cached folder
rm -rf folder/.git
git add folder
```

---

## ❓ Q4: Why does GitHub show an empty folder or broken directory?

**Answer:**

This is usually caused by:

* submodule misconfiguration
* partial commits
* or missing file tracking

### Fix:

Ensure files are properly added:

```bash
git add .
git commit -m "restore files"
git push
```

---

## ❓ Q5: Why does `toyaikit.tool` or `Agent` import fail?

**Answer:**

Some versions of `toyaikit` do not expose `tool` or `Agent` directly.

### Fix:

Use the correct import style:

```python
from toyaikit.tools import Tools
```

Or check available exports:

```python
import toyaikit
dir(toyaikit)
```

---

## ❓ Q6: Why does the agent call search multiple times?

**Answer:**

This is expected behavior in an agentic loop.

The LLM:

1. Generates an answer
2. Calls search tool if unsure
3. Uses results to refine reasoning
4. Repeats until confident

This is what differentiates **agentic RAG vs normal RAG**.

---

## ❓ Q7: Why does the agent sometimes give inconsistent token counts?

**Answer:**

Different models (e.g. `gpt-5.4-mini`, OpenRouter models) report slightly different token usage.

Always use:

* `response.usage.input_tokens`
* or framework-provided cost tracking

---

## 📌 Summary

The main issues in this assignment were related to:

* environment variable handling
* Git submodule mistakes
* tool import differences
* agent loop behavior

```

---

# 🧠 Why this version is good

✔ matches YOUR real errors  
✔ aligned with LLM Zoomcamp expectations  
✔ explains both Python + Git + agent issues  
✔ clean and readable  
✔ not too long or random  

---

# 🚀 Next step (optional)

If you want, I can now:

- :contentReference[oaicite:0]{index=0}
- or :contentReference[oaicite:1]{index=1}
- or :contentReference[oaicite:2]{index=2}

Just say 👍
```
