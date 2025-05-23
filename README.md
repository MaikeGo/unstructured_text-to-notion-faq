# unstructured_text-to-notion-faq

> Built with Python, OpenAI API, and Notion API.

This project uses an LLM (via the OpenAI API) to extract commonly asked questions from unstructured text data and automatically creates a Notion page (via the Notion API) to document them.

The Slack message data used in this example was originally extracted using **Fivetran**.  However, the code is **designed to work with any text-based message data**. You can adapt it easily to any dataset containing text conversations (e.g., customer chats, support tickets, forum posts).

The results created by the automated Notion integration can be viewed here:  
🔗 [View Results on Notion](https://www.notion.so/Auto-generated-FAQ-1afd8cbfdbfd80279fa5c9200855c19b)
(Note: The formatting still has room for improvement!)

---

# Requirements

To run this notebook, you will need:

- A database or file containing the text message data you want to analyze.
- In this example, Slack message data (`team_slack`) is loaded from **Google Drive**.  
  ➔ You will need to replace this part with your own data loading method, depending on where your messages are stored (e.g., local file, database, or cloud storage).
- An **OpenAI API key** for processing and summarizing your text data.
- A **Notion API integration**, which provides you with a Notion "secret" (your Notion API key), for automatically exporting the results to Notion.
- An empty **Notion page** to export your results to.

👉 **Important:**  
- You must have a **billed OpenAI account** (free-tier accounts without billing enabled cannot use the API).
- Running this notebook will **incur API costs** based on the number of tokens processed.  
  Costs depend on the size of your message dataset and the OpenAI model you use.
- You can create and manage your OpenAI API key here: [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys)

- You can create a **Notion integration** here: [https://www.notion.so/my-integrations](https://www.notion.so/my-integrations).  
  After creating the integration, copy your **Internal Integration Token** (the Notion secret/API key), and  
  ➔ **share the target Notion page** with your integration to give it the necessary permissions.

Please make sure you have both your OpenAI and Notion API keys ready before running the code.  
You can set them securely as environment variables (recommended) or insert them directly into the code (not recommended for shared environments).

Example environment variables:
- `OPENAI_API_KEY`
- `NOTION_API_KEY`

---
# **API Cost Estimate**

Running this code on approximately 2,000 text messages using the OpenAI `gpt-4o` model cost me less than **$1** in API usage.

👉 **Important:** Actual costs will vary depending on:
- The total number of tokens processed — which depends heavily on **how many messages** you process and **how long each message is** (more text = more tokens).
- The model used (e.g., GPT-4o is cheaper than GPT-4-turbo).

🛡️ **Tip:**  
To control spending, you can disable "Auto-recharge" in your OpenAI billing settings and/or set a usage limit.  
Always monitor your usage in the [OpenAI usage dashboard](https://platform.openai.com/usage) to avoid unexpected charges.
