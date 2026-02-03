# Ahssistant

Configuration repository for Home Assistant.

## Structure

This repository uses a `custom-config/` directory to manage dashboard configurations and other custom YAML files. This allows for version control of dashboards that might otherwise be managed via the UI in storage mode.

### `custom-config/`

- **`home-desktop.yaml`**: Configuration for the main desktop dashboard. This dashboard uses the "Sections" view type and includes:
    - **Quick Access**: Enhanced greeting, temperature graph (mini-graph-card), and room selector.
    - **Active Room**: Context-aware controls that appear based on the selected room.
    - **Global Control**: Master switches for lights and doors.
    - **Waste Collection**: `trash-card` configuration for upcoming scheduled collections.

## Usage

To use these configurations:
1.  Copy the content from `custom-config/home-desktop.yaml`.
2.  In Home Assistant, create a new "Sections" dashboard (or edit an existing one).
3.  Enter "Raw Configuration Editor" mode.
4.  Paste the content.

## Setup
(Add setup instructions here if needed)
