#  AI-Powered Digital Twin System

**FastAPI • AWS Bedrock • S3 Memory • CloudFront • Terraform**

---

##  Overview

**MY Twin Chatbot** is a production-grade **AI Digital Twin System** designed to simulate **personalized, memory-enhanced conversations** using **AWS Bedrock foundation models**.  
The system creates an AI-powered digital replica of a person by learning from their personal data (LinkedIn profile, summaries, facts, and writing style) and responding consistently in their **tone, style, and personality**.

It is built with a **serverless, scalable cloud architecture**, fully provisioned using **Terraform**, and supports **persistent memory across sessions**.

---

## ✨ Key Capabilities

- 🧑‍💻 **Personalized AI Digital Twin**
- 🧠 **Memory-aware, multi-turn conversations**
- ☁️ **AWS Bedrock LLM integration (Converse API)**
- 💾 **Persistent memory (Local or S3-backed)**
- ⚡ **High-performance FastAPI backend**
- 🌍 **Globally distributed frontend via CloudFront**
- 🏗️ **100% Infrastructure-as-Code (Terraform)**

---

## 🏗️ Tech Stack

### 🔙 Backend
- **FastAPI (Python)**
- UUID-based session management
- Replayable multi-turn conversation history
- AWS Lambda (serverless execution)

### 🧠 AI Models (AWS Bedrock)
Supports multiple foundation models:
- `amazon.nova-lite-v1` *(Default)*
- `amazon.nova-micro-v1`
- `amazon.nova-pro-v1`

### 💾 Memory Layer
Persistent conversation memory stored in:
- 🗂️ Local filesystem (`/memory`) – Development
- ☁️ AWS S3 – Production

### 🖥️ Frontend
- **Next.js static web application**
- Hosted on **S3**
- Delivered globally via **CloudFront CDN**

### ☁️ Infrastructure (Terraform)
- S3 (Frontend hosting)
- CloudFront (CDN)
- S3 (Memory storage bucket)
- API Gateway (HTTP API)
- AWS Lambda (FastAPI backend)
- IAM Roles & Permissions
- Optional: Custom Domain + SSL (ACM)

---

## 🧬 System Architecture

```text
ai-powered-digital-twin-system/
├── backend/
│   ├── __pycache__/
│   ├── data/
│   │   ├── facts.json          # Structured personal facts
│   │   ├── linkedin.pdf        # Professional profile data
│   │   ├── style.txt           # Writing tone & style
│   │   └── summary.txt         # High-level personal summary
│   │
│   ├── lambda-package/         # Lambda build artifacts
│   ├── Twin/                   # Core Digital Twin logic
│   ├── .env                    # Environment variables
│   ├── context.py              # Prompt & context builder
│   ├── deploy.py               # Lambda deployment script
│   ├── lambda-handler.py       # AWS Lambda entry point
│   ├── lambda-deployment.zip   # Packaged Lambda artifact
│   ├── me.txt                  # Developer notes / metadata
│   ├── requirements.txt        # Python dependencies
│   ├── resources.py            # Bedrock & AWS resources
│   └── server.py               # FastAPI application
│
├── frontend/
│   ├── .next/                  # Next.js build output
│   ├── app/
│   │   ├── favicon.ico
│   │   ├── globals.css
│   │   ├── layout.tsx
│   │   └── page.tsx
│   │
│   ├── components/
│   │   └── twin.tsx            # Chat UI component
│   │
│   ├── node_modules/
│   ├── out/                    # Static export for S3 hosting
│   ├── public/
│   ├── .env.production         # Production environment vars
│   ├── eslint.config.mjs
│   ├── next-env.d.ts
│   ├── next.config.ts
│   ├── package.json
│   ├── package-lock.json
│   ├── postcss.config.mjs
│   ├── README.md
│   └── tsconfig.json
│
├── memory/                     # Persistent conversation memory
├── scripts/                    # Utility & automation scripts
│
├── terraform/
│   ├── .terraform/
│   ├── .terraform.lock.hcl
│   ├── main.tf                 # Core infrastructure
│   ├── variables.tf            # Input variables
│   ├── outputs.tf              # Terraform outputs
│   ├── terraform.tfvars        # Environment-specific values
│   └── versions.tf             # Provider versions
│
├── LICENSE
└── README.md
```

---

## 🤖 AI Digital Twin Design

The system builds a **digital persona** using structured and unstructured personal data:

| File | Purpose |
|-----|--------|
| `linkedin.pdf` | Professional background & experience |
| `summary.txt` | High-level personality and bio |
| `style.txt` | Writing tone and communication style |
| `facts.json` | Personal facts and preferences |

This data is injected into prompts and memory context to ensure:
- Consistent tone
- Personality preservation
- Context-aware responses

---

## 🚀 Core Features

### 🔹 AI Digital Twin
- Persona-driven responses
- Style and tone imitation
- Knowledge grounded in personal data

### 🔹 Bedrock Conversational Intelligence
- Multi-turn reasoning
- Model switching via Converse API
- Low-latency inference

### 🔹 Persistent Memory
- Cross-session memory retention
- Pluggable storage (Local / S3)
- Replayable conversation history

### 🔹 Scalable Serverless Backend
- AWS Lambda + API Gateway
- Automatic scaling
- Fault-tolerant Bedrock integration

### 🔹 Full IaC Deployment
- One-command infrastructure provisioning
- Version-controlled cloud resources
- Zero manual AWS console setup

---

## 📂 Project Structure

```text
text
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── api/
│   │   ├── services/
│   │   └── memory/
│   └── requirements.txt
│
├── frontend/
│   ├── app/
│   ├── components/
│   └── next.config.js
│
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── memory/
│   └── sessions/
│
├── README.md
└── .env.example
```

---
## Architecture Recap

Your updated architecture:

```
User Browser
    ↓ HTTPS
CloudFront (CDN)
    ↓ 
S3 Static Website (Frontend)
    ↓ HTTPS API Calls
API Gateway
    ↓
Lambda Function (Backend)
    ↓
    ├── AWS Bedrock (AI responses)  ← NEW!
    └── S3 Memory Bucket (persistence)
```

All services now stay within AWS, providing:
- Lower latency (no external API calls)
- Better security (IAM integration)
- Potential cost savings
- Unified billing and monitoring

## ⚙️ Deployment

### 1️⃣ Prerequisites
- AWS Account
- Terraform ≥ 1.5
- Python 3.10+
- Node.js 18+
- AWS CLI configured

### 2️⃣ Infrastructure Provisioning

```bash
cd terraform
terraform init
terraform apply
```

### 3️⃣ Backend (Local Development)

```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload
```

### 4️⃣ Frontend Build

```bash
cd frontend
npm install
npm run build
```

---

## 🔐 Security & IAM
- Least-privilege IAM roles
- Scoped Bedrock permissions
- Secure S3 bucket policies
- Optional HTTPS with ACM + Custom Domain

---

## 🎯 Use Cases

- Personal AI avatar
- Founder / Developer digital clone
- AI portfolio showcase
- AI-powered personal assistant
- Knowledge-preserving chatbot

---

## Architecture Summary

Your Terraform manages:

```
Terraform Configuration
    ├── S3 Buckets (Frontend + Memory)
    ├── Lambda Function with IAM Role
    ├── API Gateway with Routes
    ├── CloudFront Distribution
    └── Optional: Route 53 + ACM Certificate

Managed via Workspaces:
    ├── dev/   (Development environment)
    ├── test/  (Testing environment)
    └── prod/  (Production with custom domain)
```

## 🛣️ Future Enhancements

- 🔄 Vector database (RAG integration)
- 🧑‍🤝‍🧑 Multi-user digital twins
- 🧠 Long-term memory summarization
- 🖼️ Multimodal inputs (images, voice)
- 📊 Conversation analytics dashboard

---

## 📜 License

MIT License © 2025

---

## 🙌 Acknowledgements

- AWS Bedrock
- FastAPI
- Terraform
- Next.js

---

**Built to demonstrate production-ready AI systems, LLMOps, and cloud-native engineering excellence.** 🚀

