# openclaw-start

Starter configuration for running an [OpenClaw](https://openclaw.dev) gateway with AI agent support.

## Overview

This project sets up an OpenClaw gateway that:
- Connects to AI models via [OpenRouter](https://openrouter.ai) (Claude Sonnet 4.5, DeepSeek Chat)
- Receives messages via Telegram bot
- Exposes a local HTTP gateway on port 18789
- Runs AI agents with browser support

## Prerequisites

- [Node.js](https://nodejs.org) (download and install from nodejs.org)
- [Visual Studio Code](https://code.visualstudio.com) (recommended editor)
- An [OpenRouter](https://openrouter.ai) API key
- A Telegram bot token (from [@BotFather](https://t.me/BotFather))

## Setup

1. Install dependencies:
   ```sh
   npm install
   ```

2. **Create a Telegram bot** via [@BotFather](https://t.me/BotFather):
   - Open Telegram and start a chat with [@BotFather](https://t.me/BotFather)
   - Send `/newbot` and follow the prompts (choose a name and username)
   - Copy the **bot token** you receive (format: `123456789:AAF...`)

3. **Get your Telegram user ID** (`TELEGRAM_ALLOWED_USER_ID`):
   - Start a chat with [@userinfobot](https://t.me/userinfobot)
   - It will reply with your numeric user ID (e.g. `123456789`)
   - This restricts bot access to your account only

4. Create a `.env` file with your credentials:
   ```sh
   OPENROUTER_API_KEY=your_openrouter_api_key
   TELEGRAM_BOT_TOKEN=your_telegram_bot_token      # from BotFather
   TELEGRAM_ALLOWED_USER_ID=your_telegram_user_id  # numeric ID from step 3
   AGENT_FOLDER_NAME=your-folder-name              # agent workspace folder
   GATEWAY_AUTH_TOKEN=your_gateway_auth_token
   ```

5. Start the gateway:
   ```sh
   ./start.sh
   ```
   Or via npm:
   ```sh
   npm start
   ```

## Configuration

The main configuration is in [openclaw.json](openclaw.json):

| Section | Description |
|---|---|
| `models` | AI model providers and settings (via OpenRouter) |
| `agents` | Agent defaults — primary model, concurrency, workspace; set `verboseDefault: "full"` to enable full verbose output |
| `channels.telegram` | Telegram bot configuration and allowlist |
| `gateway` | HTTP gateway port, auth, and network binding |
| `browser` | Browser automation settings |

## Scripts

| Script | Description |
|---|---|
| `npm start` | Start the OpenClaw gateway (verbose mode) |
| `npm run status` | Check gateway status |
