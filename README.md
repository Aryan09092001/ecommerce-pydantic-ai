# 🛍️ LUXE — AI-Powered E-Commerce Platform

> A full-stack e-commerce store with a **conversational AI shopping assistant** that turns plain English into live database queries — built with **FastAPI**, **MongoDB**, and **Pydantic AI**.

<p align="left">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white">
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white">
  <img alt="MongoDB" src="https://img.shields.io/badge/MongoDB%20Atlas-47A248?logo=mongodb&logoColor=white">
  <img alt="Pydantic AI" src="https://img.shields.io/badge/Pydantic%20AI-E92063?logo=pydantic&logoColor=white">
  <img alt="Groq" src="https://img.shields.io/badge/Groq%20LLM-F55036?logo=groq&logoColor=white">
  <img alt="Logfire" src="https://img.shields.io/badge/Logfire-Observability-E92063">
  <img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white">
</p>

---

## ✨ Overview

**LUXE** is a complete online clothing store where customers can browse, filter, and shop products — and, most importantly, **chat with an AI assistant in natural language** to find exactly what they want.

Instead of clicking through menus and price sliders, a customer can simply type:

> *"Show me men's shirts under ₹2000"*

…and the AI agent understands the intent, builds the right MongoDB query, fetches **real products from the database**, and replies conversationally. This is achieved with **Pydantic AI's tool-calling** — the LLM never invents fake products; it can only return data that genuinely exists.

---

## 🏆 Technical Highlights & Results

| Metric / Outcome | Detail |
|------------------|--------|
| 🤖 **Agentic AI search** | LLM autonomously translates natural language → structured MongoDB queries (**Text2NoSQL**) via tool-calling |
| 🚫 **0 hallucinated products** | Tool-grounded architecture guarantees the assistant returns **only real database records** — a hard requirement for commerce |
| ⚡ **Sub-second LLM responses** | Served via **Groq** inference for low-latency conversational UX |
| 🔌 **12+ REST endpoints** | Spanning **4 domains** (products, cart, orders, chatbot) in a clean, modular router design |
| 🛡️ **100% type-safe I/O** | Every request/response validated by **Pydantic v2** — no unvalidated data reaches the database |
| 📦 **500-product seeding** | One-call demo data generator to load-test and showcase filtering at scale |
| 📊 **Full-stack observability** | Auto-instrumented tracing of every request and AI call with **Pydantic Logfire** |
| 🐳 **Deploy in one command** | Containerized with **Docker** — reproducible builds, environment-agnostic |

> **In short:** an end-to-end product demonstrating modern **agentic AI**, **API design**, **data validation**, **observability**, and **containerized deployment** — the full lifecycle of a production-style application.

---

## 🎯 Key Features

### 🤖 AI Shopping Assistant (the highlight)
- **Natural-language product search** — "Text2NoSQL": converts human messages into MongoDB queries
- **Agentic tool-calling** with Pydantic AI — the LLM autonomously decides *when* and *how* to search
- **Grounded responses** — strict system prompt prevents hallucinated products, prices, or details
- **Context-aware filtering** by category, keyword, and price range
- Powered by **Groq** (`qwen3-32b`) for fast, low-latency inference

### 🛒 Core Commerce
- **Product catalog** with category & price-range filtering
- **Full CRUD** for products (create, read, update, delete) with **image upload** (Base64 storage)
- **Shopping cart** — add items, view per-user cart, clear after checkout
- **Order placement** with validated payloads
- **Bulk data generator** — seed 500 realistic demo products across men/women/kids with one API call

### ⚙️ Engineering Quality
- **Type-safe** request/response validation with **Pydantic v2** models
- **Modular architecture** — routes split by domain (`products`, `cart`, `orders`, `chatbot`) via FastAPI routers
- **Production-grade observability** with **Pydantic Logfire** (auto-instrumented FastAPI + Pydantic)
- **Auto-generated interactive API docs** (Swagger UI) out of the box
- **Containerized** with Docker for consistent, one-command deployment anywhere

---

## 🏗️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend API** | FastAPI, Uvicorn |
| **AI / Agent** | Pydantic AI, Groq LLM (`qwen3-32b`) |
| **Database** | MongoDB Atlas (PyMongo) |
| **Validation** | Pydantic v2 |
| **Observability** | Pydantic Logfire |
| **Frontend** | Vanilla JavaScript SPA (custom router, components, services) |
| **Containerization** | Docker |
| **Config** | python-dotenv |

---

## 📐 Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (SPA)                         │
│   Vanilla JS · router · pages · components · API client   │
└───────────────────────────┬─────────────────────────────┘
                            │  HTTP / JSON
┌───────────────────────────▼─────────────────────────────┐
│                      FastAPI App                          │
│  ┌──────────┐ ┌────────┐ ┌────────┐ ┌────────────────┐   │
│  │ products │ │  cart  │ │ orders │ │    chatbot     │   │
│  │  router  │ │ router │ │ router │ │ (Pydantic AI)  │   │
│  └────┬─────┘ └───┬────┘ └───┬────┘ └───────┬────────┘   │
│       │           │          │              │            │
│       │      Pydantic v2 validation         │            │
│       │           │          │       Groq LLM + tool     │
└───────┼───────────┼──────────┼──────────────┼────────────┘
        │           │          │              │
        ▼           ▼          ▼              ▼
┌─────────────────────────────────────────────────────────┐
│                   MongoDB Atlas                           │
│        products · cart · orders · users                   │
└─────────────────────────────────────────────────────────┘
              ▲
              │  auto-instrumented traces
         Pydantic Logfire (observability dashboard)
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11+
- A **MongoDB Atlas** account (free tier works)
- A **Groq API key** (free) — for the AI chatbot
- *(Optional)* A **Logfire** token — for observability

### 1. Clone & set up the environment
```bash
git clone https://github.com/Aryan09092001/ecommerce-pydantic-ai.git
cd ecommerce-pydantic-ai

python -m venv ecpyenv
# Windows
ecpyenv\Scripts\activate
# macOS / Linux
source ecpyenv/bin/activate

pip install -r requirements.txt
```

### 2. Configure environment variables
Create a `.env` file in the project root:
```env
MONGO_URI=your_mongodb_atlas_connection_string
GROQ_API_KEY=your_groq_api_key
# Optional — enables observability
LOGFIRE_TOKEN=your_logfire_token
```

> 💡 In **MongoDB Atlas → Network Access**, add your IP (or `0.0.0.0/0` for local testing) so the app can connect.

### 3. Run the app
```bash
python main.py
```

The server starts at **http://localhost:8000**

| URL | Description |
|-----|-------------|
| http://localhost:8000 | Storefront (frontend) |
| http://localhost:8000/docs | Interactive API documentation (Swagger UI) |

### 4. (Optional) Seed demo data
With the server running, generate 500 demo products:
```bash
curl -X POST http://localhost:8000/products/bulk-generate-500
```

---

## 🐳 Run with Docker

Prefer containers? The app ships with a `Dockerfile` — no local Python setup required.

```bash
# Build the image
docker build -t luxe-ecommerce .

# Run the container (pass your environment variables)
docker run -p 8000:8000 --env-file .env luxe-ecommerce
```

The app will be available at **http://localhost:8000**.

---

## 📡 API Reference

### Products
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/products` | List products (filters: `category`, `min_price`, `max_price`) |
| `POST` | `/products` | Add a product (with image upload) |
| `POST` | `/products/bulk` | Add multiple products |
| `POST` | `/products/bulk-generate-500` | Seed 500 demo products |
| `PUT` | `/products/{id}` | Update a product |
| `DELETE` | `/products/{id}` | Delete a product |
| `DELETE` | `/products` | Delete all products |

### Cart
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/cart/add` | Add an item to a user's cart |
| `GET` | `/cart/{user_email}` | Get a user's cart |
| `DELETE` | `/cart/{user_email}` | Clear a user's cart |

### Orders
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/orders` | Place an order |

### Chatbot
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/chat` | Send a message to the AI shopping assistant |

**Example chat request:**
```json
POST /chat
{ "message": "find me women's dresses under 1500" }
```
**Response (products found):**
```json
{
  "type": "products",
  "message": "Here are women's dresses under ₹1500!",
  "data": [ { "name": "Elegant Red Dress", "price": 1299, "category": "women", "...": "..." } ]
}
```

---

## 🧠 How the AI Assistant Works

```
User: "show me men's shirts under ₹2000"
        │
        ▼
 Pydantic AI Agent (Groq LLM)
        │  reads system prompt + decides intent
        ▼
 Calls tool → search_products(category="men", keyword="shirt", max_price=2000)
        │
        ▼
 Tool runs a real MongoDB query  ──►  returns matching products
        │
        ▼
 Agent replies conversationally + endpoint returns the product list to the UI
```

The agent is constrained by a strict system prompt and **can only surface products returned by the database tool** — eliminating hallucinated results, which is critical for a real commerce use case.

---

## 🛠️ Skills Demonstrated

- **Generative / Agentic AI** — LLM tool-calling, prompt engineering, grounding & hallucination control (Pydantic AI + Groq)
- **Backend Engineering** — RESTful API design, async endpoints, modular routing, file uploads (FastAPI)
- **Data & Persistence** — NoSQL schema design, dynamic query building, filtering & pagination (MongoDB / PyMongo)
- **Data Validation** — strongly-typed models and runtime validation (Pydantic v2)
- **Observability** — distributed tracing and request instrumentation (Logfire / OpenTelemetry)
- **DevOps** — containerization and reproducible deployments (Docker), environment-based config
- **Full-Stack Integration** — a JavaScript SPA frontend consuming the API and AI chat, served by the backend

---

## 📂 Project Structure

```
ecom-pydantic/
├── main.py                  # App entry point — mounts routers, frontend, Logfire
├── backend/
│   ├── database.py          # MongoDB Atlas connection & collections
│   ├── models.py            # Pydantic models (Product, Order, CartItem)
│   └── routes/
│       ├── products.py      # Product CRUD, filtering, bulk seeding
│       ├── cart.py          # Shopping cart operations
│       ├── orders.py        # Order placement
│       └── chatbot.py       # 🤖 Pydantic AI agent + search tool
├── Frontend/                # Vanilla JS SPA (router, pages, components, services)
├── Dockerfile               # Container build definition
├── .dockerignore
├── requirements.txt
└── README.md
```

---

## 🔮 Future Enhancements
- User authentication & JWT-based sessions (user model & bcrypt already in place)
- Payment gateway integration
- Order history & tracking
- Conversation memory for multi-turn chat context
- Vector search for semantic product recommendations

---

## 👤 Author

**Aryan Gorasiya**
🔗 [GitHub](https://github.com/Aryan09092001)

---

<p align="center"><i>Built to explore agentic AI in a real-world full-stack application.</i></p>
