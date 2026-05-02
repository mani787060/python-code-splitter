# LangChain Python Code Splitter
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![Code Parsing](https://img.shields.io/badge/Pipeline-Code%20Chunking-orange)](https://python.langchain.com/docs/modules/data_connection/document_transformers/code_splitter)

## 🏗️ Project Overview
This repository focuses on **Source Code Ingestion** for Retrieval-Augmented Generation (RAG). Building AI tools that can interact with a codebase (like automated code reviewers or repo-chatbots) requires specialized data preparation. Standard text splitters destroy code by slicing through loops and separating functions from their definitions. This project demonstrates how to use LangChain's language-specific splitters to chunk Python code gracefully, respecting its Abstract Syntax Tree (AST) logic.

---

## 🛠️ Key Technical Implementations

### 1. Syntax-Aware Splitting
* **`Language.PYTHON` Integration:** Utilizing the specific Python configuration of the `RecursiveCharacterTextSplitter`. This tells LangChain to look for Python-specific structural markers rather than standard paragraphs.

### 2. Preservation of Logical Boundaries
* **Class and Function Integrity:** The splitter prioritizes breaking the text at the top level (between `class` and `def` statements). If a function is too large for the chunk size, it intelligently steps down to split at logical inner blocks (like massive lists, dictionaries, or separate conditional branches).
* **Indentation Respect:** Python is whitespace-dependent. This implementation ensures that indentation levels are not orphaned from their parent scopes, keeping the code mathematically and logically coherent for the LLM.

### 3. AI Developer Tool Readiness
* **Docstring Association:** Ensuring that a function's defining signature (e.g., `def calculate_loss(y_true, y_pred):`) stays in the exact same vector chunk as its explanatory docstring, drastically improving the LLM's ability to explain the code back to the user.

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Framework:** LangChain Text Splitters (`langchain-text-splitters`)
* **Environment:** `python-dotenv`

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/langchain-python-code-splitter.git](https://github.com/your-username/langchain-python-code-splitter.git)

2. **Install Dependencies:**
   ```bash
   pip install -U langchain langchain-text-splitters python-dotenv

3. **Run the Implementation:**
   ```bash
   python python_code_splitting.py   
