# Quick Start Guide

## ✅ What's Implemented (Phase 1-3 Complete)

All core features have been implemented:

### Phase 1: Core Architecture ✅
- **Smart Website Scraper** - Parallel page discovery and fetching
- **Gap Detection Agent** - Only triggers web search when needed
- **Reduced Web Searches** - From 15 to 5 (only for gap filling)
- **JSON Knowledge Base** - Structured storage for chatbot context

### Phase 2: Knowledge Management ✅
- **URL Caching** - Previously processed sites load instantly
- **Force Refresh** - UI option to re-scrape cached sites
- **JSON Storage** - All knowledge saved to `knowledge_files/`

### Phase 3: Quality Enhancements ✅
- **Retry Logic** - 3 attempts for failed requests
- **robots.txt Compliance** - Respects website crawling rules
- **Rate Limiting** - Polite delays between requests
- **Error Handling** - User-friendly error messages

## 🚀 Running the Project

### 1. Install Dependencies

```bash
# Activate your virtual environment first
pip install -r requirements.txt
```

### 2. Set Up Environment

Create a `.env` file:
```
OPENAI_API_KEY=your_openai_api_key_here
```

### 3. Run the Notebook

Open `main.ipynb` and run all cells in order (Cells 1-10).

The Gradio UI will launch automatically at `http://127.0.0.1:7860`

### 4. Generate a Chatbot

1. Enter any website URL
2. (Optional) Check "🔄 Force Refresh" to re-scrape cached sites
3. Click "🚀 Generate Chatbot"
4. Wait for processing:
   - **First time:** 10-30 seconds
   - **Cached:** ~1-2 seconds (instant!)
5. Chat with your website-trained bot!

## 📊 Workflow

```
URL Input
    ↓
Check Cache ──→ [Cached?] ──→ Load Instantly (~1-2s)
    ↓ (not cached)
Scrape Website (PRIMARY SOURCE)
    ↓
Analyze Content Gaps
    ↓
[Gaps Found?] ──→ Run Web Searches (SECONDARY)
    ↓
Build Knowledge Base (JSON)
    ↓
Save to Cache
    ↓
Prepare Chatbot
    ↓
Ready to Chat! 🎉
```

## 📁 Output Files

Knowledge files are saved to `knowledge_files/`:
- Named by URL hash (e.g., `example_com_abc123.json`)
- Contains primary (website) and secondary (search) content
- Enables instant reload on subsequent visits

## 🎯 Key Features

| Feature | Description |
|---------|-------------|
| **Primary Source Priority** | Website content always used first |
| **Intelligent Gap Detection** | Web search only runs when needed |
| **JSON Caching** | Instant load for repeat visits |
| **Polite Scraping** | Respects robots.txt, rate limits |
| **Error Recovery** | Automatic retries, fallback to search |
| **Source Attribution** | Clear PRIMARY vs SECONDARY labels |

## ⚠️ Troubleshooting

**"Module not found" errors:**
```bash
pip install openai-agents aiohttp beautifulsoup4 lxml gradio pydantic python-dotenv
```

**API key errors:**
- Ensure `.env` file exists with valid `OPENAI_API_KEY`

**Slow first load:**
- Normal! First scrape takes 10-30s depending on website size
- Subsequent loads are instant (cached)

**Website blocked:**
- Some sites block automated access
- Try a different URL or check robots.txt

