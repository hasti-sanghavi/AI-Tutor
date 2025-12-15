# AI Learning Coach – Phase 1 (Track A)

This repository contains **Phase 1 implementation** of an AI Learning Coach built as part of **Practice Set 2.0 – Build Your Own AI Learning Coach**.

Phase 1 focuses on **Track A (Beginner)** and implements all core required features using **n8n**, **Supabase**, and **OpenAI**.

video recording: https://youtu.be/JEul7KVqcPA
---

## 🎯 What This Project Does

The AI Learning Coach:
- Ingests learning content from RSS feeds
- Processes and stores content using vector embeddings
- Generates personalized daily learning digests
- Allows semantic search across past insights and content

All automation is implemented using **n8n workflows**.

---

## 🧠 Tech Stack

- **Workflows:** n8n
- **Database:** Supabase (PostgreSQL + pgvector)
- **AI Models:**
  - `text-embedding-3-small`
  - `gpt-4o-mini`

---

## 🧩 Implemented Features (Phase 1)

### 1. Content Source Management
**Workflow:** `Content RSS.json`

- Add RSS sources
- Assign priority levels
- Enable / disable sources
- Delete sources
- Supports webhook + natural language input

---

### 2. Automated Content Ingestion
**Workflow:** `Ingestion – Fetching + Chunking + Embedding.json`

- Scheduled ingestion every 6 hours
- Fetches active RSS feeds
- Deduplicates content using URL + content hash
- Cleans HTML to plain text
- Chunks content for vector search
- Generates embeddings
- Stores data in Supabase

---

### 3. Daily Digest Generator
**Workflow:** `Daily Digest Generator.json`

- Runs on a daily schedule
- Builds user context
- Performs vector similarity search
- Generates structured learning digest using OpenAI
- Stores:
  - Daily digest
  - Individual insights
  - Insight embeddings
- Computes a digest quality score

---

### 4. Insights History & Search
**Workflow:** `Insights History - Search & Retrieve.json`

- Semantic search via webhook
- Embeds user query
- Searches across:
  - Past insights
  - Ingested content chunks
- Combines and ranks results
- Returns structured JSON response

---

## 📁 Repository Structure

```text
.
├── workflows/
│   ├── Content RSS.json
│   ├── Ingestion – Fetching + Chunking + Embedding.json
│   ├── Daily Digest Generator.json
│   └── Insights History - Search & Retrieve.json
└── README.md

