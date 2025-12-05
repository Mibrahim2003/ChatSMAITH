# ChatSMITH - Website to Chatbot Generator

An intelligent AI system that automatically generates chatbots from any website URL using smart web scraping, gap detection, and multi-agent orchestration.

## ⚠️ Python Version Requirements

**Important:** This project requires:
- **Python 3.9, 3.10, 3.11, or 3.12** (recommended: 3.10 or 3.11)
- Python 3.13+ may have compatibility issues

See [PYTHON_SETUP.md](PYTHON_SETUP.md) for detailed setup instructions.

## ✨ Features

- **Smart Website Scraping** - Directly extracts content from websites (PRIMARY SOURCE)
- **Intelligent Gap Detection** - Only runs web searches when necessary
- **JSON Knowledge Caching** - Instant load for previously processed websites
- **Polite Scraping** - Respects robots.txt, rate limiting, retry logic
- **Modern Gradio UI** - Clean interface with progress tracking

## 🏗️ Architecture

### Multi-Agent System

1. **Smart Website Scraper (PRIMARY SOURCE)**
   - Parallel page discovery and fetching
   - Respects robots.txt and rate limits
   - Retry logic with exponential backoff
   - Extracts and cleans HTML content

2. **Gap Detection Agent**
   - Analyzes extracted content completeness
   - Only triggers web search when confidence < 7/10
   - Recommends specific search queries

3. **Web Search Agent (SECONDARY SOURCE)**
   - Runs only when gaps are detected
   - Maximum 5 targeted searches (reduced from 15)
   - Results marked as secondary source

4. **Knowledge Storage System**
   - JSON files saved to `knowledge_files/`
   - URL-based caching (instant reload)
   - Source attribution (primary vs secondary)

5. **Chatbot Generator**
   - GPT-4o-mini powered responses
   - Priority: Homepage > Key pages > Blog > Web search
   - Context-aware answers

### Workflow

```
URL → Check Cache → [If cached: Load instantly]
                  → [If not cached:]
                     → Scrape Website (PRIMARY)
                     → Analyze Gaps
                     → Optional Web Search (SECONDARY)
                     → Save to JSON Cache
                     → Generate Chatbot
```

## 🚀 Quick Start

### 1. Install Dependencies

```bash
# Create virtual environment
python -m venv .venv

# Activate (Windows)
.venv\Scripts\activate

# Activate (Mac/Linux)
source .venv/bin/activate

# Install requirements
pip install -r requirements.txt
```

### 2. Set Up Environment

Create a `.env` file in the project root:
```
OPENAI_API_KEY=your_openai_api_key_here
```

### 3. Run the Application

Open `main.ipynb` in VS Code or Jupyter and run all cells. The Gradio UI will launch automatically.

### 4. Generate a Chatbot

1. Enter a website URL (e.g., `https://example.com`)
2. Click "🚀 Generate Chatbot"
3. Wait for processing (first time: 10-30s, cached: instant)
4. Chat with your new website-trained bot!

## 📁 Project Structure

```
chatsmith/
├── main.ipynb           # Main application notebook
├── requirements.txt     # Python dependencies
├── .env                 # API keys (create this)
├── knowledge_files/     # Cached JSON knowledge bases
├── README.md            # This file
├── QUICK_START.md       # Quick start guide
├── IMPLEMENTATION_NOTES.md  # Technical details
├── IMPROVEMENT_PLAN.md  # Future improvements
└── PYTHON_SETUP.md      # Python setup guide
```

## 🔧 Configuration

Key settings in `main.ipynb`:

| Setting | Default | Description |
|---------|---------|-------------|
| `MAX_PAGES_TO_SCRAPE` | 10 | Max pages to scrape per website |
| `REQUEST_TIMEOUT` | 15s | Timeout for HTTP requests |
| `MAX_RETRIES` | 3 | Retry attempts for failed requests |
| `POLITE_DELAY` | 0.5s | Delay between request batches |
| `HOW_MANY_SEARCHES` | 5 | Max web searches for gap filling |

## 📊 Performance

| Metric | Before | After (Phase 1-3) |
|--------|--------|-------------------|
| First load | 45-60s | 10-30s |
| Cached load | N/A | ~1-2s |
| Web searches | 15 | 0-5 (only if needed) |
| Accuracy | Medium | High (primary source) |

## 🛠️ Troubleshooting

**"ModuleNotFoundError: No module named 'agents'"**
```bash
pip install openai-agents
```

**"OpenAIError: api_key not set"**
- Create `.env` file with `OPENAI_API_KEY=your_key`

**Gradio format errors**
- Ensure Gradio 4.0+ is installed
- The app uses dict format: `{"role": "user", "content": "..."}`

## 📝 License

MIT License - See LICENSE file for details.

## 🤝 Contributing

Contributions welcome! Please see IMPROVEMENT_PLAN.md for planned enhancements.
