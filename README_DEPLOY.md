# How to Deploy Chatsmith

The easiest way to deploy this Gradio application for free is using **Hugging Face Spaces**.

## Prerequisites

1.  A [Hugging Face account](https://huggingface.co/join).
2.  An [OpenAI API Key](https://platform.openai.com/api-keys).

## Deployment Steps

1.  **Create a New Space:**
    *   Go to [huggingface.co/spaces](https://huggingface.co/spaces).
    *   Click **"Create new Space"**.
    *   **Space name:** `chatsmith` (or any name you like).
    *   **License:** `MIT` (optional).
    *   **Select the Space SDK:** Choose **Gradio**.
    *   **Hardware:** Keep it as **CPU basic (free)**.
    *   Click **"Create Space"**.

2.  **Upload Files:**
    *   You can upload files directly via the browser or use git.
    *   **Upload the following files** from your `chatsmith/chatsmith` folder:
        *   `app.py`
        *   `requirements.txt`
    *   *Note: You do not need to upload the `.ipynb` file or other markdown files.*

3.  **Set Environment Variables (Secrets):**
    *   Go to the **"Settings"** tab of your Space.
    *   Scroll down to **"Variables and secrets"**.
    *   Click **"New secret"**.
    *   **Name:** `OPENAI_API_KEY`
    *   **Value:** Paste your actual OpenAI API key (starts with `sk-...`).
    *   Click **"Save"**.

4.  **Run:**
    *   The Space will automatically build and start.
    *   Watch the **"Logs"** tab for any errors.
    *   Once built, your app will be live at `https://huggingface.co/spaces/<your-username>/chatsmith`.

## Troubleshooting

*   **Runtime Error:** Check the "Logs" tab. If it says "Module not found", ensure `requirements.txt` was uploaded correctly.
*   **API Error:** Ensure your OpenAI API key is correct and has credits.
