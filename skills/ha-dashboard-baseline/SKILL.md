---
name: ha-dashboard-baseline
description: Create a standard, responsive Home Assistant dashboard using 'Sections' view and core design principles.
---

# Home Assistant Baseline Dashboard Skill

This skill guides you through creating a "Gold Standard" dashboard in Home Assistant, focusing on responsiveness, usability, and modern refined aesthetics.

## 1. Principles

1.  **Context is King**: Create separate dashboards for **Desktop** (info-dense), **Mobile** (action-oriented), and **Tablets/Wall Panels** (glanceable).
2.  **Use "Sections" View**: This is the modern standard. It allows for drag-and-drop, Z-grid layout, and responsive resizing.
3.  **No Dead Space**: Aim for high information density without clutter.

## 2. Setup (YAML Mode)

While "storage mode" (UI) is common, for reproducible setups we use YAML.

**Structure:**
```yaml
views:
  - title: Home
    type: sections
    max_columns: 4 # Optimized for Desktop
    path: home
    icon: mdi:home
    sections:
      - type: grid
        title: "Global Control"
        cards:
          - type: tile
            entity: light.all_lights
          - type: tile
            entity: lock.front_door
      - type: grid
        title: "Climate"
        cards:
           - type: thermostat
             entity: climate.home
```

## 3. Card Selection Standards

*   **Primary Controls**: Use `tile` or `mushroom-entity-card`. They are touch-friendly and aesthetically pleasing.
*   **Graphs**: Use `mini-graph-card` (HACS) for aesthetically pleasing data visualization.
*   **Conditions**: Use `conditional` cards to hide clutter (e.g., only show "Turn Off Lights" if lights are actually on).
*   **Layout**: Keep section widths consistent.
    *   **Mobile**: 1 section wide.
    *   **Tablet**: 2 sections wide.
    *   **Desktop**: 3-4 sections wide.

## 4. Implementation Steps

1.  **Create View**: Go to Edit Dashboard -> add View -> Select "Sections".
2.  **Define Sections**: Create vertical stacks (grids) for logical groups (e.g., "Living Room", "Security", "Energy").
3.  **Add Cards**: Populate with `tile`, `mushroom`, or `button` cards.
4.  **Refine**:
    *   Add **Greeting** (Markdown card with template).
    *   Add **Weather** (Weather card or chips).
    *   Add **Navigation** (Chips to jump between sub-views).
