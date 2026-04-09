## 1. Folders = Projects (mostly)

In VS Code, a project is essentially a **folder**:

- You open a folder
- That folder is treated as your working context
- Source code, configuration files, and build scripts live inside it

## 2. Workspace = Closest equivalent to IntelliJ projects

VS Code’s closest match to an IntelliJ project is a **Workspace**.

A workspace:

- Can contain one or multiple folders
- Stores settings in a `.code-workspace` file
- Supports:
  - Folder-specific settings
  - Debug configurations
  - Tasks
  - Extensions per workspace
 
Example workspace file:

{
  "folders": [
    { "path": "frontend" },
    { "path": "backend" }
  ],
  "settings": {
    "editor.tabSize": 2
  }
}
