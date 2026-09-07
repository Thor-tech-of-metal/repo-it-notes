

## Comparison with Other Modes

| Mode | Purpose |
|--------|---------|
| **Ask** | Answers questions and explains code. |
| **Plan** | Creates a structured implementation strategy. |
| **Edit** | Modifies code directly. |
| **Agent** | Executes multi-step development tasks and can make code changes across files. |


## Simple Mental Model

- **Ask** → "Explain it."
- **Plan** → "Tell me how you'd do it."
- **Edit** → "Make the code changes."
- **Agent** → "Take the task and work through it."


## Agent
**Delegate to Coding Agent** allows you to assign a software development task to an autonomous AI coding agent rather than working through a traditional chat-based interaction. The agent can analyze a codebase, make changes, and prepare those changes for review in a pull request.

---

## 
**How it works**

When you delegate a task, the Coding Agent:

1. Receives your development request.
2. Analyzes the repository and project structure.
3. Identifies the files that need modification.
4. Implements the required code changes.
5. Creates or updates tests when appropriate.
6. Generates a draft Pull Request (PR) containing the proposed changes.
7. Requests your review before the changes are merged. 【1-89d56b】

---

## Agent Customization
Agent Customization in GitHub Copilot for IntelliJ enables teams to create reusable AI assistants tailored to their development workflows.
