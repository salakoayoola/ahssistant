# Contribution Proposal: Antigravity Skills for Home Assistant

This folder contains a set of new skills developed during a Google Antigravity session to enhance the `home-assistant-vibecode-agent`.

## Included Skills

### 1. `ha-energy-helpers`
*   **Purpose**: Solves the common issue where "smart" switches report Power (W) but not Energy (kWh), making them invisible to the Energy Dashboard.
*   **Function**: Guides the agent/user to identifying attributes and creating Riemann Sum Integral sensors.

### 2. `ha-dashboard-baseline`
*   **Purpose**: Establishes a "Gold Standard" for creating dashboards.
*   **Function**: Promotes the use of the new "Sections" view, responsive design principles, and specific card choices (Mushroom/Tile) for a premium feel.

### 3. `ha-antigravity-connection`
*   **Purpose**: Addresses connectivity challenges in sandboxed AI environments.
*   **Function**: Documents the requirement for IP-based routing (vs mDNS) and Long-Lived Access Tokens for reliable MCP connection.

## Integration Plan

We propose adding these directories to the `skills/` folder of the main repository.

```text
skills/
├── ha-energy-helpers/
│   └── SKILL.md
├── ha-dashboard-baseline/
│   └── SKILL.md
└── ha-antigravity-connection/
    └── SKILL.md
```

These skills empower the agent to autonomously solve complex configuration and UI design tasks without needing to "reinvent the wheel" each session.
