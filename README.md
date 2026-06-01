# IKEA BILRESA Dual Button (Matter) - Home Assistant Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fandre-sam%2Fikea-bilresa-matter-blueprint%2Fmain%2Fbilresa_dual_button_matter.yaml)

Home Assistant automation blueprint for the IKEA BILRESA dual-button remote in Matter mode.

This blueprint is event-entity based (recommended for Matter remotes) and supports:

- Single press (button 1 and button 2)
- Double press (button 1 and button 2)
- Long press start (button 1 and button 2)
- Long press release (button 1 and button 2)
- Optional repeat-while-held loop with interval and safety cap

## Why event entities

Matter button devices in Home Assistant are exposed as `event.*` entities whose state changes to a timestamp on each press. The specific button interaction is available in the entity attribute `event_type`.

This blueprint listens for state changes on two Matter event entities (one per button) and routes actions by `event_type`.

## Requirements

- Home Assistant with Matter integration.
- Two Matter event entities from your BILRESA dual-button device (one per button).

Typical selector path in Home Assistant:

- Settings -> Devices & Services -> Matter -> your BILRESA device -> Events

## Install

Import this blueprint using Home Assistant blueprint import and the raw URL:

```text
https://raw.githubusercontent.com/andre-sam/ikea-bilresa-matter-blueprint/main/bilresa_dual_button_matter.yaml
```

## Notes on event names

Different firmware/controller combinations can vary slightly in naming. Defaults are set for common Matter button behavior:

- single: `short_release`
- double: `multi_press_complete` with count `2`
- hold start: `long_press`
- hold release: `long_release`

If your remote uses different values, run a quick debug automation and inspect `event_type` and attributes for each gesture.

## License

MIT
