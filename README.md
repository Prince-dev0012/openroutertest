# OpenRouter ENVAPI Integration

This example demonstrates how to use the ENVAPI Worker to proxy requests to [OpenRouter](https://openrouter.ai/), which provides access to many LLMs (DeepSeek, Llama 3, Claude, etc.) using an OpenAI-compatible API.

## 1. Configure the Admin Dashboard

You need to add a new API configuration in your Admin Dashboard using the **Advanced JSON Configuration** mode.

### JSON Configuration

Copy and paste this into the "Advanced JSON Configuration" field:

```json
{
  "provider": "custom",
  "endpoint": "https://openrouter.ai/api/v1/chat/completions",
  "method": "POST",
  "headers": {
    "Authorization": "Bearer {{apiKey}}",
    "Content-Type": "application/json",
    "HTTP-Referer": "https://github.com/prince-dev0012/env-manager",
    "X-Title": "ENVAPI Demo"
  },
  "apiKey": "sk-or-YOUR_OPENROUTER_API_KEY_HERE"
}
```

*   **Note:** Replace `YOUR_OPENROUTER_API_KEY_HERE` with your actual key starting with `sk-or-...`.
*   **Headers:** OpenRouter requires `HTTP-Referer` and optional `X-Title` for rankings.

## 2. Update Client Code

The `index.html` file is set up to use this configuration.

### Key Settings in `index.html`:
1.  **Project Key:** Use your Project Key (e.g., `pk_demo_12345`).
2.  **API Name:** Use the name you gave the API above (e.g., `openrouter-chat`).
3.  **Model:** You can specify any model supported by OpenRouter (e.g., `deepseek/deepseek-r1:free`, `meta-llama/llama-3-8b-instruct:free`).

## 3. Testing

1.  Open `index.html` in your browser.
2.  Enter your **Worker URL** and **Project Key**.
3.  Enter the **API Name** (`openrouter-chat`).
4.  Type a message and click **Send**.
5.  The AI should reply!
