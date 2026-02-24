# Agents

This directory contains generated automation agents created by the "App Action AI Agent" generator.

**Purpose**
- Store small, self-contained automation agents that run locally on a device (Termux/Linux/macOS) to perform safe, allowlisted tasks after an app is shared to the GitHub share target.

**How it works**
1. A share action (for example: "Share -> GitHub" on Android) should hand off basic context to a small local runner (Termux or equivalent).
2. The runner calls the generator (generate_agent.py) with the shared app name, optional content, and a short action history.
3. The generator creates a new folder inside this Agents/ directory with:
   - agent.py (the agent script, heavily commented)
   - metadata.yaml (agent metadata)
   - README.md (what this agent does and usage)
4. The agent scripts are intentionally conservative and only execute commands from Agents/allowlist.yaml.

**Security & safety**
- No secrets are stored in this repository. Any API keys must be provided via environment variables or GitHub Secrets.
- Agents are limited to an allowlist of actions. An agent runner verifies the allowlist at runtime.

**Using the generator**
- See generator usage in Agents/generate_agent.py. Example:

  python3 Agents/generate_agent.py --app "Notepad" --content "Notes from meeting" --output-dir Agents

**Support**
- For issues, open a GitHub issue in this repository. Keep logs and generated agent metadata to help debugging.
