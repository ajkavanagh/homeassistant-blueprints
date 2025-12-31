# Home Assistant Blueprints

These Blueprints are automations that I have found useful.  YMMV!  Feel free to
copy, update, etc, as needed.  Also feel free to open Issues or PRs for
new/updated Blueprints.

NOTE: these are ZHA *only* at the moment, as that's all I use.  They could be updated to use z2m.

## Devices

1. Candeo [RD1-Pro](#rd1-pro-c-zb-rd1p-decoupled-dimming-switch)

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

#### ZHA

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/ajkavanagh/homeassistant-blueprints/blob/main/candeo-blueprint-zha-RD1P-toggle-light-and-dimming.yaml)

### Activate Scenes from your RD1-Pro - not available yet

Toggle lights, cycle scenes or scripts on double press, and adjust brightness with the knob.  Select up to six scenes or scripts  in the blueprint. A simple numeric helper chooses which slot runs next.

This is modified from the original [Candeo](https://github.com/candeosmart/homeassistant-blueprints/blob/main/README.md#activate-your-scenes-or-scripts-from-your-wall-switch) one, in that *only* the double press event is used to switch between scenes.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/ajkavanagh/homeassistant-blueprints/blob/main/candeo-blueprint-zha-RD1P-scene-control-double-click.yaml)
