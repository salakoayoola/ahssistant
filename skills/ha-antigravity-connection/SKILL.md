---
name: ha-antigravity-connection
description: Guide for connecting Google Antigravity to a local Home Assistant instance via MCP.
---

# Connect Google Antigravity to Home Assistant

This skill documents the specific configuration required to connect the Google Antigravity agent to a local Home Assistant instance using the Model Context Protocol (MCP).

## Challenge
Antigravity runs in a containerized or sandboxed environment. Accessing `http://homeassistant.local:8123` often fails because mDNS definition is not propagated to the container.

## Solution

### 1. Prerequisite: Long-Lived Access Token
1.  Log in to Home Assistant.
2.  Click on your **Profile** (bottom left user icon).
3.  Scroll to **Long-Lived Access Tokens**.
4.  Click **Create Token**.
5.  Name it `antigravity-agent`.
6.  **Copy the token immediately**. You cannot see it again.

### 2. Configuration Parameters

When the agent asks for connection details, use the following:

*   **URL**: Use the **IP Address** instead of the `.local` hostname to ensure reliable routing.
    *   *Bad*: `http://homeassistant.local:8123`
    *   *Good*: `http://192.168.1.50:8123` (Replace with your HA static IP)
*   **Token**: The Long-Lived Access Token generated in Step 1.

### 3. Connection Verification

The agent will attempt to list available MCP tools.
1.  Ask the agent: "Check connection to Home Assistant".
2.  The agent should run a tool like `ha_check_config` or `ha_list_entities`.
3.  If successful, the tool will return JSON data.

### 4. Troubleshooting

*   **Connection Refused**: Check if HA is running and if the IP is correct.
*   **Unauthorized**: Regenerate the token and ensure no trailing spaces were copied.
*   **404 Not Found**: Ensure you included the port `:8123` in the URL.
