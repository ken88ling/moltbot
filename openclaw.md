# 🦞 OpenClaw Guide

OpenClaw is a powerful, personal AI assistant designed to run on your own devices and communicate via the messaging channels you already use (WhatsApp, Telegram, Slack, etc.).

## How to Run OpenClaw

Depending on your needs, you can run it via the global CLI (recommended for users) or from source (recommended for developers).

### 1. Standard Installation (via CLI)
Requires **Node.js ≥ 22**.

1.  **Install the package**:
    ```bash
    npm install -g openclaw@latest
    # or
    pnpm add -g openclaw@latest
    ```
2.  **Run the Onboarding Wizard**:
    ```bash
    openclaw onboard --install-daemon
    ```
3.  **Start the Gateway**:
    ```bash
    openclaw gateway --port 18789 --verbose
    ```

### 2. Running from Source (Development)
Recommended for contributors. Uses **pnpm**.

1.  **Clone and Install**:
    ```bash
    git clone https://github.com/openclaw/openclaw.git
    cd openclaw
    pnpm install
    ```
2.  **Build the Project**:
    ```bash
    pnpm ui:build
    pnpm build
    ```
3.  **Run in Watch Mode**:
    ```bash
    pnpm gateway:watch
    ```

### 📱 The two-phone setup (recommended)

To keep your personal chat separate from your assistant's input, we recommend using a second phone or number for the assistant.

#### WhatsApp Setup
```
Your Phone (personal)          Second Phone (assistant)
┌─────────────────┐           ┌─────────────────┐
│  Your WhatsApp  │  ──────▶  │  Assistant WA   │
│  +1-555-YOU     │  message  │  +1-555-ASSIST  │
└─────────────────┘           └────────┬────────┘
                                       │ linked via QR
                                       ▼
                              ┌─────────────────┐
                              │  Your Device    │
                              │  (OpenClaw)     │
                              └─────────────────┘
```

#### Telegram Setup
For Telegram, it's even easier: you don't necessarily need a second phone, just a **Bot Token** from [BotFather](https://t.me/botfather).
```
Your Telegram (personal)       Telegram Cloud (Bot)
┌─────────────────┐           ┌─────────────────┐
│  @YourHandle    │  ──────▶  │  @YourAgentBot  │
└─────────────────┘  message  └────────┬────────┘
                                       │ Bot Token
                                       ▼
                              ┌─────────────────┐
                              │  Your Device    │
                              │  (OpenClaw)     │
                              └─────────────────┘
```

## 🧹 Maintenance: Pulling & Updating

To keep your personal instance up-to-date with the latest features and fixes:

### 1. Pull Latest Changes
Run this in your project root to get the newest code:
```bash
git pull origin main
```

### 2. Update Dependencies & Rebuild
After pulling, update your environment:
```bash
pnpm install
pnpm ui:build
pnpm build
```

### 3. Restart the Gateway
If you have a running gateway, restart it to apply changes:
```bash
openclaw gateway --port 18789 --verbose
```

---

## 🧩 Key Subsystems
*   **Gateway**: The central control plane (WebSocket server).
*   **Channels**: Connectors for WhatsApp, Telegram, Slack, Discord, Signal, iMessage, and more.
*   **Pi Agent**: The reasoning engine that handles your requests.
*   **UI**: Built-in Control UI and WebChat at the gateway port.
*   **Nodes**: Companion apps for **macOS**, **iOS**, and **Android**.

## ⚙️ Configuration
Settings are stored in `~/.openclaw/openclaw.json`. Check your setup:
```bash
openclaw doctor
```
