# xray — Hardware, Firmware, BLE & Mobile Reverse Engineering

AI Agent Skill for **Antigravity**, **Claude Code**, and **OpenAI Codex**. Evidence-first reverse engineering playbook combining APK decompilation (JADX/apktool), Frida SSL unpinning, BLE packet protocol analysis, binary firmware/watchface mapping, and Android/Linux debugging.

---

## Quick Install (Claude Code / Codex / Antigravity)

Clone this skill into your agent's global or project skills directory:

| Agent | Global Install Path | Project-Local Path |
| :--- | :--- | :--- |
| **Antigravity** | `~/.gemini/config/skills/xray` | `.agents/skills/xray` |
| **Claude Code** | `~/.claude/skills/xray` | `.claude/skills/xray` |
| **OpenAI Codex** | `~/.codex/skills/xray` | `.agents/skills/xray` |

```bash
# Example (Antigravity / Claude Code / Codex — pick your path):
git clone https://github.com/triwahyu45/xray.git ~/.claude/skills/xray
```

---

## Requirements & Dependencies (For Agents)

- **Runtime / Tools**: **JADX**, **apktool**, **ADB**, **Frida** (`frida-tools`), **Python 3.10+** (`scapy`/`bleak` for packet parsing); optional Ghidra/rizin
- **MCP Servers**: Recommended: `rea` MCP (Reverse Engineer Anything) for unified binary, Frida, JADX, & ADB inspection
- **Related Skills**: None required
- **API Keys / Secrets**: None

```json
{
  "mcpServers": {
    "rea": {
      "command": "npx",
      "args": ["-y", "rea-agents", "mcp"]
    }
  }
}
```

---

## Included Files

- `SKILL.md` — Evidence-first RE rules & byte-roundtrip Self-Audit Gate
- `references/mobile-and-ble-re.md` — JADX/apktool, Frida SSL unpinning, BLE & binary watchface/firmware workflows

## When to Trigger / Search Keywords

`xray`, `reverse engineering`, `apk`, `jadx`, `apktool`, `frida`, `ssl unpinning`, `ble packet`, `firmware`, `watchface`, `ghidra`
