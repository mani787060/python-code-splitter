# Python Code Splitter

A simple implementation of **code splitting using LangChain** and Python-specific splitting rules. This project demonstrates how to divide Python source code into smaller, manageable chunks using `RecursiveCharacterTextSplitter` and `Language.PYTHON`.

The goal is to understand how programming-language-aware text splitting works and why it is useful when preparing source code for downstream Generative AI applications.

## Overview

When working with large Python files, processing the entire source code at once can be difficult because of context-length limitations and processing requirements.

LangChain provides `RecursiveCharacterTextSplitter`, which supports language-specific splitting configurations. By selecting `Language.PYTHON`, the splitter uses Python-oriented separators to divide the source code into smaller chunks.

This project uses a sample Python `Student` class to demonstrate the splitting process.

## Key Features

- **Python-specific splitting:** Uses `Language.PYTHON` to configure the splitter for Python source code.
- **Recursive character splitting:** Uses LangChain's `RecursiveCharacterTextSplitter`.
- **Custom chunk size:** Sets the target chunk size to 300 characters.
- **Chunk overlap configuration:** Uses `chunk_overlap=0` to avoid intentionally repeating text between chunks.
- **Chunk inspection:** Displays the total number of generated chunks and prints an individual chunk.

## Technologies Used

- Python
- LangChain
- `langchain-text-splitters`

## Project Structure

```text
python-code-splitter/
│
├── python_code_splitter.py
├── README.md
└── requirements.txt
```

*Note: Update the Python filename above if your actual file uses a different name.*

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/mani787060/python-code-splitter.git
cd python-code-splitter
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
```

Activate it:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux/macOS:**
```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install langchain-text-splitters
```

Alternatively, if you maintain a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

## Implementation

### 1. Import the required classes

```python
from langchain_text_splitters import (
    RecursiveCharacterTextSplitter,
    Language
)
```

### 2. Prepare Python source code

The example uses a Python `Student` class containing:

- A constructor (`__init__`)
- A `get_details()` method
- An `is_passing()` method
- Example object creation and method calls

### 3. Configure the splitter

```python
splitter = RecursiveCharacterTextSplitter.from_language(
    language=Language.PYTHON,
    chunk_size=300,
    chunk_overlap=0,
)
```

**Configuration explained:**

| Parameter | Description |
|---|---|
| `language=Language.PYTHON` | Applies Python-specific splitting rules. |
| `chunk_size=300` | Sets the target maximum chunk size. |
| `chunk_overlap=0` | Disables intentional overlap between chunks. |

The chunk size is a target rather than a guarantee that every chunk will be exactly 300 characters.

### 4. Split the source code

```python
chunks = splitter.split_text(text)
```

The splitter returns a list of text chunks.

### 5. Inspect the results

```python
print(len(chunks))
print(chunks[1])
```

The first statement displays the number of generated chunks, while the second prints the second chunk.

Make sure the requested index exists before accessing a chunk.

## How It Works

```text
Python Source Code
        |
        v
RecursiveCharacterTextSplitter
        |
        v
Python Language Configuration
        |
        v
Recursive Splitting
        |
        v
List of Smaller Code Chunks
        |
        v
Inspect Chunk Count and Content
```

## Why Is Code Splitting Useful in Generative AI?

Code splitting is useful when building applications that need to process or retrieve information from source code.

Some potential applications include:

- **Code RAG:** Retrieve relevant code snippets based on a user's question.
- **Code understanding:** Provide smaller sections of source code to an LLM.
- **Repository analysis:** Prepare large codebases for retrieval and processing.
- **AI coding assistants:** Supply relevant code context to language models.

This repository demonstrates the splitting step, not a complete RAG or code-understanding application.

## Run the Project

Execute the Python file:

```bash
python python_code_splitter.py
```

The program prints the number of chunks and the content of the second chunk.

## Learning Outcomes

Through this implementation, you can understand:

- How `RecursiveCharacterTextSplitter` works.
- How to configure a language-specific splitter for Python.
- How chunk size and overlap affect text splitting.
- How to prepare source code for downstream Generative AI workflows.

## Future Improvements

- Experiment with different chunk sizes and overlap values.
- Compare Python-specific splitting with generic character splitting.
- Preserve additional code metadata where needed.
- Explore combining code splitting with embeddings and vector databases.
- Build a code-focused Retrieval-Augmented Generation (RAG) application.
