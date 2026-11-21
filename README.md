# 🧠 CogniSearch Network

> **AI Enterprise Cognitive Search Network**  
> A multi-agent AI search system that understands intent, retrieves evidence via GraphRAG, reasons step-by-step, verifies facts, and synthesizes verified answers — built with Python, FastAPI, React & Google Gemini.

![GitHub last commit](https://img.shields.io/github/last-commit/vishakha2121/cognisearch-network?style=flat-square)
![GitHub repo size](https://img.shields.io/github/repo-size/vishakha2121/cognisearch-network?style=flat-square)
![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue?style=flat-square&logo=python)
![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688?style=flat-square&logo=fastapi)
![Gemini](https://img.shields.io/badge/Google%20Gemini-API-4285F4?style=flat-square&logo=google)

---

## 📖 Table of Contents
1. [Project Overview](#-project-overview)
2. [System Architecture](#-system-architecture)
3. [Core Features](#-core-features)
4. [Technology Stack](#-technology-stack)
5. [Multi-Agent Pipeline](#-multi-agent-pipeline)
6. [GraphRAG (Graph Retrieval-Augmented Generation)](#-graphrag-graph-retrieval-augmented-generation)
7. [Database Schema](#-database-schema)
8. [Folder Structure](#-folder-structure)
9. [API Endpoints](#-api-endpoints)
10. [Installation & Setup Guide](#-installation--setup-guide)
11. [Environment Variables](#-environment-variables)
12. [How to Run the Project](#-how-to-run-the-project)
13. [Future Scope](#-future-scope)
14. [Contributing](#-contributing)
15. [License](#-license)

---

## 🔍 Project Overview

**CogniSearch Network** is an AI-powered cognitive search system that reimagines how we interact with information. Unlike traditional search engines that simply match keywords and return a list of links, CogniSearch deploys a coordinated network of specialized AI agents that collaborate to deeply understand user intent, retrieve relevant evidence, reason through complex questions, verify their findings, and deliver a synthesized, trustworthy answer with citations.

### 🎯 The Problem We Solve
Traditional keyword-based search engines often fail when a user asks complex, multi-hop questions (e.g., *"How does the CEO of Company X relate to the latest acquisition in the tech industry, and what are the financial implications?"*). Keyword matching fails here because the information is scattered across multiple documents.

### 💡 The CogniSearch Solution
We use **Multi-Step Reasoning** and **GraphRAG**. Our system doesn't just look for keywords; it builds a **Knowledge Graph** of entities and relationships, retrieves the right context using vector embeddings, and uses a team of AI agents to reason through the connections before generating an answer.

---

## 🏗️ System Architecture

The architecture is divided into three main layers: **Frontend (React)**, **Backend (FastAPI)**, and **AI Core (Agents & GraphRAG)**.

```text
[ User Query ]
      │
      ▼
┌────────────────────────────────────────────────────────┐
│               FRONTEND (React + Tailwind)              │
│  - Interactive UI, Knowledge Graph Viewer, Chat UI     │
└─────────────────────────┬──────────────────────────────┘
                          │ HTTP/REST
                          ▼
┌────────────────────────────────────────────────────────┐
│                BACKEND API (FastAPI)                   │
│  - Routes, Validation, Document Ingestion              │
└─────────────────────────┬──────────────────────────────┘
                          │
                          ▼
┌────────────────────────────────────────────────────────┐
│             MULTI-AGENT ORCHESTRATOR                   │
│                                                        │
│   1. Intent Agent    ──▶ Extracts true user intent     │
│   2. Retrieval Agent ──▶ Queries Vector DB & Graph     │
│   3. Reasoning Agent ──▶ Step-by-step logic execution  │
│   4. Verification    ──▶ Checks facts against sources  │
│   5. Synthesis Agent ──▶ Generates final cited answer  │
└─────────────────────────┬──────────────────────────────┘
                          │
         ┌────────────────┴────────────────┐
         ▼                                 ▼
┌──────────────────┐             ┌──────────────────┐
│   Vector DB      │             │ Knowledge Graph  │
│ (ChromaDB)       │             │ (SQLite/SQL)     │
│ - Semantic Search│             │ - Entities/Edges │
└──────────────────┘             └──────────────────┘

cognisearch-network/
├── backend/
│   ├── app/
│   │   ├── api/          # FastAPI Routes
│   │   ├── agents/       # Multi-Agent logic
│   │   ├── graphrag/     # Graph building & traversal
│   │   ├── rag/          # Vector search & embeddings
│   │   ├── reasoning/    # Multi-step logic
│   │   ├── models/       # DB & Pydantic models
│   │   ├── utils/        # Helpers
│   │   └── main.py       # Entry point
│   ├── requirements.txt
│   └── .env
├── frontend/
│   ├── src/
│   │   ├── components/   # UI Components
│   │   ├── pages/        # React Pages
│   │   ├── api/          # Axios setup
│   │   ├── hooks/        # Custom hooks
│   │   └── App.jsx
│   ├── package.json
│   └── tailwind.config.js
├── database/
│   ├── schema.sql
│   └── migrations/
└── README.md

python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activatec