# Prompt Optimizer (Chrome Extension)

Prompt Optimizer is a Chrome extension that enhances user prompts directly within LLM interfaces such as ChatGPT, Claude, and Gemini. It intercepts prompt input fields, applies structured prompt-engineering transformations, and rewrites the content in place.

## Overview

The extension operates via a content script that dynamically detects active input areas across supported platforms. It then applies either:

-   A **rule-based optimization pipeline** (local, no external dependencies), or
-   A **Gemini-powered rewrite** (via Google Generative AI API)

The optimized prompt replaces the original input seamlessly within the DOM.

## Features

-   **Context-aware prompt rewriting**
-   **Cross-platform support** (ChatGPT, Claude, Gemini)
-   **Zero-dependency local optimization engine**
-   **Optional LLM-powered refinement via Gemini API**
-   **Automatic input field detection using DOM heuristics**
-   **In-place prompt replacement (no UI disruption)**

## Architecture

```
prompt-optimizer/
├── manifest.json
├── popup.html
├── popup.js
├── styles.css
├── content.js
├── background.js
└── libs/
    └── google-genai.js
```

### Core Components

-   **Content Script (`content.js`)**
    -   Identifies editable prompt fields across supported platforms
    -   Extracts user input and injects optimized output
-   **Popup Interface (`popup.js`)**
    -   Stores API key using Chrome Storage API
    -   Triggers optimization workflow
-   **Background Worker (`background.js`)**
    -   Manages extension lifecycle events
-   **Gemini Integration (`google-genai.js`)**
    -   Handles API calls to Google's Generative AI endpoints

## Installation

```
git clone https://github.com/praveen4107/prompt-optimizer-chrome.git
```

1.  Navigate to `chrome://extensions`
2.  Enable **Developer Mode**
3.  Click **Load unpacked**
4.  Select the cloned project directory

## Gemini API Integration

To enable LLM-based optimization:

1.  Obtain an API key from Google AI Studio
2.  Provide the key via the extension popup UI
3.  The extension will automatically switch from rule-based rewriting to Gemini-backed optimization

> If no API key is configured, the extension defaults to the local rule-based optimizer.

## Usage Flow

1.  Open a supported platform (ChatGPT / Claude / Gemini)
2.  Enter a prompt in the input field
3.  Click the extension icon
4.  Trigger optimization
5.  The rewritten prompt replaces the original input instantly
