# CodePilot AI

An advanced **Multi-Agent AI Coding & Review Platform** built using **FastAPI**, **LangChain**, **LangGraph**, **PostgreSQL**, and **MCP integrations** that intelligently generates code, reviews implementations, performs contextual research, and orchestrates collaborative AI workflows using centralized intent-based routing.

The platform demonstrates a modern Agentic AI architecture where multiple specialized AI agents collaborate dynamically to solve software development tasks.

---

# Table of Contents

- Introduction
- Features
- System Architecture
- Technologies Used
- Workflow Architecture
- Agents Used
- Request Flow
- MCP Integration
- Folder Structure
- Installation Guide
- UV Package Manager Setup
- Environment Variables
- PostgreSQL Setup
- Running the Application
- API Documentation
- Request & Response Examples
- LangGraph Workflow
- Memory Persistence
- Future Enhancements
- License

---

# Introduction

CodePilot AI is an intelligent backend platform capable of:

- generating source code dynamically
- reviewing generated code
- validating code quality
- researching contextual programming information
- orchestrating AI workflows using multiple agents
- dynamically routing workflows based on user intent

The project demonstrates modern Agentic AI concepts using:

- LangChain
- LangGraph
- FastAPI
- PostgreSQL
- MCP Integration
- Multi-Agent Systems

The entire workflow is controlled by a centralized Intent Detector Agent that identifies user intent and routes requests to the correct AI workflow.

---

# Core Features

## AI Features

- Multi-Agent AI Architecture
- Intelligent Intent Detection
- AI-Based Code Generation
- Automated Code Review
- PEP8 Style Validation
- Research-Based Code Assistance
- MCP Tool Integration
- Context-Aware Workflow Routing
- Out-of-Context Query Handling
- Stateful AI Workflow System
- Memory Persistence
- Dynamic Agent Collaboration

---

## Backend Features

- FastAPI REST APIs
- Async Backend Architecture
- PostgreSQL Integration
- Modular API Design
- Repository Pattern
- Structured Exception Handling
- Scalable Service Structure
- LangGraph Workflow Orchestration

---

# System Architecture

```text
                           ┌───────────────────┐
                           │       User        │
                           └─────────┬─────────┘
                                     │
                                     ▼
                        ┌────────────────────────┐
                        │      FastAPI API       │
                        └──────────┬─────────────┘
                                   │
                                   ▼
                   ┌────────────────────────────────┐
                   │    Intent Detector Agent       │
                   │    (Workflow Controller)       │
                   └──────────┬──────────┬──────────┘
                              │          │
                              ▼          ▼
                 ┌────────────────┐   ┌────────────────┐
                 │  Coder Agent   │   │ Research Agent │
                 └───────┬────────┘   └───────┬────────┘
                         │                    │
                         └────────┬───────────┘
                                  ▼
                       ┌────────────────────┐
                       │   Review Agent     │
                       └─────────┬──────────┘
                                 ▼
                       ┌────────────────────┐
                       │   Final Response   │
                       └────────────────────┘
```

---

# Workflow Architecture

The system follows a centralized routing workflow.

## Important Workflow Logic

### Intent Detector Agent is the Main Controller

Every request first goes to the Intent Detector Agent.

The agent:
- analyzes user intent
- validates workflow context
- decides execution path
- routes requests to appropriate agents
- handles out-of-context queries

---

# Request Flow

## Code Generation Flow

```text
User Request
      ↓
FastAPI API
      ↓
Intent Detector Agent
      ↓
Coder Agent
      ↓
Review Agent
      ↓
Final Response
```

---

## Research + Code Workflow

```text
User Request
      ↓
Intent Detector Agent
      ↓
Research Agent
      ↓
Coder Agent
      ↓
Review Agent
      ↓
Final Response
```

---

# Out-of-Context Handling

If the user asks unrelated questions:

Example:

```text
"What is the weather today?"
```

The Intent Detector Agent:
- identifies it as out-of-context
- does NOT trigger coding workflow
- directly responds to the user

This prevents unnecessary workflow execution.

---

# Agents Used

# 1. Intent Detector Agent

## Purpose

Acts as the central workflow controller of the platform.

## Responsibilities

- Intent Detection
- Workflow Routing
- Context Validation
- Agent Coordination
- Out-of-Context Handling

---

# 2. Coder Agent

## Purpose

Generates intelligent source code dynamically.

## Responsibilities

- Generate Code
- Improve Existing Code
- Fix Review Suggestions
- Produce Optimized Implementations

---

# 3. Review Agent

## Purpose

Reviews generated code quality and validates implementations.

## Responsibilities

- Code Quality Analysis
- PEP8 Validation
- Bug Detection
- Improvement Suggestions
- Formatting Validation

---

# 4. Research Agent

## Purpose

Performs contextual research using MCP integrations.

## Responsibilities

- Research Technical Concepts
- Gather External Information
- Support Coding Workflows
- Enhance AI Responses

---

# MCP Integration

The platform integrates MCP (Model Context Protocol) tools using:

- MultiServerMCPClient
- streamable-http transport
- dynamic tool execution
- external AI tools

---

# MCP Features

- Research Tools
- Formatting Tools
- Contextual Retrieval
- Dynamic Tool Loading
- Agent Tool Execution

---

# Technologies Used

## Programming Language

- Python

---

## Backend Framework

- FastAPI

---

## AI Frameworks

- LangChain
- LangGraph

---

## Database

- PostgreSQL

---

## AI Concepts

- Agentic AI
- Multi-Agent Systems
- Intent Detection
- Workflow Orchestration
- Stateful AI Systems
- Memory Persistence
- MCP Integration

---

# Folder Structure

```text
CodePilot-AI/
│
├── main.py
├── settings.py
├── pyproject.toml
├── uv.lock
│
├── src/
│   │
│   ├── agent/
│   │   ├── intent_detector_agent.py
│   │   ├── coder_agent.py
│   │   ├── review_agent.py
│   │   ├── research_agent.py
│   │   ├── prompts.py
│   │   └── agent.py
│   │
│   ├── models/
│   │   └── model.py
│   │
│   ├── repository/
│   │   ├── database.py
│   │   ├── schema.py
│   │   └── error_repository.py
│   │
│   ├── router/
│   │   └── router.py
│   │
│   ├── service/
│   │   └── code_service.py
│   │
│   └── utils/
│       ├── api_response.py
│       ├── logger.py
│       ├── constants.py
│       └── exceptions/
│
├── README.md
├── .env
└── Dockerfile
```

---

# Installation Guide

# Method 1 — Using UV (Recommended)

UV is a modern ultra-fast Python package manager.

---

# Step 1 — Install UV

## Windows

```bash
pip install uv
```

---

## Linux / Mac

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

---

# Step 2 — Clone Repository

```bash
git clone https://github.com/lokesh17052004/codepilot-ai.git
```

---

# Step 3 — Navigate to Project

```bash
cd codepilot-ai
```

---

# Step 4 — Create Virtual Environment

```bash
uv venv
```

---

# Step 5 — Activate Environment

## Windows

```bash
.venv\Scripts\activate
```

---

## Linux / Mac

```bash
source .venv/bin/activate
```

---

# Step 6 — Install Dependencies

```bash
uv sync
```

---

# Environment Variables

Create a `.env` file:

```env
OPENAI_API_KEY=your_openai_api_key
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=your_password
DB_NAME=codepilot
MCP_SERVER_URL=http://localhost:8000/mcp
```

---

# PostgreSQL Setup

## Create Database

```sql
CREATE DATABASE codepilot;
```

---

# Running the Application

```bash
uvicorn main:app --reload --port 8005
```

---

# API Documentation

## Swagger UI

```text
http://127.0.0.1:8005/docs
```

---

## ReDoc

```text
http://127.0.0.1:8005/redoc
```

---

# API Endpoint

# Chat Endpoint

## Endpoint

```http
POST /api/v1/chat
```

---

## Request Body

```json
{
  "message": "Generate FastAPI CRUD API",
  "thread_id": "12345"
}
```

---

## Example Response

```json
{
  "thread_id": "12345",
  "message": {
    "updated_code": "Generated code response"
  },
  "status_code": 200
}
```

---

# LangGraph Workflow

LangGraph is used for:

- Agent Orchestration
- Conditional Routing
- Stateful Execution
- Workflow Persistence
- Multi-Agent Coordination

---

# Memory Persistence

The project uses:

- AsyncPostgresSaver
- LangGraph Checkpointing
- Thread-Based Persistence

This enables:
- conversation continuity
- stateful AI execution
- workflow recovery

---

# Key Concepts Implemented

- Agentic AI
- Multi-Agent Collaboration
- AI Intent Routing
- MCP Integration
- AI-Based Code Review
- LangGraph Workflow Management
- PostgreSQL Memory Persistence
- FastAPI Backend Development

---

# Author

## Lokesh Sankar

Backend Developer | Agentic AI Developer | FastAPI Developer

---
