# Slack Recipe AI Bot using n8n

## Overview

The **Slack Recipe AI Bot** is an automation workflow built using **n8n**, **Slack**, and **OpenAI GPT-4.1 Mini**.

Whenever a user sends the name of a recipe in a Slack channel, the bot automatically generates a concise shopping list containing the required ingredients and approximate quantities, then posts the response back to the same Slack channel.

---

# Features

* Slack message trigger
* Automatic recipe detection
* AI-generated ingredient list
* Approximate ingredient quantities
* Automatic reply in Slack
* Powered by OpenAI GPT-4.1 Mini
* Built completely using n8n (low-code automation)

---

# Tech Stack

* n8n
* Slack API
* OpenAI GPT-4.1 Mini
* JSON Workflow

---

# Workflow Architecture

```text
Slack User
      │
      ▼
Slack Trigger
      │
      ▼
Edit Fields
(Extract Recipe Name)
      │
      ▼
OpenAI Chat Model
(GPT-4.1 Mini)
      │
      ▼
Basic LLM Chain
(Create Ingredient List)
      │
      ▼
Send Message to Slack
```

---

# Workflow Description

## 1. Slack Trigger

* Listens for new Slack messages.
* Starts the workflow whenever a new message is posted.

---

## 2. Edit Fields Node

Extracts the recipe name from the Slack message.

Example:

```
Chicken Biryani
```

Stores it as:

```
recipe = Chicken Biryani
```

---

## 3. OpenAI Chat Model

Uses the **GPT-4.1 Mini** model to process the request.

---

## 4. Basic LLM Chain

Prompt used:

```
List all the products and ingredients needed to make <recipe>.

Return a clear bulleted list with approximate quantities.

Keep it short and practical.

If the recipe name is unclear or empty, reply:

Please provide a valid recipe name.
```

The AI generates a structured ingredient list.

Example output:

```
• Basmati Rice – 500 g
• Chicken – 1 kg
• Onion – 3 large
• Tomato – 2
• Ginger Garlic Paste – 2 tbsp
• Yogurt – 1 cup
• Mint Leaves – 1 bunch
• Coriander Leaves – 1 bunch
• Biryani Masala – 3 tbsp
• Green Chillies – 4
• Oil – 4 tbsp
• Salt – as required
```

---

## 5. Slack Send Message

Posts the AI-generated ingredient list back into the Slack channel automatically.

---

# Prerequisites

Before running this workflow, ensure you have:

* n8n installed (local or cloud)
* Slack Workspace
* Slack App with Bot Token
* Slack OAuth Credentials
* OpenAI API Key
* Internet connection

---

# Required Credentials

## Slack

Configure the following in n8n:

* Slack API Credential
* Bot OAuth Token
* Channel Permissions
* Event Subscription

Required scopes include:

* `chat:write`
* `channels:history`
* `channels:read`
* `groups:history`
* `groups:read`

---

## OpenAI

Configure an OpenAI credential in n8n with:

* API Key
* Model: `gpt-4.1-mini`

---

# Importing the Workflow

1. Open n8n.
2. Click **Import Workflow**.
3. Paste the JSON workflow or upload the JSON file.
4. Configure Slack credentials.
5. Configure OpenAI credentials.
6. Save the workflow.
7. Activate the workflow.

---

# Sample Input

Slack message:

```
Paneer Butter Masala
```

---

# Sample Output

```
Ingredients:

• Paneer – 250 g
• Onion – 2
• Tomato – 3
• Butter – 3 tbsp
• Fresh Cream – 100 ml
• Ginger Garlic Paste – 1 tbsp
• Kashmiri Chilli Powder – 1 tsp
• Garam Masala – 1 tsp
• Cashews – 10
• Oil – 2 tbsp
• Salt – as required
```

---

# Error Handling

If the recipe name is missing or invalid, the bot responds with:

```
Please provide a valid recipe name.
```

---

# Future Enhancements

* Nutrition information
* Estimated cooking time
* Step-by-step cooking instructions
* Serving size selection
* Vegetarian/Non-vegetarian options
* Grocery store recommendations
* Recipe images using AI
* Multi-language support
* Voice input from Slack
* PDF recipe generation
* Amazon or grocery shopping links

---

# Workflow Summary

| Component          | Purpose                                                  |
| ------------------ | -------------------------------------------------------- |
| Slack Trigger      | Starts the workflow when a new Slack message is received |
| Edit Fields        | Extracts the recipe name from the incoming message       |
| OpenAI Chat Model  | Connects to GPT-4.1 Mini                                 |
| Basic LLM Chain    | Generates the ingredient list using AI                   |
| Slack Send Message | Sends the generated response back to Slack               |

---

# Project Structure

```
Slack Recipe AI Bot
│
├── README.md
├── slack_recipe_ai_bot.json
└── screenshots/
    ├── workflow.png
    ├── slack_input.png
    └── slack_output.png
```

---

# Author

**Ponmathi Radhakrishnan**

Built using **n8n**, **Slack**, and **OpenAI GPT-4.1 Mini**.
