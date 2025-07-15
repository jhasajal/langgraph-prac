# LangGraph Practice Project

A comprehensive learning project exploring **LangGraph** - a framework for building stateful, multi-step applications with large language models (LLMs). This repository contains practical examples, tutorials, and implementations demonstrating various LangGraph concepts and patterns.

## 🚀 Overview

This project serves as a hands-on learning resource for understanding and implementing LangGraph workflows. It includes:

- **State management** with TypedDict
- **Graph-based workflows** with nodes and edges
- **Chatbot implementations** with conversation history
- **Conditional routing** and complex graph structures
- **Integration** with multiple LLM providers (OpenAI, Google Gemini)

## 📋 Prerequisites

- Python 3.13+
- API keys for LLM providers (OpenAI and/or Google)
- Basic understanding of Python and async programming

## 🛠️ Installation

### 1. Clone the Repository
```bash
git clone https://github.com/jhasajal/langgraph-prac.git
cd langgraph-prac
```

### 2. Set Up Environment
This project uses [uv](https://github.com/astral-sh/uv) for dependency management:

```bash
# Install dependencies
uv sync

# Activate virtual environment
source .venv/bin/activate  # On Linux/Mac
# or
.venv\Scripts\activate     # On Windows
```

### 3. Configure Environment Variables
Create a `.env` file in the project root:

```env
# Google AI API Key (for Gemini models)
GOOGLE_API_KEY=your_google_api_key_here

# OpenAI API Key (for GPT models)
OPENAI_API_KEY=your_openai_api_key_here
```

**⚠️ Important**: Never commit your `.env` file to version control. It's already included in `.gitignore`.

## 📚 Project Structure

```
langgraph-prac/
├── 📓 chatbot.ipynb                     # Interactive chatbot with conversation history
├── 📓 simple_graph.ipynb               # Basic LangGraph workflow example
├── 📓 2_graph_with_condition.ipynb     # Conditional routing examples
├── 📓 jupyter_notebook_guide.ipynb     # VS Code Jupyter setup guide
├── 🐍 main.py                          # Main Python script entry point
├── ⚙️ pyproject.toml                   # Project configuration and dependencies
├── 🔒 .env                            # Environment variables (not tracked)
├── 📄 .gitignore                       # Git ignore rules
└── 📖 README.md                        # This file
```

## 🎯 Examples and Tutorials

### 1. Simple Graph (`simple_graph.ipynb`)
A basic LangGraph example demonstrating:
- State definition with TypedDict
- Node functions for calculations
- Sequential workflow execution
- Currency conversion pipeline

**Example workflow**: USD amount → Apply tax → Convert to INR

### 2. Chatbot (`chatbot.ipynb`)
An interactive chatbot implementation featuring:
- Conversation state management
- Message history tracking
- Multiple LLM provider support
- Interactive chat loop

### 3. Conditional Graphs (`2_graph_with_condition.ipynb`)
Advanced routing patterns including:
- Conditional node execution
- Dynamic workflow paths
- State-based decision making

### 4. Jupyter Setup Guide (`jupyter_notebook_guide.ipynb`)
Complete guide for working with Jupyter notebooks in VS Code:
- Extension installation
- Environment setup
- Cell execution
- Export options

## 🚦 Getting Started

### Quick Start with Notebooks

1. **Open VS Code** in the project directory
2. **Install Jupyter Extension** (if not already installed)
3. **Open any `.ipynb` file** to start exploring
4. **Select the Python kernel** from your virtual environment
5. **Run cells** using `Shift+Enter`

### Quick Start with Scripts

```bash
# Run the main script
python main.py
```

## 🔧 Key Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `langgraph` | ^0.5.2 | Core graph framework |
| `langchain` | ^0.3.26 | LLM abstraction layer |
| `langchain-openai` | ^0.3.27 | OpenAI integration |
| `langchain-google-genai` | ^2.1.7 | Google Gemini integration |
| `python-dotenv` | ^1.1.1 | Environment variable management |
| `notebook` | ^7.4.4 | Jupyter notebook support |

## 💡 Usage Examples

### Basic Graph Creation
```python
from langgraph.graph import StateGraph, START, END
from typing import TypedDict

class State(TypedDict):
    value: int

def increment(state: State) -> State:
    return {"value": state["value"] + 1}

# Build graph
graph = StateGraph(State)
graph.add_node("increment", increment)
graph.add_edge(START, "increment")
graph.add_edge("increment", END)

# Execute
app = graph.compile()
result = app.invoke({"value": 0})
print(result)  # {"value": 1}
```

### Chatbot Integration
```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-3.5-turbo")
response = llm.invoke("Hello, how are you?")
print(response.content)
```

## 🐛 Troubleshooting

### Common Issues

1. **Kernel not found in Jupyter**
   - Make sure VS Code Jupyter extension is installed
   - Select the correct Python interpreter from your virtual environment

2. **API Key errors**
   - Verify your `.env` file contains valid API keys
   - Check that `python-dotenv` is loading the environment variables

3. **Import errors**
   - Ensure all dependencies are installed: `uv sync`
   - Activate the virtual environment before running scripts

4. **Package installation issues**
   - Update uv: `pip install --upgrade uv`
   - Clear cache: `uv cache clean`

## 🤝 Contributing

This is a learning project, but contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Add examples or improvements
4. Submit a pull request

## 📝 Learning Resources

- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [Google AI Documentation](https://ai.google.dev/)

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🏷️ Tags

`langgraph` `langchain` `llm` `chatbot` `python` `jupyter` `openai` `gemini` `state-management` `workflow`

---

**Happy Learning!** 🎉

If you find this repository helpful, please give it a ⭐ and share it with others learning LangGraph!