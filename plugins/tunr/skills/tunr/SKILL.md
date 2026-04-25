---
description: Skill for searching and referencing user's screen and audio context. Auto-invokes when the user references something they were looking at ("that page I had open", "what was on screen", "what I was browsing") or listening to ("what they said in the video", "in the meeting"), or when screen/audio context would help understand their request. Pass a channel name as argument to subscribe to that channel.
---

# tunr — Screen & Audio Context

Search and reference what the user is seeing on screen or hearing via audio. Uses tunr's MCP tools to query screen history and audio transcriptions recorded by the tunr start daemon.

## Channel subscription via arguments

When `/tunr:tunr` is called with arguments, perform channel operations:

- `/tunr:tunr dev` → call `subscribe(channel: "dev")`
- `/tunr:tunr dev,research` → call `subscribe` for both `dev` and `research`
- `/tunr:tunr -dev` → call `unsubscribe(channel: "dev")`
- `/tunr:tunr` (no args) → normal screen/audio context search

When arguments are provided, only perform channel operations — do not search.

## When to use

- User references something on screen: "that page", "what I was looking at", "the browser tab"
- User references audio content: "what they said", "in the video", "during the meeting"
- Understanding the user's intent requires knowing what they're currently viewing
- User refers to something without providing a specific URL or file path

## Steps

1. Start with `recent_screens` to check recent screen states (default 10 minutes)
2. Use the `app` parameter to filter by app (e.g. `app: "Chrome"`)
3. Use `search_screen_history` for keyword-based search
4. For audio queries, use `recent_audio` for recent transcriptions
5. Use `search_audio` for keyword search in audio transcriptions
6. Use `subscribe(channel)` to receive real-time channel notifications
7. Use the retrieved context to understand the user's intent and respond

## MCP Tools

- `list_channels()` — list available channels and subscription status
- `subscribe(channel)` — subscribe to a channel for real-time notifications
- `unsubscribe(channel)` — unsubscribe from a channel
- `search_screen_history(query, channel?, app?, minutes?, limit?)` — search screen text by keyword, optionally filter by channel
- `recent_screens(channel?, app?, minutes?, limit?)` — recent screen states, optionally filter by channel
- `recent_audio(channel?, minutes?, limit?)` — recent audio transcriptions
- `search_audio(query, channel?, minutes?, limit?)` — search audio transcriptions by keyword

## Channel events

- `user_send` — user pressed shortcut to share current screen
- `screen` — screen content changes (subscribed channels only)
- `audio` — audio transcription (subscribed channels with audio enabled)

## Notes

- If the tunr start daemon is not running, tools return "No screen/audio history available". Suggest the user run `tunr start`.
- Channels are created and managed in the tunr TUI (`tunr start`). Window-to-channel assignment is also done in the TUI.
- Audio capture requires BlackHole and a multi-output audio device.
