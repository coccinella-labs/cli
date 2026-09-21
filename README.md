<p align="center">
  <img src="https://raw.githubusercontent.com/Coccinella-Labs/cli/main/.github/assets/thumbnail.png" alt="cli" width="100%">
</p>

# coccinella-labs

Master CLI to control all Coccinella Labs repositories.

## Dynamic Repository Management

The CLI fetches the list of repositories dynamically from [coccinella-labs/config](https://github.com/coccinella-labs/config) → `repos.json`. This means you don't need to update the CLI when adding new repos - just update the JSON file!

### To add new repos:
1. Update [repos.json](https://github.com/coccinella-labs/config/blob/main/repos.json) in the config repo
2. All coccinella-labs CLI commands will automatically use the updated list

## Installation

```bash
gh extension install coccinella-labs/cli
```

Or add to PATH:
```bash
cp coccinella-labs /usr/local/bin/
```

## Usage

```bash
# List all repositories
coccinella-labs list

# Clone all repos
coccinella-labs clone ~/coccinella-labs

# Pull all repos
coccinella-labs pull

# Push all repos
coccinella-labs push

# Show status
coccinella-labs status

# Create new repo
coccinella-labs create new-repo "Description"

# Execute command in all repos (tested with real example)
coccinella-labs exec "echo 'test' > test.txt"
coccinella-labs exec "git add -A && git commit -m 'chore: add test file' && git push"
```

## Examples - Tested Workflow

```bash
# 1. Clone all repos
coccinella-labs clone ~/coccinella-labs

# 2. Change to the cloned directory
cd ~/coccinella-labs

# 3. Add a file to all repos
coccinella-labs exec "echo 'test' > test.txt"

# 4. Commit and push to all repos (successfully pushed to all 11 repos!)
coccinella-labs exec "git add -A && git commit -m 'chore: add test file' && git push"
```

## Commands

| Command | Description |
|---------|-------------|
| `list` | List all Coccinella Labs repos |
| `clone [dir]` | Clone all repos to directory |
| `pull` | Pull all cloned repos |
| `push` | Push all cloned repos |
| `status` | Show status of all repos |
| `create <name> [desc]` | Create new repository |
| `exec <command>` | Execute command in all repos |

## Repositories Managed

Managed dynamically from `repos.json` in [coccinella-labs/config](https://github.com/coccinella-labs/config).

## Future: Automation with GitHub Bot

A GitHub bot can be created to:
- Automatically sync repos list from config to all extensions
- Trigger updates when `repos.json` changes
- Run scheduled tasks across all repos

To implement, you would need:
1. Create a GitHub App or use existing token
2. Add repository dispatch webhook
3. Create a workflow that listens for config changes

Would you like to create a bot for this automation?