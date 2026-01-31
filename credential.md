# 🔐 Credentials Guide – n8n Dental AI Chatbot (OpenAI + Supabase)

This document explains how to securely configure and manage credentials for the **Dental AI Chatbot Assistant** built with **n8n**, using **OpenAI API** and **Supabase** as the vector database.

---

## ⚠️ Security Guidelines (Read First)

- ❌ Never hardcode API keys inside workflow nodes
- ❌ Never commit credentials to GitHub
- ✅ Always use **n8n Credentials Manager**
- ✅ Use environment variables for self-hosted n8n
- 🔄 Rotate API keys regularly

---

## 🔑 Required Credentials

### 1️⃣ OpenAI API Key (Required)

Used for:
- Generating chatbot responses
- Context-aware answers using RAG

#### How to Add in n8n:
1. Go to **n8n → Credentials**
2. Create new credential → **OpenAI**
3. Paste your **OpenAI API Key**
4. Save and assign it to AI-related nodes

#### Example (Self-Hosted Environment Variable):
```env
OPENAI_API_KEY=your_openai_api_key_here
2️⃣ Supabase Credentials (Required)

Supabase is used for:

Vector storage

Document embeddings

RAG-based knowledge retrieval

Required Supabase Details:

Supabase Project URL

Supabase Service Role Key (or anon key with limited permissions)

Database Table for embeddings

How to Add in n8n:

Use HTTP Request or Supabase credentials (if available):

SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_SERVICE_KEY=your_supabase_service_key


⚠️ Important:
Use the Service Role Key only on secure backends.
Never expose it on the frontend or public workflows.

🧠 RAG Configuration Notes (Supabase)

Ensure pgvector extension is enabled in Supabase

Embeddings table should include:

id

content

embedding

metadata

Similarity search is performed via SQL or RPC functions

🔗 Optional Integration Credentials
3️⃣ Email Credentials (Optional)

Used for:

Appointment confirmations

Follow-up messages

Supported:

Gmail

SMTP

Outlook

Add via:

n8n → Credentials → Email / SMTP

4️⃣ WhatsApp / Messaging APIs (Optional)

Used for:

Patient chat

Appointment reminders

Possible Providers:

WhatsApp Cloud API

Twilio

Third-party WhatsApp APIs

Store tokens using:

n8n → Credentials → HTTP Request

🌐 Webhook Security (n8n)

The chatbot workflow uses Webhook Trigger nodes.

Best Practices:

Keep webhook URLs private

Use secret tokens or headers

Validate request payloads

Restrict public access when possible

🏥 Medical & Data Compliance Notice

This chatbot provides informational support only

No diagnosis or medical advice is generated

Clinics must upload verified and approved dental documents

Patient data should follow local data protection laws

✅ Credential Setup Checklist

 OpenAI API key added in n8n

 Supabase URL & key configured securely

 Vector table and pgvector enabled

 Webhooks secured

 No secrets pushed to GitHub

🎉 Setup Complete

Once these credentials are configured, the Dental AI Chatbot Assistant will function securely using OpenAI + Supabase RAG architecture inside n8n.


