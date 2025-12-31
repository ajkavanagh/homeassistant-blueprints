# Home Assistant Blueprints

These Blueprints are automations that I have found useful.  YMMV!  Feel free to
copy, update, etc, as needed.  Also feel free to open Issues or PRs for
new/updated Blueprints.

NOTE: these are ZHA *only* at the moment, as that's all I use.  They could be updated to use z2m.

These blueprints are **heavily** inspired and sourced from the original [Candeo Blueprints](https://github.com/candeosmart/homeassistant-blueprints). Without those, these Blueprints probably wouldn't have happened.

## Devices

1. Candeo [RD1-Pro](#rd1-pro-c-zb-rd1p-decoupled-dimming-switch)
2. SONOFF [SNZB-01P](#sonoff-snzb-01p-wireless-button)

## RD1-Pro (C-ZB-RD1P) Decoupled Dimming Switch

2 Blueprints for the RD1-Pro (C-ZB-RD1P) Decoupled Dimming Switch

### Smart Bulb control on single click and dimmer

Control a smart bulb using an RD1-Pro.  The single click turns the bulb on an off, and the rotations either brighten or dim the bulb.  Note that unlike the [Candeo Blueprint](https://github.com/candeosmart/homeassistant-blueprints/blob/main/candeo-blueprint-zha-RD1P-3-light-control-toggle-dimming.yaml) this *only* controls the brightness; the colour and temperature are not affected.  I found them difficult to use.

The blueprint includes a feature to ignore rotations for a configurable time (default 500ms) after pressing the switch button. This prevents accidental brightness changes when pressing the button.

#### Setup Requirements

Before using this blueprint, you need to create a helper entity in Home Assistant:

1. Go to **Settings** → **Devices & Services** → **Helpers** tab
2. Click **+ Create Helper** button
3. Select **Date and/or time**
4. Configure the helper:
   - **Name**: Something like "RD1P Last Press Time" (you'll select this in the blueprint)
   - **Type**: Select **Date and time** (not just date or just time)
5. Click **Create**

When configuring the blueprint automation, you'll select this helper entity in the "Last Press Timestamp Helper" field.

For ZHA:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/ajkavanagh/homeassistant-blueprints/blob/main/candeo-blueprint-zha-RD1P-toggle-light-and-dimming.yaml)

### Scene/Script Control with Double Press and Long Press

Cycle through scenes or scripts on double press, and trigger a dedicated scene/script with long press. Select up to six scenes or scripts in the blueprint. A simple numeric helper chooses which slot runs next.

This is modified from the original [Candeo](https://github.com/candeosmart/homeassistant-blueprints/blob/main/README.md#activate-your-scenes-or-scripts-from-your-wall-switch) one, in that *only* the double press and long press events are used. Single press and rotations are ignored by this blueprint, allowing it to work alongside the Smart Bulb control blueprint.

**Features:**

- **Double press**: Activates the current scene/script from your helper selection, then moves to the next (1 → 2 → … → N → 1)
- **Long press**: Runs a dedicated scene or script (independent of the helper)
- **Single press & rotations**: Ignored (can be handled by another blueprint)

#### Scene Setup Requirements

Before using this blueprint, you need to create a helper entity in Home Assistant:

1. Go to **Settings** → **Devices & Services** → **Helpers** tab
2. Click **+ Create Helper** button
3. Select **Dropdown**
4. Configure the helper:
   - **Name**: Something like "RD1P Scene Index" (you'll select this in the blueprint)
   - **Options**: 1, 2, 3, 4, 5, 6 (set the range to match how many scenes/scripts you configure in the blueprint)
5. Click **Create**

When configuring the blueprint automation, you'll select this helper entity in the "Scene Cycle Helper" field.

For ZHA:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/ajkavanagh/homeassistant-blueprints/blob/main/candeo-blueprint-zha-RD1P-scene-control-double-click.yaml)

## SONOFF SNZB-01P Wireless Button

1 Blueprint for the SONOFF SNZB-01P Wireless Button

### Bedside Light Control

Intelligent bedside light control using a wireless button. Perfect for controlling two individual bedside lights plus a room light group.

**Features:**

- **Single press**: Toggles "my light" on/off
- **Double press**: Smart sync - if lights differ, matches "your light" to "my light"; if both are the same state, toggles both lights together
- **Long press**: Turns off all lights in the "other lights" group/area

This blueprint provides intuitive control for bedside scenarios:

- Control your own light independently without disturbing your partner
- Synchronize both lights with a double press, or toggle them together if they're already matched
- Quick all-off for room lights with a long press

No helper entities required - just select your three light targets (individual lights, groups, or areas) and you're ready to go!

For ZHA:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/ajkavanagh/homeassistant-blueprints/blob/main/sonoff-blueprint-zha-SNZB-01P-bedside-light-control.yaml)
