# PRODUCT SPECIFICATION

Version: 1.0

## MVP

### AI Providers

* OpenAI
* Google Gemini

### Features

* Multiple chats
* Chat history
* Context memory
* Model selection
* Premium subscription
* Telegram Stars payments
* User settings
* Multi-language interface
* Internet search
* Daily free message limit

### Not Included

* Claude
* DeepSeek
* Image generation
* Video generation
* Music generation
* Voice
* Admin panel
* Referral system
* Web app
* Mobile app

---

# USER FLOW

Start

↓

Language Selection

↓

Welcome

↓

Subscription Check

↓

Main Menu

↓

New Chat

↓

Model Selection

↓

Chat

---

# SCREENS

## S01 - Language Selection

Buttons

* 🇺🇸 English
* 🇷🇺 Русский
* 🇺🇦 Українська
* 🇨🇿 Čeština

Action

* Save language
* Open Welcome

---

## S02 - Welcome

Show introduction.

Button

* Continue

Action

* Open Subscription Check

---

## S03 - Subscription Check

If subscribed:

* Open Main Menu

If not subscribed:

Buttons

* Join Channel
* Check Subscription
* Premium

Action

* Verify subscription
* Open Main Menu after successful verification

---

## S04 - Main Menu

Buttons

* 💬 New Chat
* 📂 My Chats
* 🤖 Models
* ⭐ Premium
* ⚙ Settings
* ❓ Help

Actions

New Chat → Open new chat

My Chats → Open history

Models → Open model selection

Premium → Open premium

Settings → Open settings

Help → Open help
---

## S05 - New Chat

Action

* Create new chat
* Open Model Selection

---

## S06 - Model Selection

Available Models

### Free

* GPT
* Gemini

### Premium

* Other models (future)

If user selects a Premium model without subscription:

* Open Premium screen

After selecting a model:

* Create chat
* Open Chat

---

## S07 - Chat

User can:

* Send text
* Send voice message
* Reply to messages
* Copy messages
* Regenerate last answer
* Stop generation
* Delete messages

Every chat stores:

* Selected model
* Message history
* Context
* Creation date
* Last update date

If daily free limit is reached:

* Block new requests
* Show Premium screen

---

## S08 - Chat History

Display all chats ordered by last activity.

For every chat show:

* Title
* Last message
* Last update time

Actions

* Open
* Rename
* Delete
* Archive

---

## S09 - Premium

Display subscription plans.

Buttons

* Monthly
* Quarterly
* Yearly

Payment

* Telegram Stars

After successful payment:

* Activate Premium
* Remove daily limit
* Unlock Premium features
---

## S10 - Settings

Settings

* Default AI model
* Interface language
* Conversation style
* Creativity level
* Context memory (On / Off)

Coming Soon

* Voice replies
* Voice selection

---

## S11 - Help

Display

* Bot features
* Available commands
* Premium information
* Support contact

---

## S12 - Internet Search

User sends:

/i Your request

Action

* Search the Internet
* Generate answer using search results

---

## S13 - Coming Soon

Display

This feature is not available yet.

Button

* Back

---

# LIMITS

Free

* 40 messages per day
* GPT
* Gemini

Premium

* Unlimited messages
* Premium models
* Future features

---

# GENERAL RULES

* Each chat has its own message history.
* Each chat remembers its own context.
* Context is not shared between chats.
* Deleting a chat permanently removes its history.
* User settings apply to all chats.
* Premium is linked to the Telegram account.
* All texts must support localization.
* All limits must be configurable.
* Channel links must be configurable.
* Payment provider: Telegram Stars.

---

# OUT OF SCOPE

Do not implement:

* Image generation
* Video generation
* Music generation
* Admin panel
* Referral system
* Mobile application
* Web application
