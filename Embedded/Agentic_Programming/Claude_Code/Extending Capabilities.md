## Overview
- **CLAUDE.md** adds persistent context Claude sees every session.
- **Skills** add reusable knowledge and invocable workflows.
- **Code intelligence** connects Claude to a language server.
- **MCP** connects Claude to external services and tools.
- **Subagents** run their own loops in isolated context, returning summaries.[^1]
- **Dynamic workflows** runs many subagents from a script Claude writes, returning one result.
- **Cross-session messaging** lets Claude pass a message from one session to another.
- **Hooks** run script, HTTP request, MCP tool call, prompt, or subagent when CC reaches a lifecycle event.
- **Plugins** and **marketplaces** package and distribute these features.

A plugin is a package of skills, agents, hooks, MCP servers, LSP servers, and monitors.

[^1]: This doesn't add context to the main chat.
