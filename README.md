# Agentic AI Website-to-Chatbot Generator

This project automatically generates a fully trained chatbot from any website URL using intelligent agents.

## ⚠️ Python Version Requirements

**Important:** This project requires:
- **Python 3.9, 3.10, 3.11, or 3.12** (recommended: 3.10 or 3.11)
- Python 3.13+ may have compatibility issues

See [PYTHON_SETUP.md](PYTHON_SETUP.md) for detailed setup instructions.

## How It Works

The system uses a multi-agent approach:

1. **Website Data Extraction Agent (PRIMARY SOURCE)**
   - Visits the website directly
   - Extracts accurate, real, trustworthy content
   - Cleans and structures the information
   - Breaks content into meaningful sections

2. **Gap Detection Agent**
   - Analyzes extracted content
   - Determines if web search is needed to fill gaps
   - Only recommends web search when necessary

3. **Web Search Agent (SECONDARY SOURCE)**
   - Runs web searches ONLY when needed
   - Fills missing gaps
   - Finds related official pages
   - Marked as "web_search" for reliability tracking

4. **Knowledge Storage System**
   - All extracted content saved into JSON files
   - JSON format optimized for LLM usage
   - Acts as the "single source of truth" for the chatbot
   - Enables accurate RAG (Retrieval-Augmented Generation)

5. **Chatbot Generator**
   - Automatically trains an LLM-powered chatbot
   - Uses JSON data + optional web search context
   - Answers questions about the website instantly
   - No coding or manual dataset preparation needed

## Dependencies

**Prerequisites:**
- Python 3.9-3.12 (recommended: 3.10 or 3.11)
- Virtual environment (recommended)

**Installation:**

```bash
# Create virtual environment with Python 3.11 (recommended)
python3.11 -m venv .venv

# Activate virtual environment
source .venv/bin/activate  # Mac/Linux
# OR
.venv\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt

# Install OpenAI Agents SDK (if not in requirements)
pip install git+https://github.com/openai/openai-agents-python.git
```

If you prefer inline installation inside the notebook use:

```python
# In a cell
%pip install -r requirements.txt
```

## Running
Open `main.ipynb` and run cells top-to-bottom. Provide a URL in the variable `query` (last cell) or adapt the interface cell if re-added.

## Optional Email / SendGrid
Email functionality was removed to keep the environment minimal. Add `sendgrid` to `requirements.txt` and reintroduce imports if you need it.

## Maintenance
- Keep only dependencies you truly use.
- Remove or archive any large outputs from the notebook to avoid bloating the repo.

Enjoy exploring and extending the research workflow!
