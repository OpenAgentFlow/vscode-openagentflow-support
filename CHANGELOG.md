# Change Log

All notable changes to the "openagentflow-support" extension will be documented in this file.

## [0.0.1] - 2026-07-18

### Added
- **Syntax Highlighting**: Comprehensive TextMate grammar (`source.oaf`) for `.oaf` and `.openagentflow` files.
- **Top-Level Blocks**: Highlighting for `workflow`, `agent`, `state`, `flow`, and `config` blocks.
- **Type Expressions**: Support for primitive (`string`, `int`, `float`, `bool`) and generic (`list`, `map`) types.
- **State Options & Decorators**: Recognition for decorators such as `@required`, `@default`, `@description`, `@secret`, `@persist`, `@reducer`, `@min`, `@max`, and `@pattern`.
- **Properties & Attributes**: Dedicated colorization for agent properties (`instructions`, `model`, `provider`, `temperature`, `tools`, `inputs`, `outputs`) and config keys (`max_iterations`, `timeout_seconds`, `runtime`, `version`).
- **Strings & Escapes**: Multi-line triple-quoted strings (`"""`) and double-quoted strings (`"`) with escape sequence recognition (`\n`, `\t`, `\"`, `\\`).
- **Flow Operators**: Highlighting for edge operator (`->`) and reserved nodes (`start`, `end`).
- **Language Configuration**: Auto-closing pairs for brackets and strings, line comment toggle (`//`), and smart indentation rules when opening/closing block braces (`{ }`).
