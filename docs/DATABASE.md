# DATABASE

Version: 1.0

---

# Tables

* users
* chats
* messages
* settings
* subscriptions
* payments

---

# users

Fields

* id
* telegram_id
* username
* first_name
* last_name
* language
* created_at
* updated_at

---

# chats

Fields

* id
* user_id
* title
* model
* context_enabled
* summary
* created_at
* updated_at

Relations

* users.id -> chats.user_id

---

# messages

Fields

* id
* chat_id
* role
* content
* token_count
* created_at

Relations

* chats.id -> messages.chat_id

---

# settings

Fields

* id
* user_id
* default_model
* language
* conversation_style
* creativity
* context_enabled

Relations

* users.id -> settings.user_id

---

# subscriptions

Fields

* id
* user_id
* plan
* status
* started_at
* expires_at

Relations

* users.id -> subscriptions.user_id

---

# payments

Fields

* id
* user_id
* subscription_id
* telegram_payment_id
* amount
* currency
* status
* created_at

Relations

* users.id -> payments.user_id

* subscriptions.id -> payments.subscription_id

---

# Rules

* UUID primary keys.
* Foreign keys required.
* UTC timestamps.
* created_at for every table.
* updated_at where applicable.
* Cascade delete for messages.
* Soft delete only for chats.
* Never store API keys.
* Never store prompts.
