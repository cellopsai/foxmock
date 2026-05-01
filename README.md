# FoxMock

**All-in-one HTTP, SFTP, and gRPC mock server built into your JetBrains IDE.**

Stop switching between tools. FoxMock lets you stub out REST APIs, SFTP file transfers, and gRPC services without leaving your editor — then switch between named test scenarios in one click.

---

## Features

| Feature | Details |
|---------|---------|
| **HTTP Mocking** | Define routes (method + path), add multiple named scenarios per route, enable/disable routes and scenarios individually |
| **Route Groups** | Organise routes into named groups; drag-and-drop routes between groups |
| **Collections** | Save/import route sets as JSON; selective export; conflict resolution on import (Keep / Replace / Merge) |
| **SFTP Mocking** | Local SFTP server with configurable credentials and root directory |
| **gRPC Mocking** | Load `.proto` files to stub individual RPC methods |
| **AI Generation** | Generate realistic JSON response bodies using OpenAI, Claude, Gemini, or a local Ollama instance |
| **Request Inspector** | Live transaction log for all three servers |
| **Dashboard** | Status cards with one-click start/stop per server |
| **Secure Credentials** | API keys are stored in the OS keychain via IntelliJ PasswordSafe — never written to disk |
| **IDE compatible** | IntelliJ IDEA, Android Studio, WebStorm, GoLand, PyCharm, Rider, CLion, and all other JetBrains IDEs |

---

## Installation

### From JetBrains Marketplace
1. Open **Settings → Plugins → Marketplace**
2. Search for **FoxMock**
3. Click **Install** and restart the IDE

### From source
```bash
git clone https://github.com/your-org/foxmock.git
cd foxmock
./gradlew :foxmock-plugin:buildPlugin
```
The plugin ZIP is written to `foxmock-plugin/build/distributions/`. Install it via **Settings → Plugins → ⚙ → Install Plugin from Disk**.

---

## Quick Start

1. Open **View → Tool Windows → FoxMock**
2. On the **Dashboard** tab, click **Start** on the HTTP card
3. Switch to the **HTTP Mock** tab and click **Add Route**
4. Fill in method (`GET`), path (`/api/hello`), scenario name (`success`), and response body
5. Point your application at `http://localhost:8089` — done

---

## HTTP Mock Server

### Adding routes
Click **Add Route** in the HTTP Mock tab. Each route has:
- **Method** — GET, POST, PUT, PATCH, DELETE, etc.
- **Path** — supports path parameters, e.g. `/users/{id}`
- **Scenarios** — one or more named responses; only one is active at a time

### Groups
Click **+** (top-right of the routes panel) to create a group. Drag routes into groups to organise them. Double-click a group name to rename it. The **×** button on a group row deletes the group (routes are un-grouped, not deleted).

### Collections
| Action | How |
|--------|-----|
| Save | Click **Save Collection** → choose routes to include → pick a file |
| Load | Click **Load Collection** → pick a JSON file → resolve any conflicts |

Conflict resolution per route:
- **Keep** — keep the existing route, discard incoming
- **Replace** — replace the existing route with incoming
- **Merge** — keep existing route, add only new scenarios from incoming

---

## SFTP Mock Server

Configure in **Settings → Tools → FoxMock**:
- **Port** — default `2222`
- **Root directory** — local path served as the SFTP root
- **Username / Password** — stored securely in the OS keychain

Connect with any SFTP client:
```
sftp -P 2222 mockuser@localhost
```

---

## gRPC Mock Server

1. Go to the **gRPC Mock** tab
2. Click **Load Proto File** and select a `.proto` file
3. Click on a method row to configure response JSON and add scenarios

---

## AI-Powered Generation

Configure an AI provider in the **AI Settings** tab:

| Provider | What you need |
|----------|--------------|
| **OpenAI** | API key from [platform.openai.com](https://platform.openai.com) |
| **Claude** | API key from [console.anthropic.com](https://console.anthropic.com) |
| **Gemini** | API key from [aistudio.google.com](https://aistudio.google.com) |
| **Ollama** | Ollama running locally; set the host (default `http://localhost:11434`) |

Click **Test Connection** after entering your credentials. Click **Generate with AI** inside any route/scenario dialog to auto-fill the response body.

---

## Keyboard Shortcuts

| Action | Default shortcut |
|--------|-----------------|
| Start all servers | `Alt+Shift+F` |
| Stop all servers | `Alt+Shift+X` |

Shortcuts can be customised in **Settings → Keymap → FoxMock**.

---

## Settings

Open **Settings → Tools → FoxMock** to configure:

| Setting | Default |
|---------|---------|
| HTTP port | `8089` |
| SFTP port | `2222` |
| gRPC port | `9090` |
| SFTP root directory | `~/.foxmock/sftp` |
| Auto-start HTTP on IDE startup | off |

---

## Building from Source

**Requirements**: JDK 17, Gradle 8+

```bash
# Build everything
./gradlew build

# Run tests (foxmock-core)
./gradlew :foxmock-core:test

# Run the plugin in a sandboxed IDE
./gradlew :foxmock-plugin:runIde

# Build the distributable ZIP
./gradlew :foxmock-plugin:buildPlugin
```

---

## Project Structure

```
foxmock/
├── foxmock-core/          # Server logic — HTTP (Javalin), SFTP (Apache SSHD), gRPC, AI
│   └── src/
│       ├── main/java/com/foxmock/core/
│       └── test/java/com/foxmock/core/
└── foxmock-plugin/        # IntelliJ plugin — UI, actions, settings
    └── src/main/
        ├── java/com/foxmock/plugin/
        └── resources/META-INF/
```

---

## License

FoxMock is proprietary software. Use is governed by the
[FoxMock End User License Agreement](LICENSE.html).
All rights reserved. &copy; 2026 FoxMock.

---

## Support / Issues

Please open an issue at the project repository or email `support@foxmock.dev`.
README_ac6025fb-fd78-4f22-9483-55a16b338e54.md
Displaying README_ac6025fb-fd78-4f22-9483-55a16b338e54.md.
