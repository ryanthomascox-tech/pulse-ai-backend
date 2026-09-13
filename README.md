# PULSE AI Coach backend

This keeps the OpenAI API key on a server instead of inside the iPhone app.

## 1. Install

```bash
npm install
```

## 2. Set the OpenAI API key

macOS/Linux:

```bash
export OPENAI_API_KEY="your_api_key_here"
```

Never put this key in `ContentView.swift`, Git, or the App Store build.

## 3. Deploy

This folder is structured for a Vercel serverless function.

Deploy the project with Vercel, then set the environment variable:

`OPENAI_API_KEY`

The endpoint will be:

`https://YOUR-PROJECT.vercel.app/api/coach`

## 4. Connect the iPhone app

In `ContentView.swift`, change:

```swift
static let endpoint = "https://YOUR-PULSE-AI-BACKEND.example.com/api/coach"
```

to your deployed HTTPS endpoint.

The app sends the Coach question, the recent conversation, and the current PULSE/Fuel context. The backend sends that to the OpenAI Responses API and returns the AI reply.

The request uses `store: false` so the Response is not stored as application state by default.
