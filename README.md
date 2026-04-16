# Burp Suite MCP Server - Extended Edition 🚀

This repository is a feature-rich fork of the official [PortSwigger MCP Server](https://github.com/PortSwigger/mcp-server-main). It extends the original foundation to turn Burp Suite into an automated **Bambda** and **Scan Check** powerhouse using the Model Context Protocol (MCP).

---

## 🚀 Overview

While the original repository provides the essential bridge between LLMs and the Burp Montoya API, this **Extended Edition** introduces specialized tools that allow AI agents to generate and register complex Burp logic—such as filters, custom columns, and active scan checks—directly into your Burp instance using natural language.

---

## ✨ New Extended Features

I have implemented a specialized toolset that allows the AI to interface directly with Burp’s core logic engines.

### 🛠️ The Bambda & Scan Toolkit

| Feature | Capability | Target Locations |
| :--- | :--- | :--- |
| **Bambda Generator** | Instant generation of Java-based filters and actions. | Proxy, Logger, Target, Repeater |
| **Custom Columns** | Auto-create data-extraction columns for the UI. | HTTP History, Logger |
| **Active Scan Library** | Generate per-request custom audit checks. | Scanner Engine |
| **Library Integration** | Direct injection into the official Bambda Library. | Burp Suite 2025.10+ |

---

## ⚙️ Configuration & Official Setup

This extension builds upon the core MCP framework. For the baseline configuration—including how to connect your LLM (Claude, ChatGPT, etc.) and the structure of the `config.json` file—please refer to the official PortSwigger documentation:

* **Official Setup Guide:** [PortSwigger MCP Server Documentation](https://github.com/PortSwigger/mcp-server-main#setup)
* **MCP Protocol Details:** Learn more about the [Model Context Protocol](https://modelcontextprotocol.io).

---

## 📖 How to Build and Load

To get up and running with these custom tools:

1.  **Clone the Fork:**
    ```bash
    git clone [https://github.com/](https://github.com/)[Your-Username]/mcp-server-burp-extended.git
    ```
2.  **Build the Extension:**
    Run the following command in the root directory to compile the Montoya-compatible JAR:
    ```bash
    ./gradlew.bat embedProxyJar
    ```
3.  **Load into Burp:**
    * Open Burp Suite.
    * Go to **Extensions** > **Installed** > **Add**.
    * Select the JAR located in `mcp-server/build/libs/`.

---

## 💡 Real-World Examples

This fork is optimized to handle complex, multi-step security logic on the fly:

* **🔍 GraphQL Introspection (Custom Action):** Automatically converts standard GraphQL requests into introspection queries to map out the API schema.
    * *Location: REPEATER | Function: CUSTOM_ACTION*

* **🔑 JWT Algorithm Tracker (Custom Column):** Decodes JWTs found in Cookies or Authorization headers and displays the `alg` field (e.g., HS256, RS256) in the history view.
    * *Location: PROXY_HTTP_HISTORY | Function: CUSTOM_COLUMN*

* **🛡️ CORS Misconfig Checker (Active Scan):** Generates random origins and audits responses for insecure `Access-Control-Allow-Origin` and `Credentials` reflections.
    * *Location: SCANNER | Function: SCAN_CHECK_ACTIVE_PER_REQUEST*

---

## 🤝 Credits & Acknowledgments

This project is a dedicated extension of the original work by the **PortSwigger** team. It maintains compatibility with their original vision while adding high-utility security automation tools.

* **Original Repository:** [PortSwigger/mcp-server-main](https://github.com/PortSwigger/mcp-server-main)
* **Extended Features & Tooling by:** [Your Name/Handle]

---

### 🛡️ Security Note
*Generated scripts should always be reviewed before being applied to production environments. Bambdas and Scan Checks run with the permissions of the Burp Suite process.*