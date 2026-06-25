# ARCHITECTURE

Version: 1.0

---

# Architecture

Presentation

↓

Application

↓

Domain

↓

Infrastructure

↓

Database

Dependencies are allowed only from top to bottom.

---

# Project Structure

```text
src/

    bot/
    config/
    core/
    database/
    features/
    providers/
    services/
    shared/
```

---

# Features

Each feature is isolated.

Example

```text
features/

    chats/
    settings/
    premium/
    payments/
    users/
```

Each feature contains:

```text
handlers.py
service.py
repository.py
schemas.py
keyboards.py
texts.py
```

---

# Rules

* Business logic only in services.
* Database access only in repositories.
* Handlers never access the database.
* Handlers never call AI providers directly.
* Providers never access Telegram.
* Services never depend on Telegram objects.

---

# AI Providers

Every provider implements the same interface.

Required methods

```python
generate()
stream()
count_tokens()
estimate_cost()
```

Supported providers

* OpenAI
* Gemini

Future providers

* Claude
* DeepSeek
* Perplexity

---

# Prompt Builder

Responsibilities

* Build system prompt.
* Add conversation history.
* Add context.
* Add user message.

Services never build prompts manually.

---

# Context

Each chat has its own context.

Context is never shared between chats.

Context can be disabled in Settings.

Long conversations must be summarized automatically.

---

# Configuration

Never hardcode:

* API keys
* Prices
* Limits
* Model names
* Channel links
* Text messages

Everything must come from configuration.

---

# Logging

Use structured logging.

Never use print().

Never log:

* API keys
* Tokens
* Secrets

---

# Localization

All user-visible text must be stored outside the source code.

Python files must not contain interface text.
---

# Source Structure

```text
src/

├── bot/
├── config/
├── core/
├── database/
├── features/
├── providers/
├── services/
└── shared/
```

---

# Folder Responsibilities

## bot

Telegram initialization.

Contains:

* bot
* dispatcher
* routers
* middlewares

---

## config

Application configuration.

Contains:

* environment
* settings
* constants

---

## core

Application startup.

Contains:

* dependency injection
* application lifecycle
* initialization

---

## database

Database layer.

Contains:

* models
* migrations
* session
* repositories

---

## features

Business modules.

Each feature is independent.

Example

```text
features/

    chats/
    users/
    settings/
    premium/
    payments/
```

---

## providers

External services.

Example

```text
OpenAI

Gemini

Telegram Stars
```

---

## services

Shared business services.

Example

```text
AIService

ContextService

PromptService

LocalizationService
```

---

## shared

Reusable components.

Example

```text
exceptions/

helpers/

validators/

types/
```

---

# Feature Structure

Every feature must follow the same structure.

```text
feature/

    handlers.py

    service.py

    repository.py

    schemas.py

    keyboards.py

    texts.py
```

Additional files are allowed only when required.

---

# Dependency Rules

Allowed

Handler

↓

Service

↓

Repository

↓

Database

Forbidden

Repository → Handler

Service → Telegram

Provider → Telegram

Handler → Database

Handler → AI Provider
# Services

## UserService

Responsibilities

* Create user
* Update user
* Get user
* Manage user settings

---

## ChatService

Responsibilities

* Create chat
* Delete chat
* Rename chat
* Archive chat
* Get chat history

---

## MessageService

Responsibilities

* Save messages
* Load messages
* Delete messages

---

## AIService

Responsibilities

* Generate response
* Stream response
* Select provider
* Count tokens

---

## ContextService

Responsibilities

* Load context
* Save context
* Summarize long conversations
* Clear context

---

## PromptService

Responsibilities

* Build system prompt
* Build user prompt
* Build final prompt

---

## ModelService

Responsibilities

* Get available models
* Check model access
* Select active model

---

## PremiumService

Responsibilities

* Check subscription
* Activate premium
* Deactivate premium
* Check limits

---

## PaymentService

Responsibilities

* Create invoice
* Verify payment
* Activate subscription

---

## SettingsService

Responsibilities

* Get settings
* Update settings
* Reset settings

---

## LocalizationService

Responsibilities

* Get translated text
* Change language

---

# Service Rules

* Services contain business logic.
* Services communicate through public methods only.
* Services never access Telegram directly.
* Services never contain SQL.
* Services may call other services when required.
# Repositories

## UserRepository

* Create user
* Get user
* Update user
* Delete user

---

## ChatRepository

* Create chat
* Get chat
* Get user chats
* Update chat
* Delete chat

---

## MessageRepository

* Save message
* Get messages
* Delete message
* Delete chat messages

---

## SettingsRepository

* Get settings
* Update settings

---

## PremiumRepository

* Get subscription
* Activate subscription
* Deactivate subscription

---

## PaymentRepository

* Create payment
* Get payment
* Update payment

---

# Repository Rules

* Repositories only work with the database.
* No business logic.
* No Telegram API.
* No AI providers.
* No prompt generation.
* Return data only.

---

# Providers

Current

* OpenAI
* Gemini

Future

* Claude
* DeepSeek
* Perplexity

Every provider implements the same interface.

```python
generate()
stream()
count_tokens()
estimate_cost()
```

Provider Rules

* No Telegram API.
* No database access.
* No business logic.
* Only provider-specific implementation.

---

# Prompt Builder

Builds the final prompt.

Input

* System prompt
* Chat context
* Previous messages
* Current message

Output

* Final prompt

Rules

* Services never build prompts manually.
* Prompt Builder is the only place where prompts are assembled.

---

# Context

Each chat has its own context.

Context includes:

* Previous messages
* Conversation summary
* Selected model

Rules

* Chats never share context.
* Context can be disabled.
* Long chats must be summarized automatically.
# Configuration

Configuration must contain:

* API keys
* Database settings
* Redis settings
* Telegram settings
* AI models
* Limits
* Prices
* Channel links

Rules

* No hardcoded values.
* Environment variables for secrets.
* Constants only for immutable values.

---

# Logging

Use structured logging.

Log

* Requests
* Errors
* Payments
* AI requests

Never log

* API keys
* Passwords
* Tokens
* User secrets

Never use

```python
print()
```

---

# Localization

All interface text must be stored outside the source code.

Supported languages

* English
* Russian
* Ukrainian
* Czech

Rules

* No hardcoded interface text.
* Every message must have a translation key.

---

# Error Handling

Errors must be handled in one place.

User errors

* Invalid input
* Daily limit reached
* Premium required

System errors

* Database unavailable
* AI provider unavailable
* Telegram API error

Rules

* Never expose internal errors.
* Always log exceptions.
* Always return a user-friendly message.

---

# General Architecture Rules

* Feature-first architecture.
* One responsibility per class.
* One responsibility per function.
* Business logic only in Services.
* Database access only in Repositories.
* AI access only through Providers.
* No duplicate logic.
* No circular dependencies.
* No hardcoded values.
* No global state.
* No SQL outside Repositories.
* No Telegram API outside Handlers.
* All code must be asynchronous.

---

# Naming Convention

Folders

snake_case

Files

snake_case

Functions

snake_case

Classes

PascalCase

Constants

UPPER_CASE

Variables

snake_case

---

# Project Principles

* Keep modules independent.
* Prefer composition over duplication.
* Write reusable code.
* Keep functions small.
* Keep files focused.
* Follow existing architecture.
* Do not implement undocumented features.
