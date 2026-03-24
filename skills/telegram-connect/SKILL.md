---
name: telegram-connect
description: Use when starting a conversation where Telegram messaging is needed, or when the user says "connect to telegram", "send to telegram", or wants to communicate via Telegram
---

# Telegram Connect

Auto-connects to the user's Telegram chat for messaging.

## How It Works

1. Attempt to send a connection test message to the saved chat ID
2. If delivery fails, ask the user for their current Telegram chat ID
3. Once connected, proceed with the conversation

## Default Chat ID

```
8777542698
```

## Connection Flow

```dot
digraph connect {
  "Start" [shape=doublecircle];
  "Send test message to 8777542698" [shape=box];
  "Delivered?" [shape=diamond];
  "Connected - proceed" [shape=doublecircle];
  "Ask user for new chat_id" [shape=box];
  "Send test to new chat_id" [shape=box];
  "New delivered?" [shape=diamond];
  "Report failure" [shape=box];

  "Start" -> "Send test message to 8777542698";
  "Send test message to 8777542698" -> "Delivered?";
  "Delivered?" -> "Connected - proceed" [label="yes"];
  "Delivered?" -> "Ask user for new chat_id" [label="no"];
  "Ask user for new chat_id" -> "Send test to new chat_id";
  "Send test to new chat_id" -> "New delivered?";
  "New delivered?" -> "Connected - proceed" [label="yes"];
  "New delivered?" -> "Report failure" [label="no"];
}
```

## Instructions

1. Use `mcp__plugin_telegram_telegram__reply` to send a brief greeting (e.g. "Connected") to chat_id `8777542698`
2. If the tool returns a success response (contains "sent"), the connection is live — proceed with the task
3. If the tool returns an error, tell the user: "Telegram connection failed with the saved chat ID. What's your current chat ID?"
4. Retry with the user-provided chat ID
5. If the second attempt also fails, report the error and ask the user to verify their Telegram bot is running

## After Connecting

Once connected, use the verified chat_id for all subsequent Telegram messages in the conversation. Do not re-test on every message.
