## What is Claude Code?
An agentic coding tool that
- reads your codebase
- edits files
- runs commands
- integrates with other dev tools
In other words, it is an AI-powered coding assistant help build features, fix bugs, and automate dev tasks.
## Claude Code Capabilities
- Automate tedious work: writing tests, fixing lint errors, resolving merge conflicts, updating dependencies, writing release notes.
- Build features and fix bugs: you plan in plain English, CC plans and executes.
- Create commits and pull requests.
- Connect to tools with MCP: MCP allows CC to read Google Docs, pull data from Slack...
- Customize with instructions, skill, and hooks:
	- **CLAUDE.md** is a markdown file that is used to customize CC. CC reads this file at the start of every session. This file can be used to set coding standards, architecture decisions, preferred libraries, and review checklists. CC also builds **auto-memory** to save learnings across sessions.
	- Create **skills** to package repeatable workflow, which can be shared.
	- **Hooks** let you run shell commands before or after CC actions like running lint before a commit or auto-formatting after every file edit.
- Run agents in parallel and build custom agents.
- Spawn multiple CC agents to work on different parts of the task simultaneously:
	- A lead agent coordinates the work, assigns subtasks, and merges results.
	- Use background agents to run several full sessions in parallel and watch them from one screen.
	- Use **Agent SDK** to build custom agents.
- Pipe, script, and automate with the CLI: composable and follows UNIX philosophy.
- Schedule recurring tasks.
	- **Routines** run in the cloud, can be triggered on API calls or GitHub events. In CLI, create them with `/schedule`. 
	- **Desktop scheduled tasks** run on local (your) machine.
	- `/loop` repeats a prompt within a CLI session for quick polling.
- Work from everywhere.
	- **Remote Control** to work from your phone or any browser.
	- Message **Dispatch** a task from your phone and open the Desktop session it creates.
	- Kick off a long-running task on the web or phone, then pull it into the terminal with `claude --teleport`.[^1]
	- `/Desktop` to continue your current terminal session in the Desktop app.
	- Route tasks from team chat: mention `@Claude` in Slack with a bug report and get a pull request back.
## How does it work?
CC is an agentic loop: when given a task, it will work through three phases: gather context, take action, and verify results. The loop is made up of **models** and **tools**. CC serve as **agentic harness** around Claude.
![[agentic-loop.png|400]]

[^1]: Require claude.ai subscription.
