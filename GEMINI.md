# ChatAgentCore

## Project Overview

ChatAgentCore is a middleware service designed to bridge Qt-based AI applications with major Chinese enterprise chat platforms. It acts as a unified interface layer, allowing AI applications to interact with these platforms without handling platform-specific protocols directly.

**Key Features:**
*   **Multi-Platform Support:** Currently supports **Feishu (Lark)**, **QQ (BotPy)**, and **DingTalk (Stream Mode)**. WeCom support is planned.
*   **WebSocket Long Connection:** Uses official SDKs (e.g., `lark-oapi`, `qq-botpy`, `dingtalk-stream`) to establish persistent WebSocket connections, eliminating the need for public IPs or complex network tunneling.
*   **Unified Interface:** Provides a standard HTTP API for sending messages and a WebSocket interface for receiving events/messages in real-time.
*   **Process Management:** Built-in manager to lifecycle-control the backend AI assistant process (`uos-ai-assistant`).
*   **Configuration Driven:** Fully configurable via YAML, supporting dynamic hot-reloading without service interruption.
*   **Local Deployment:** Optimized for running on personal computers or local servers alongside the AI application.

## Architecture

The system follows a layered architecture:

1.  **Interface Layer (`api/`)**:
    *   **HTTP API (FastAPI):** Handles synchronous requests (e.g., sending messages) from the AI application.
    *   **WebSocket Server:** Pushes real-time events (incoming messages) to the AI application.

2.  **Core Service Layer (`core/`)**:
    *   **Adapter Manager:** Manages the registration, loading, and hot-reloading of platform adapters.
    *   **Process Manager:** Manages the lifecycle of external AI assistant processes.
    *   **Router:** Routes incoming messages to the Event Bus and outgoing messages to the appropriate Platform Adapter.
    *   **Event Bus:** Publishes message events to subscribers (Loggers, WebSocket clients).
    *   **Config Manager:** Manages configuration loading and validation with hot-reload support.

3.  **Platform Adapter Layer (`adapters/`)**:
    *   **Base Adapter:** Defines the abstract interface for all platform adapters.
    *   **Feishu Adapter:** Implements the Feishu protocol using `lark-oapi` (WebSocket SSE).
    *   **QQ Adapter:** Implements the QQ Bot protocol using `qq-botpy`.
    *   **DingTalk Adapter:** Implements the DingTalk protocol using `dingtalk-stream`.

## Building and Running

### Prerequisites

*   Python 3.10+
*   Platform Credentials (App ID, App Secret/Token) for enabled adapters.

### Installation

1.  **Create Virtual Environment:**
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # or venv\Scripts\activate on Windows
    ```

2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Install Package in Editable Mode:**
    ```bash
    pip install -e .
    ```

### Configuration

Copy the example configuration and edit it:

```bash
cp config/config.yaml.example config/config.yaml
```

**Key Configuration Fields (`config/config.yaml`):**
*   `platforms.<platform>.enabled`: Set to `true`.
*   `platforms.<platform>.config`: Specific credentials for the platform.
*   `server.host` / `server.port`: API server settings.

### Running the Service

```bash
# Run the main application
python main.py
```

### Verification & Testing

Use the interactive CLI tools to verify platform connections and send/receive messages:

*   **Feishu:** `python cli/test_feishu_ws.py`
*   **QQ:** `python cli/test_qq_ws.py`

**Common CLI Commands:**
*   Type text to reply to the last sender/conversation.
*   `/status`: Check connection status and message statistics.
*   `/set <id> [type]`: Manually set target recipient ID and type.
*   `/help`: Show available commands.

## Development Conventions

*   **Code Style:** Follows PEP 8. Format with `black` and lint with `ruff`.
*   **Type Hinting:** Extensive use of Python type hints (`mypy` enabled).
*   **AsyncIO:** The core is built on `asyncio`. Platform SDKs running in threads are carefully bridged using `run_coroutine_threadsafe`.
*   **Logging:** Uses `loguru` for structured, colorized logging.
*   **Testing:** Uses `pytest` with `pytest-asyncio`. Run tests via `pytest`.

## Key Files & Directories

*   `chatagentcore/api/main.py`: Application entry point and lifecycle management.
*   `chatagentcore/core/adapter_manager.py`: Central hub for platform integrations.
*   `chatagentcore/adapters/`: Implementation of various platform protocols.
*   `cli/`: Interactive testing tools for platform verification.
*   `docs/architecture/system-design.md`: Detailed system architecture documentation.
