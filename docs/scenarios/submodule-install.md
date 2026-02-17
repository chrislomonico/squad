# Using Squad as a Git Submodule (No npx Required)

You can add Squad directly to your repository as a git submodule instead of using `npx`. This keeps Squad version-pinned, fully offline-capable, and removes any dependency on npm at runtime.

## Setup

### 1. Add the submodule

From your project root:

```bash
git submodule add https://github.com/bradygaster/squad .squad
```

This clones Squad into a `.squad/` directory in your repo.

### 2. Configure VS Code to discover the agent

Create or update `.vscode/settings.json`:

```json
{
  "chat.promptFiles.locations": {
    ".squad/.github/agents": true
  }
}
```

This tells VS Code to look for agent files inside the submodule. **Squad** will appear in the Copilot agent picker automatically.

### 3. Start using Squad

Open Copilot Chat in VS Code, select **Squad** from the agent list, and say:

> "Let's set up my team"

Squad will detect that no team exists yet and walk you through team creation. When it needs to scaffold the project (directories, templates, workflows), it can run the setup script automatically:

```bash
node .squad/index.js
```

You don't need to run this yourself — the agent handles it. But you can run it manually if you prefer.

## Updating Squad

Pull the latest version of the submodule:

```bash
git submodule update --remote .squad
```

Then either ask the agent to upgrade, or run manually:

```bash
node .squad/index.js upgrade
```

## Cloning a repo that uses this setup

When someone clones your repo for the first time, they need to initialize the submodule:

```bash
git clone --recurse-submodules <your-repo-url>
```

Or if already cloned:

```bash
git submodule update --init
```

## What the setup script creates

Running `node .squad/index.js` scaffolds your project with:

| Path | Purpose |
|------|---------|
| `.ai-team/` | Team state — roster, decisions, agent histories, skills |
| `.ai-team-templates/` | Format guides for runtime files |
| `.ai-team/casting/` | Persistent character naming state |
| `.ai-team/skills/` | Starter skill definitions |
| `.ai-team/plugins/` | Plugin marketplace config |
| `.github/workflows/` | Squad CI/CD workflows |
| `.gitattributes` | Merge rules for append-only team files |

The script never overwrites your team state in `.ai-team/` — it only creates new files and directories.

## Optional: Add .squad to .gitignore

If you don't want to commit the submodule reference (e.g., each contributor adds it locally), you can `.gitignore` it instead. In that case, each contributor runs the `git submodule add` step themselves. However, committing the submodule reference is recommended so the team stays in sync on the same Squad version.
