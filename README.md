<p align="center">
  <img src="https://raw.githubusercontent.com/OpenAgentFlow/OpenAgentFlow/master/docs/assets/oaf-logo.svg" alt="OpenAgentFlow Logo" width="120"/>
</p>

# OpenAgentFlow Support

> *What OpenAPI is for REST APIs, **OpenAgentFlow** is for AI agent workflows.*

Official Visual Studio Code language support for **OpenAgentFlow (`.oaf`)** — the portable, runtime-independent specification for AI agent workflows.

<p align="center">
  <img src="https://raw.githubusercontent.com/OpenAgentFlow/OpenAgentFlow/master/docs/assets/demo.gif" alt="OpenAgentFlow — compile and execute .oaf workflows live" width="720"/>
</p>

---

## 🚀 Get Started in 60 Seconds

Clone our **[Starter Repository](https://github.com/OpenAgentFlow/OpenAgentFlow-starter)** and run your first multi-agent workflow immediately:

```bash
git clone https://github.com/OpenAgentFlow/OpenAgentFlow-starter.git my-agents
cd my-agents
npm install && npm run setup
npm run triage
```

Or install the CLI globally and author workflows from scratch:

```bash
npm install -g openagentflow
oaf run my-workflow.oaf --input data.json
```

> 📖 **Full documentation**: [openagentflow.github.io/OpenAgentFlow](https://openagentflow.github.io/OpenAgentFlow/)

---

## 🔗 Ecosystem

| Resource | Link |
| :--- | :--- |
| 📦 **Core Compiler & Spec** | [OpenAgentFlow/OpenAgentFlow](https://github.com/OpenAgentFlow/OpenAgentFlow) |
| 🚀 **Starter Repository** | [OpenAgentFlow/OpenAgentFlow-starter](https://github.com/OpenAgentFlow/OpenAgentFlow-starter) |
| 📚 **Documentation** | [openagentflow.github.io/OpenAgentFlow](https://openagentflow.github.io/OpenAgentFlow/) |
| 📥 **npm Package** | [openagentflow on npm](https://www.npmjs.com/package/openagentflow) |

---

## ✨ Features

- **Full Syntax Highlighting (`source.oaf`)**: Accurate semantic and lexical highlighting for `.oaf` and `.openagentflow` files according to the official OpenAgentFlow language specification.
- **Keyword & Block Recognition**: Highlighting for top-level workflow blocks (`workflow`, `agent`, `state`, `flow`, `config`).
- **Type Expressions**: Support for primitive (`string`, `int`, `float`, `bool`) and generic (`list`, `map`) types.
- **State Options & Decorators**: Distinct highlighting for variable decorators such as `@required`, `@default`, `@description` / `@desc`, `@reducer`, `@min`, and `@max`.
- **Agent & Config Properties**: Dedicated colorization for property keys (`instructions`, `model`, `provider`, `temperature`, `tools`, `inputs`, `outputs`, `max_iterations`, `timeout_seconds`, `runtime`, `version`).
- **Multi-Line Triple-Quoted Strings**: Highlighting and auto-closing for `""" ... """` strings and `" ... "` strings with escape sequence recognition (`\n`, `\t`, `\"`, `\\`, etc.).
- **Flow Operators & Constants**: Colorization for flow graph edges (`->`) and reserved nodes (`start`, `end`).
- **Smart Editor Configuration**: Auto-closing brackets (`{}`, `[]`, `()`), line comments (`//`), and smart indentation rules when opening/closing blocks.

---

## 📝 Example Code (`.oaf`)

```oaf
// Summarize workflow: analyze text then produce a summary
workflow "Summarize" {

    config {
        version: "0.1"
        runtime: "langgraph"
        timeout_seconds: 60
    }

    state {
        request: string
        source_text: string @required @description("Original text to summarize")
        key_points: list[string]
        summary: string
    }

    agent Analyst {
        instructions: """
        Analyze the request and source text.
        Identify the most important facts, themes, and action items.
        Produce concise key_points only.
        """
        model: "gemma-4-26b-a4b-it"
        temperature: 0.2
        inputs: [request, source_text]
        outputs: [key_points]
    }

    agent Writer {
        instructions: """
        Use the key_points to write a clear, concise summary.
        Preserve meaning, remove redundancy, and match the requested tone.
        """
        model: "gemma-4-26b-a4b-it"
        temperature: 0.7
        inputs: [key_points]
        outputs: [summary]
    }

    flow {
        start -> Analyst
        Analyst -> Writer
        Writer -> end
    }

}
```

---

## ⚙️ Installation & Usage

1. Open Visual Studio Code.
2. Go to the Extensions tab (`Ctrl+Shift+X` or `Cmd+Shift+X`).
3. Search for **OpenAgentFlow Support** or install directly from `.vsix`.
4. Any file with `.oaf` or `.openagentflow` extension will automatically activate the syntax highlighting and language configuration.

---

## 📄 License

MIT License
