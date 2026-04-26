---
description: Unsubscribe from tunr channels. Pass channel names as arguments (e.g. `/tunr:unsubscribe dev`). Use `/tunr:pause` instead to temporarily stop all notifications while remembering subscriptions.
---

# tunr:unsubscribe

Unsubscribe from tunr channels to permanently stop receiving notifications.

## Usage

- `/tunr:unsubscribe dev` → unsubscribe from the `dev` channel
- `/tunr:unsubscribe dev,research` → unsubscribe from both
- `/tunr:unsubscribe` (no args) → call `list_channels` to show current subscriptions

## Steps

1. If no arguments provided, call `list_channels()` and show current subscriptions
2. Parse comma-separated channel names from the argument
3. Call `unsubscribe(channel)` for each channel name
4. Report which channels were unsubscribed
