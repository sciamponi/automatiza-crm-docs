<div align="center">

![Automatiza logo](images/crm/automatiza-logo-fundo-escuro-500px.png) 

# 🤖 Automatiza — WhatsApp CRM

**The multi-tenant customer service platform built on WhatsApp.**

Real-time ticket management, no-code automation, AI assistants, campaigns, and subscription billing — all inside a single, real-time team inbox.


[🇧🇷 Português](README.pt-BR.md)
</div>




---
## 📌 Tech stack

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![Material UI](https://img.shields.io/badge/Material%20UI-0081CB?style=flat&logo=mui&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Socket.io](https://img.shields.io/badge/Socket.io-010101?style=flat&logo=socket.io&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=flat&logo=sequelize&logoColor=white)
![Baileys](https://img.shields.io/badge/Baileys-25D366?style=flat&logo=whatsapp&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat&logo=googlegemini&logoColor=white)

---

## 🎯 About

Automatiza is a **multi-tenant WhatsApp CRM** built to organize customer service and sales conversations into a single, real-time team inbox.

**Problem it solves:** scattered WhatsApp conversations, no routing or team ownership, no visibility over service performance, and no automation.

**Who it is for:** support and sales teams, contact centers, and businesses that rely on WhatsApp as their main communication channel. Built as a SaaS — one deployment, multiple tenant companies, each with its own plans, users, and permissions.

**Goal:** turn WhatsApp into a manageable, automated, and measurable service channel.

---

## ✨ Features

- 📊 **Dashboard** — service metrics and KPI overview
- 💬 **Tickets & real-time chat** — conversations with live updates via Socket.io
- 🗂️ **Kanban** — visual ticket pipeline
- 👥 **Contacts, lists & auto-import** — contact management with custom fields, tags, and list import
- 📱 **Multiple WhatsApp connections** — QR-code pairing via Baileys
- 🧩 **FlowBuilder** — no-code flow automation
- 🤖 **AI tools** — chatbots, custom prompts (OpenAI / Gemini), and audio transcription
- 📣 **Campaigns & official broadcast** — scheduled campaigns and WABA official broadcast
- 🗓️ **Schedules & birthdays** — recurring messages and birthday automation
- 💳 **Billing & subscriptions** — plans, invoices, and payment providers (Mercado Pago, Asaas, IXC, Atlaz, Hubsoft, SGP)
- 🔔 **Push notifications** — web-push to connected browsers
- 🔐 **Authentication & RBAC** — JWT auth, multi-tenant companies, users, and permissions
- 🧾 **Reports & statistics** — performance and service reports
- ⚙️ **Queues & routing** — service queues and ticket assignment
- 💬 **Quick messages & tags** — shortcuts and content organization
- 🌐 **REST API & webhooks** — programmatic access (MessagesAPI)
- 🗺️ **Internationalization** — PT / EN / ES / TR
---

## 📸 Meet the Automatiza CRM

![Automatiza CRM overview](images/crm/mockup01.webp)

---

## ✨ What is Automatiza?

Automatiza is a **SaaS CRM powered by WhatsApp** that turns scattered customer conversations into a **single, real-time service inbox**. It is a multi-tenant platform: one deployment, many companies, each with its own plans, users and permissions.

- **Team inbox** — every WhatsApp conversation routed and owned in real time
- **No-code automation** — build flows that answer and qualify automatically
- **AI assistants** — OpenAI / Gemini chatbots and custom prompts
- **SaaS model** — plans, invoices and payment providers built-in

---

## 💬 Customer service & multi-agent

Handle multiple agents and queues in one place, with live updates, assignment and history.

![Customer service and multi-agent](images/crm/1.webp)

---

## 🗂️ CRM & Kanban

Organize contacts and move tickets through a visual pipeline.

![CRM and Kanban](images/crm/2.webp)

---

## 🧩 Flowbuilder + AI

Automate conversations with a no-code flow builder and AI-powered responses.

![FlowBuilder and AI](images/crm/3.webp)

---

## 🗓️ Scheduling

Schedule messages, recurring sends and birthday automations.

![Scheduling](images/crm/4.webp)

---

## 📊 Dashboard

Monitor service metrics and team performance in real time.

![Dashboard](images/crm/5.webp)

---

---

## 🏗️ Architecture

```text
React Frontend
      │  REST API + WebSocket
      ▼
Express Backend (TypeScript)
      │
      ├── Services & Controllers
      ├── Queues (Bull + Redis)
      └────── PostgreSQL (Sequelize)
      │
      └── Integrations: Baileys (WhatsApp) · OpenAI · Gemini · Payment providers · Webhooks
```

---

## 📁 Project structure

```text
automasol/
├── backend/                  # API, business logic, integrations
│   ├── src/controllers/      # HTTP handlers
│   ├── src/services/         # Business services & external integrations
│   ├── src/models/           # Sequelize models
│   ├── src/database/         # Migrations & seeders
│   ├── src/queues/           # Job queues (Bull/Redis)
│   ├── src/routes/           # API routes
│   └── src/jobs/             # Scheduled jobs (birthdays, send, etc.)
├── frontend/                 # React admin (dashboard, tickets, flows...)
│   └── src/pages/            # Screen modules
├── instalador.sh             # Instance installer script
├── ecosystem.config.cjs      # PM2 process configuration
└── README.md
```

---

## 🚀 Getting started

Requirements:

- **Node.js** (with `npm`)
- **PostgreSQL**
- **Redis**

```bash
# 1. Clone and install dependencies
git clone <repo-url>
cd automasol

cd backend && npm install
cd ../frontend && npm install

# 2. Configure environment
# Create backend/.env with your connection and app settings:
# BACKEND_URL, FRONTEND_URL, PORT, DB_*, JWT_SECRET, REDIS_URI, ...

# 3. Create the database and run migrations (backend)
npm run db:migrate

# 4. Build and start
cd ../backend && npm run build && npm start

# 5. Run the frontend
cd ../frontend && npm start
```

> A ready-to-use instance script is available at `instalador.sh`, and a PM2 configuration at `ecosystem.config.cjs` for production process management.

---

## 🧪 Testing

Backend test infrastructure is configured with **Jest** + **supertest**:

```bash
cd backend && npm test
```

---

## 📄 License

Not specified. All rights reserved by the author.

---
## 🌐 Try it

Explore the CRM:

- 🖥️ Product page: [crm.automatizasolucao.com.br](https://crm.automatizasolucao.com.br/)
- 📝 Sign up for a test account: [app.automatizasolucao.com.br/signup](https://app.automatizasolucao.com.br/signup)

> Screenshots shown use demo data, for presentation purposes only.

---

[🇧🇷 Português](README.pt-BR.md)
