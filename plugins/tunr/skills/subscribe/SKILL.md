---
description: Subscribe to tunr channels for real-time screen/audio notifications. Pass channel names as arguments (e.g. `/tunr:subscribe dev` or `/tunr:subscribe dev,research`).
---

# tunr:subscribe

Subscribe to tunr channels to receive real-time screen and audio notifications.

## Usage

- `/tunr:subscribe dev` → subscribe to the `dev` channel
- `/tunr:subscribe dev,research` → subscribe to both `dev` and `research`
- `/tunr:subscribe` (no args) → call `list_channels` to show available channels

## Steps

1. If no arguments provided, call `list_channels()` and show available channels
2. Parse comma-separated channel names from the argument
3. Call `subscribe(channel)` for each channel name
4. Report which channels were subscribed
