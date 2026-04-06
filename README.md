# Bulk Slack Message Deleter

[Try it out: ](https://slack-purger.rylander.io/)

<img width="1003" height="842" alt="image" src="https://github.com/user-attachments/assets/0e95ef39-1717-40a1-8a2c-a8a67b9b1080" />

Bulk delete your messages on Slack. Using Slack's public Web API, no workspace app install needed.

## What the Tool Does
The app allows you to:

- Delete all your messages in a specific channel
- Delete only messages that contain a specific keyword
- Control how many messages are fetched per batch
- Avoid Slack rate limits by adding small delays between delete requests
- It focuses on one thing: removing your own messages safely and efficiently.

## How It Works
When you run the tool:

1 You enter your Slack workspace details and session credentials.

2 The app requests message history for the selected channel.

3 It filters messages:
 - Only messages sent by you

 - Optionally filtered by a keyword (case-insensitive)

4 It sends delete requests to Slack one by one.

5 After finishing, it shows how many messages were deleted.

Because Slack’s API blocks direct browser requests from other origins (CORS restrictions), the app uses a small server-side API route to forward requests to Slack. This server does not store your data. It simply passes the request along and discards everything after the deletion process completes.

## Getting Started
```
brew install nvm
nvm install node

cd bulk-slack-message-deleter

npm install

code .

npm run dev

localhost:3000

```

## Getting the required configuration
**Your User ID:**

1. Click your profile in Slack
2. Select "View full profile"
3. Click "More" → "Copy member ID"

**Token and Cookie:**

1. Open Slack in your browser
2. Open Developer Tools (F12)
3. Go to Network tab
4. Look for any request to Slack's API
5. Copy the `xoxc-` **token** from the request body
6. Copy the entire **Cookie header** from request headers

**For regular channels:**

1. Right-click the channel name
2. Select "Copy link"
3. The ID is the last part: `C1234567890`

**For DMs:**

1. Open the DM
2. Check the URL - the ID starts with `D`

## Thanks

This project was inspired by [slack-message-deleter](https://github.com/huytd/slack-message-deleter) by [huytd](https://github.com/huytd). Thank you for the inspiration.
