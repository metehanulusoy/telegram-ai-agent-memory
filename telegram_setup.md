# Telegram Bot Setup Guide

## Step 1 — Create Your Bot
1. Open Telegram and search for **@BotFather**
2. Send `/newbot`
3. Choose a name: e.g. `My AI Assistant`
4. Choose a username (must end in `bot`): e.g. `myai_assistant_bot`
5. Copy the **Bot Token** — looks like: `123456789:ABCdef...`

## Step 2 — Google Docs Memory Store
1. Go to [docs.google.com](https://docs.google.com) and create a new document
2. Title it: `AI Agent Memory`
3. Copy the **Document ID** from the URL:
   ```
   https://docs.google.com/document/d/THIS_IS_THE_ID/edit
   ```
4. In n8n, connect your Google account via OAuth2

## Step 3 — n8n Credentials to Add
| Credential Name | Value |
|----------------|-------|
| Telegram Bot Token | From BotFather |
| OpenAI API Key | From platform.openai.com |
| Google OAuth2 | Connect via n8n UI |

## Step 4 — Configure Workflow
1. Import `workflow.json` into n8n
2. Open the **Google Docs - Read Memory** node → paste your Document ID
3. Open the **Google Docs - Write Memory** node → paste your Document ID
4. Open the **Telegram** node → select your Telegram credential
5. Activate the workflow

## Step 5 — Test
Send your bot a message:
```
Hi, my name is [your name] and I like [something]
```
Then start a new session and ask:
```
What do you know about me?
```
The bot should remember!
