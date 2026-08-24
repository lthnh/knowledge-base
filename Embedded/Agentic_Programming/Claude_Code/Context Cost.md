Every feature you add consumes some of Claude's context. Too much can fill up your context window and can noise to make Claude less effective.


| Feature           | When it loads                  | What loads                                                                 | Context cost                                 |
| ----------------- | ------------------------------ | -------------------------------------------------------------------------- | -------------------------------------------- |
| CLAUDE.md         | Session start                  | Full content                                                               | Every request                                |
| Skills            | Session start + when used      | Descriptions at start, full content when used                              | Low (description every request)              |
| MCP servers       | Session start                  | Tool names; full schemas on demand                                         | Low until a tool is used                     |
| Code intelligence | After file edits and on demand | Diagnostics after edits; symbol locations on lookup                        | Low; reduces file reads elsewhere            |
| Subagents         | When spawned                   | Fresh context with specified skills, or the parent conversation for a fork | Isolated from main session                   |
| Hooks             | On trigger                     | Nothing (runs externally)                                                  | Zero, unless hook returns additional context |
![[context-cost.png|500]]