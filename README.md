# AI-Powered Customer Support Smart Agent

An end-to-end automated pipeline built in *n8n* that monitors incoming customer emails, analyzes their sentiment using OpenAI, logs data into Google Sheets, and intelligently routes the sentiment-specific data to an Advanced AI Agent or instant messaging channels (WhatsApp/Gmail).

---

## 💼 Business Case: Problem & Solution

### The Problem
Modern companies and customer support teams face an overwhelming volume of daily emails. Manually sorting through these queries, identifying frustrated or happy customers, logging complaints into internal databases, and responding timely leads to:
* *High Response Time:* Delayed support causes low customer satisfaction.
* *Human Error:* Crucial customer leads or urgent issues get lost in messy inboxes.
* *Scalability Issues:* Hiring more support staff to handle peak loads becomes highly expensive.
* *Lack of Insights:* No automatic database or analytics to track customer emotions and feedback trendlines over time.

### The Solution (This Workflow)
This workflow helps businesses automate customer communication and reduce manual support workload. By deploying an autonomous AI pipeline:
1. *Instant Ingestion & Logging:* Every customer interaction is instantly backed up in centralized sheets for data-driven insights.
2. *Real-time Emotion Detection:* The system automatically understands if a customer is complaining, asking for a refund, or giving a compliment using advanced LLMs.
3. *Smart AI Agent Execution:* Instead of rigid canned responses, an AI Agent with memory understands the contextual history of the user and crafts dynamic, natural replies.
4. *Instant Omni-channel Alerts:* Escalates critical paths immediately via WhatsApp or Gmail, ensuring zero-latency communication.

---

## 🛠️ Tech Stack & Nodes Used

* *Automation Platform:* n8n
* *AI Models:* OpenAI Chat Model (gpt-4o or preferred model)
* *Databases/Sheets:* Google Sheets
* *Communication Tools:* Gmail, WhatsApp (Send Message node)
* *Core n8n Nodes:* Filter, Merge, AI Agent, Simple Memory

---

## 📈 Workflow Architecture & End-to-End Explanation

Here is how the data flows through the pipeline from start to finish:

### 1. Ingestion & Initial Logging
* *Gmail Trigger:* The workflow kicks off the moment a new customer email lands in the inbox.
* *Append row in sheet:* The raw details of the email (Sender, Subject, Body, Date) are immediately logged into a Google Sheet for backup and audit trails.

### 2. AI Sentiment Analysis
* *Sentiment Analysis Node:* The email body is passed to this node, which is powered by the *OpenAI Chat Model*. 
* *Merge Node:* The output branches (Positive/Negative paths) are unified into a structured format containing the assigned sentiment score/tag.

### 3. Post-Analysis Logging
* *Append row in sheet1:* The workflow logs the computed sentiment alongside the original customer details back into a secondary Google Sheet for business intelligence.

### 4. Smart Filtering & Advanced Routing
The workflow splits into two distinct paths using *Filter* nodes based on the sentiment outcome:

* *Path A (Advanced AI Handling - Top Branch):*
  * *Filter:* Checks for specific criteria/sentiment requiring deep contextual resolution.
  * *AI Agent:* A conversational agent that takes the email context. It is backed by *Simple Memory* to remember context and has direct access to the *Send a message in Gmail* tool to draft and send highly personalized, human-like responses.
  
* *Path B (Instant Alert/Response - Bottom Branch):*
  * *Filter1:* Targets paths that require immediate notifications or alternative routing.
  * *Send message (WhatsApp):* Sends an instant automated notification or text via WhatsApp to ensure rapid response.

---

## 📸 Workflow Screenshots

Below are the visual representations of the n8n canvas and setup:

### Full Workflow Canvas
![n8n Workflow Full Canvas](YOUR_IMAGE_FOLDER_OR_URL/1000055934.jpg)

> *Note for User:* If you have more screenshots of specific node configurations (like the AI Agent setup or Google Sheets), you can add them below using the same format:
> ![Description](YOUR_IMAGE_FOLDER_OR_URL/YOUR_FILE_NAME.jpg)

---

## ⚙️ Setup & Installation

1. *Prerequisites:*
   * Install and set up an *n8n* instance (Self-hosted or Cloud).
   * An *OpenAI API Key*.
   * Credentials for *Google Sheets, **Gmail, and your **WhatsApp Business API/Provider*.

2. *Importing the Workflow:*
   * Copy the JSON file of this workflow from this repository.
   * Open your n8n dashboard, click on *New Workflow*.
   * Click on the top-right menu and select *Import from File* (or press Ctrl + I and paste the JSON).

3. *Credential Configuration:*
   * Link your Google account to the Gmail and Google Sheets nodes.
   * Add your OpenAI API key to the OpenAI Chat Model nodes.
   * Configure your WhatsApp node API credentials.

4. *Test & Deploy:*
   * Click *Execute workflow* to test it with a sample email.
   * Once working perfectly, toggle the *Active* switch in the top right corner.

---

## 📜 License

This project is open-source and available for learning and portfolio purposes.

---

## 👨‍💻 Author

  **Sharjeel.ai**
  
  AI Automation Specialist
  Building intelligent AI
systems and automation workflows.
