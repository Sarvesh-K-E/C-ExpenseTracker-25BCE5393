```text
╔════════════════════════════════════════════════════════════════════════╗
║                                                                        ║
║   ██████╗ ███████╗██████╗ ███████╗ ██████╗ ███╗   ██╗ █████╗ ██╗       ║
║   ██╔══██╗██╔════╝██╔══██╗██╔════╝██╔═══██╗████╗  ██║██╔══██╗██║       ║
║   ██████╔╝█████╗  ██████╔╝███████╗██║   ██║██╔██╗ ██║███████║██║       ║
║   ██╔═══╝ ██╔══╝  ██╔══██╗╚════██║██║   ██║██║╚██╗██║██╔══██║██║       ║
║   ██║     ███████╗██║  ██║███████║╚██████╔╝██║ ╚████║██║  ██║███████╗  ║
║   ╚═╝     ╚══════╝╚═╝  ╚═╝╚══════╝ ╚═════╝ ╚═╝  ╚═══╝╚═╝  ╚═╝╚══════╝  ║
║                                                                        ║
║     ███████╗██╗███╗   ██╗ █████╗ ███╗   ██╗ ██████╗ ███████╗           ║
║     ██╔════╝██║████╗  ██║██╔══██╗████╗  ██║██╔════╝ ██╔════╝           ║
║     █████╗  ██║██╔██╗ ██║███████║██╔██╗ ██║██║      █████╗             ║
║     ██╔══╝  ██║██║╚██╗██║██╔══██║██║╚██╗██║██║      ██╔══╝             ║
║     ██║     ██║██║ ╚████║██║  ██║██║ ╚████║╚██████╗ ███████╗           ║
║     ╚═╝     ╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚══════╝           ║
║                                                                        ║
║      ████████╗██████╗  █████╗  ██████╗ ██╗  ██╗███████╗██████╗         ║
║      ╚══██╔══╝██╔══██╗██╔══██╗██╔════╝ ██║ ██╔╝██╔════╝██╔══██╗        ║
║         ██║   ██████╔╝███████║██║      █████╔╝ █████╗  ██████╔╝        ║
║         ██║   ██╔══██╗██╔══██║██║      ██╔═██╗ ██╔══╝  ██╔══██╗        ║
║         ██║   ██║  ██║██║  ██║╚██████╗ ██║  ██╗███████╗██║  ██║        ║
║         ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝        ║
║                                                                        ║
╚════════════════════════════════════════════════════════════════════════╝
```

# 💵 Personal Finance Management System

A WebAssembly-powered, retro-terminal styled expense tracker with cloud synchronization and AI financial insights. Built in C and deployed to the modern web.

---

## 🎯 Overview

The Personal Finance Management System is a lightweight, high-performance financial tracking application. Originally written in C, it is compiled to WebAssembly (Wasm) to run entirely within the browser. It features a custom ANSI-compliant terminal emulator wrapped in a sleek, retro-inspired graphical interface, offering a robust set of tools to manage expenses, track budgets, and gain AI-driven insights natively.

## ✨ Key Features

- **Blazing Fast Wasm Core:** The entire backend logic runs securely and instantly in the browser via WebAssembly, requiring no traditional backend server.
- **Retro Terminal Interface:** Full ANSI color support, custom keyboard navigation, and an interactive command-line experience built for the web.
- **Cloud Sync:** Secure, PIN-protected synchronization with Supabase storage to seamlessly persist your serialized `.dat` files across devices.
- **AI Financial Advisor:** Integrated Google Gemini architecture to analyze your monthly spending and provide actionable, context-aware financial tips.
- **Comprehensive Analytics:**
  - Real-time monthly budget dashboard with ASCII progress tracking.
  - Detailed itemized reports and category-wise spending charts.
  - Quick search, sorting, and inline editing workflows.
- **Data Portability:** Complete import and export capabilities utilizing standard CSV formats, including a drag-and-drop web import module.
- **Encrypted Enclave:** AES-style payload management leveraging a secure PIN layer to unlock APIs and cloud sync environments.

---

## 🏗️ Architecture Stack

- **Core Logic:** `C11` standard, utilizing standard library I/O adapted for Emscripten's virtual file systems.
- **Web Layer:** `HTML5`, `Vanilla JS`, and `CSS3` providing the glassmorphic terminal shell, pixel-perfect UI rendering, and bridging between JS APIs and the Wasm standard streams.
- **Compiler Target:** `Emscripten` (`emcc`) heavily utilizing Asyncify to handle synchronous C input paradigms (like `fgets` and `getch()`) natively in an asynchronous browser thread.
- **External Integrations:** `Supabase` (Storage API) and `Gemini 2.5 Flash` (Generative AI API).

## 🚀 Build & Deployment

### Prerequisites
- [Emscripten SDK (emsdk)](https://emscripten.org/docs/getting_started/downloads.html) configured in your environment PATH.
- PowerShell (for the build script)

### Compilation
1. Navigate to the `src` directory containing the source files.
2. Execute the automated PowerShell build sequence:
   ```powershell
   .\build_web.ps1
   ```
   *This compiles `main.c`, initializes the Emscripten runtime, and bundles `web_shell.html` and `web_terminal.js` into the final `/web` distribution directory.*

### Running Locally
Start a local static server to serve the generated Wasm files:
```bash
python -m http.server 8000 --directory web
```
Navigate to `http://localhost:8000` in your preferred browser.

---

## 💻 Usage & Navigation

Upon launching the application, you will be prompted to enter a secure numeric PIN to unlock the environment. Once authenticated, the terminal initializes and loads your host files from the cloud.

System navigation leverages standard keyboard interfaces:
- **Up/Down Arrows:** Traverse menu options and data tables.
- **Enter:** Select highlighted options or execute commands.
- **Live Search (S):** Rapidly filter data categories and notes in the management views.
- **Standard Input:** Context-aware prompts for numbers, string inputs, and date parsing (e.g., typing `0` resolves to the current date).

---

*Compiled with Emscripten.*
