## 1. Folders = Projects (mostly)

In VS Code, a project is essentially a **folder**:

- You open a folder
- That folder is treated as your working context
- Source code, configuration files, and build scripts live inside it

## 2. Workspace = Closest equivalent to IntelliJ projects

VS Code’s closest match to an IntelliJ project is a **Workspace**.

The only way to have a settings per project is by creating a workspace with a 1 or more folders.
File--> save as workspace that will create a workspace file 
File--> Open folder inside the created workspace

https://www.youtube.com/watch?v=k6mJwIQ6lO8

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
