---
name: ha-energy-helpers
description: Create Energy Dashboard compatible sensors from devices with hidden power attributes.
---

# Home Assistant Energy Helpers

This skill defines the workflow for converting devices that have power data hidden in attributes (or only report Watts) into entities compatible with the Home Assistant Energy Dashboard (which requires kWh).

## 1. Identify "Hidden" Power Data

Some devices (Zigbee, Tuya, etc.) report power usage as an attribute rather than a standalone sensor.
1.  Go to **Developer Tools > States**.
2.  Find your device (e.g., `switch.office_desk`).
3.  Look at the **Attributes** column for values like:
    *   `current_consumption` (often in Watts)
    *   `power`
    *   `load_power`

## 2. Create a Power Sensor (Watts)

First, expose the attribute as a dedicated sensor using the modern `template` platform in `configuration.yaml` (or `templates.yaml`).

**File:** `configuration.yaml`

```yaml
template:
  - sensor:
      - name: "Office Desk Power"
        unique_id: office_desk_power
        unit_of_measurement: "W"
        device_class: power
        state_class: measurement
        state: "{{ state_attr('switch.office_desk', 'current_consumption') }}"
```

> **Note:** Ensure `state_attr` matches the exact attribute name found in step 1.

## 3. Create an Energy Sensor (kWh)

Use the **Riemann Sum Integral** helper to calculate accumulated energy (kWh) from the live power reading (W).

**File:** `sensors.yaml` (or `sensor:` section in config)

```yaml
- platform: integration
  source: sensor.office_desk_power
  name: Office Desk Energy
  unit_prefix: k
  round: 2
  method: left
```

*   **source**: The entity ID of the power sensor created in Step 2 (or an existing power sensor).
*   **method**: Use `left` for devices that switch on/off (spiky loads). Use `trapezoidal` for continuous variable loads.
*   **unit_prefix**: `k` ensures the result is in `kWh`.

## 4. Finalize

1.  **Restart Home Assistant**.
2.  Go to **Settings > Dashboards > Energy**.
3.  Add the new `*_energy` sensor (e.g., `sensor.office_desk_energy`) to the "Individual Devices" list.
