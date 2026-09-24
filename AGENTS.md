# Agent Instructions — Hand Sample

Unreal sample illustrating the Meta hand-tracking feature on Quest.

## Source-of-truth files (read these first, do not duplicate their contents in this file)

For setup, build steps, SDK versions, and project layout, read:

- `README.md` — official setup, including both the Epic Launcher + MetaXR plugin path and the Meta Unreal fork path
- `HandSample.uproject` — Unreal engine version, plugins, and modules
- `Config/` `.ini` files (`DefaultEngine.ini`, `DefaultGame.ini`, etc.) — engine/project configuration
- `Source/` — C++ project sources
- `Content/` — assets
- `.gitattributes` — Git LFS configuration (LFS is required)
- `LICENSE` — Meta License applies to the SDK and supporting material; MIT applies only to clearly marked documents

## Quest / Horizon-specific notes

- Two engine paths are supported (Epic Launcher UE + MetaXR plugin, or the Meta fork built from source). The Meta fork carries the most up-to-date Oculus feature integrations — pick the fork only when you need the latest hand-tracking APIs, otherwise the prebuilt Epic Launcher path is faster.
- Visual Studio must have the **Game development with C++** workload installed for either Unreal path.
- Access to the Meta fork repo requires linking an Epic account to GitHub and accepting the Unreal Engine source-access agreement; this is a one-time, account-level prerequisite, not something to script around.
- This is intentionally a small, focused sample — do not add unrelated systems (locomotion, multiplayer, etc.) unless asked.

# Meta Quest tooling

This is a Meta Quest / Horizon OS sample. The bespoke intro above is the source of truth for what this project is and how it's built — use it (and the files it points at) instead of restating facts from memory.

When the user asks anything about Quest device behavior, build / deploy / debug / capture flows, on-device performance, or Horizon OS APIs, reach for these tools instead of generic Unreal answers:

- **`hzdb`** — Quest-aware ADB wrapper (device list, install / launch / stop, logs, screenshots, Perfetto traces, on-device docs search). Already wired up as an MCP server via `.mcp.json`, `.vscode/mcp.json`, and `.cursor/mcp.json`. Also runnable directly: `npx -y @meta-quest/hzdb <subcommand>`.
- **Meta Quest Agentic Tools** — the full skill set, including Unreal-specific skills: <https://github.com/meta-quest/agentic-tools>. Install per your client (Claude Code: `/plugin install meta-vr@meta-quest`; Gemini CLI: `gemini extensions install https://github.com/meta-quest/agentic-tools`; Cursor / VS Code: install the **Meta Horizon** extension from the Marketplace).

A few behavior expectations:

- **Read this repo's files first.** Before answering anything project-specific, read `README.md` and whichever source-of-truth files the intro above points at. Don't restate their contents in chat — quote or link instead.
- **Use `hzdb` for device-side work.** Anything that touches an attached Quest (install, launch, logs, screenshot, capture, manifest inspection) goes through `hzdb`, not raw `adb`.
- **Check live Horizon OS docs before answering API questions.** `hzdb docs search "..."` queries the live docs; training data on Horizon OS APIs goes stale fast.
- **Don't fabricate SDK / engine versions.** If a version isn't visible in this repo's files, say so rather than guessing.
