# MCP

# 🧠 Understanding MCP (Model Context Protocol)

## 🌟 Why MCP?

Large Language Models (LLMs) are powerful, but **they can’t perform tasks by themselves**. They need **instructions** or **examples**—this is what we call **context**.

> Think of context as the environment or setup that tells the LLM *what to do* and *how to do it*.

---

## 📌 What is Context?

* In simple terms:
  **Context = Instructions + Examples**
  (i.e., how to complete a specific task)

* Without proper context, LLMs might respond inaccurately or incompletely.

---

## 🧱 Why Do We Need to Build Context Dynamically?

* We **can’t keep copy-pasting the same prompt** every time.
* We need to build context **dynamically and programmatically**.
* This is especially important when using different **data sources**, such as:

  * Databases
  * Google Sheets
  * PDFs
  * Docs
  * Images
  * Text or Image inputs

---

## 🎯 Moving Beyond Just Information

Modern LLMs aren’t just for answering questions — we want them to **perform tasks**, like:

* Automating alarms
* Sending reminders
* Interacting with tools (e.g., calendars, APIs, devices)

---

## 🔧 Tool/Function Calling by LLMs

LLMs like **ChatGPT**, **Claude**, **Perplexity** can **call functions** (tools) when given the proper context.

### But there’s a problem:

Each LLM provider has its **own way of defining and calling functions**.
This means developers must write **LLM-specific code** — not scalable!

---

## ✅ Enter MCP – The Standardized Protocol

**MCP (Model Context Protocol)** solves this by providing a **unified, standard way** to interact with LLMs and tools — no LLM-specific code required.

---

## 🧩 Key Terminology in MCP

| Term           | Description                                                               |
| -------------- | ------------------------------------------------------------------------- |
| **MCP Host**   | The platform where the LLM runs (e.g., ChatGPT, Claude, Cursor IDE, etc.) |
| **MCP Client** | The interface or tool that communicates with the LLM via the MCP Host     |
| **MCP Server** | Provides structured **context** to LLMs via tools, resources, and prompts |

---

## 🧠 What's Inside the MCP Server?

* **Tools**: These are the functions you define (e.g., send\_email, create\_event)
* **Resources**: Files like PDFs, docs, images (we don’t send the entire file—just a reference like a URL or relevant snippet)
* **Prompts**: Predefined instructions/templates to guide the LLM
* **Communication Protocol**: JSON-RPC 2.0 (a lightweight, structured messaging format)

---

## 🌐 Communication Flow (Client ↔ Server)

### Protocol Used: **JSON-RPC 2.0**

This is the common "language" used between MCP client and MCP server.

### Transport Methods Supported by MCP:

| Transport Type               | Use Case / Description                                      |
| ---------------------------- | ----------------------------------------------------------- |
| **HTTP I/O**                 | Standard HTTP requests/responses                            |
| **Streamable HTTP**          | Can handle **real-time streaming** and **multiple clients** |
| **SSE (Server Sent Events)** | Push updates from server to client in real-time             |

---

## 🔄 Typical Interaction Flow

1. **Client** sends an **initialization request**
2. **Server** responds (e.g., with context setup info)
3. **Client** sends **notifications** (e.g., user prompt or interaction)
4. **Server** sends back a **200 OK** status
5. Client and Server establish a **stable communication channel**

> Analogy: Just like YouTube uses English for videos and delivers it via the internet, MCP uses JSON-RPC 2.0 as its **language**, and HTTP/SSE as its **transport channel**.

---

## 🎯 Why MCP Matters

* **LLM-Agnostic Tool Calling**: Write once, use with any LLM
* **Standardized Communication**: Easier debugging, logging, and integration
* **Separation of Concerns**:

  * Developers define tools/resources in MCP server
  * Clients focus on interaction/UI without internal logic

---

## 🧠 Final Thoughts

MCP enables the **next generation of agentic AI systems** where LLMs are not just passive responders but **active doers** — performing tasks reliably across environments using a standardized, plug-and-play protocol.
