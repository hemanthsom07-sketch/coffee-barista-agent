# ☕ Coffee Barista AI Agent

An AI-powered coffee shop assistant built with **Google Cloud, Gemini, Google ADK, Streamlit, and Retrieval-Augmented Generation (RAG)**.

The agent understands natural-language customer preferences and recommends items from a grounded coffee shop menu while following constraints such as menu availability and dietary requirements.

---

## 🚀 Project Overview

Coffee Barista is an AI agent that acts as a virtual coffee shop barista.

Instead of requiring users to search through a static menu, users can describe what they want in natural language.

For example:

> "I want something strong and warm."

The agent understands the request and recommends an appropriate menu item.

It can also handle requests such as:

- "I want a cold, strong, dairy-free coffee."
- "Do you have a matcha frappuccino?"
- "I'm lactose intolerant, what can I get?"
- "Recommend something sweet and hot."

The agent is designed to remain grounded in the available menu instead of inventing products.

---

## ✨ Features

### 🤖 AI Barista

Uses Gemini to understand natural-language customer requests and provide recommendations.

### 🔎 RAG-Based Menu Grounding

The agent retrieves relevant menu information before generating recommendations.

This helps reduce hallucinations and keeps responses grounded in the available menu.

### 🛡️ Safety & Constraint Handling

The agent was tested against:

- In-menu requests
- Out-of-menu requests
- Dietary/allergen-aware requests

For example, when asked for a product that does not exist on the menu, the agent declines the request instead of pretending that the product exists.

### 🥛 Dietary Awareness

The menu contains attributes such as:

- Dairy-free
- Sugar-free
- Sweet
- Hot
- Cold

The agent uses these attributes when making recommendations.

### 💬 Interactive Streamlit UI

A user-friendly Streamlit interface displays:

- Coffee shop menu
- Menu descriptions
- Prices
- Tags
- AI conversation
- Recommendations

### ☁️ Google Cloud Deployment

The application was deployed using:

- Google Cloud Run
- Cloud Build
- Artifact Registry
- Dedicated Cloud Run service account

### 🗄️ Firestore Vector Search

The project was extended to support dynamic menu retrieval using:

- Cloud Firestore
- Vector embeddings
- Firestore Vector Search
- Gemini text embeddings

This allows menu data to be stored outside the application container.

---

## 🏗️ Architecture

```text
                    ┌─────────────────────┐
                    │       User          │
                    │  Natural Language   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Streamlit App     │
                    │       app.py        │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    AI Barista       │
                    │      agent.py       │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Menu Retrieval    │
                    │       RAG           │
                    └──────────┬──────────┘
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
                 ▼                           ▼
        ┌─────────────────┐        ┌──────────────────┐
        │   menu.json     │        │    Firestore     │
        │  Local Menu     │        │  Vector Search   │
        └─────────────────┘        └────────┬─────────┘
                                           │
                                           ▼
                                  ┌──────────────────┐
                                  │ Gemini Embeddings│
                                  │  Semantic Search │
                                  └────────┬─────────┘
                                           │
                                           ▼
                                  Relevant Menu Items
                                           │
                                           ▼
                                  ┌──────────────────┐
                                  │      Gemini      │
                                  │  Final Response  │
                                  └──────────────────┘
🧰 Tech Stack
Technology	Purpose
Python	Application development
Streamlit	Web interface
Google Gemini	AI reasoning and responses
Google ADK	Agent development
Google Cloud Run	Application deployment
Cloud Firestore	Menu database
Firestore Vector Search	Semantic menu retrieval
Gemini Embeddings	Text vector generation
Cloud Build	Container build process
Artifact Registry	Container storage
📁 Project Structure
coffee-barista-agent/
│
├── agent.py
├── app.py
├── menu.json
├── requirements.txt
├── seed.py
└── README.md
agent.py

Contains the AI agent logic and menu retrieval functionality.

app.py

Contains the Streamlit application and user interface.

menu.json

Contains the original coffee shop menu data.

seed.py

Seeds menu data into Firestore and generates vector embeddings.

requirements.txt

Contains the Python dependencies required by the application.

🧠 RAG Workflow

The application follows a retrieval-augmented workflow:

User Query
     │
     ▼
Understand User Intent
     │
     ▼
Generate Query Embedding
     │
     ▼
Search Menu Using Vector Similarity
     │
     ▼
Retrieve Relevant Menu Items
     │
     ▼
Provide Retrieved Context to Agent
     │
     ▼
Generate Grounded Recommendation

Instead of relying entirely on the language model's general knowledge, the agent retrieves information from the coffee shop's menu.

🧪 Testing

The agent was tested using three important scenarios.

1. In-Menu Request

Query:

Recommend something strong and warm.

Expected behavior:

The agent recommends an appropriate menu item such as Espresso Solo.

2. Out-of-Menu Request

Query:

Do you have a matcha frappuccino?

Expected behavior:

The agent explains that the requested item is not available rather than hallucinating a menu item.

3. Allergen-Aware Request

Query:

I'm lactose intolerant, what can I get?

Expected behavior:

The agent recommends appropriate dairy-free menu items and avoids unsuitable products.

☁️ Google Cloud Deployment

The application was deployed to Google Cloud Run using source-based deployment.

Cloud Run uses Google Cloud Buildpacks to detect the Python application and create the container without requiring a custom Dockerfile.

The application used a dedicated service account with limited permissions following the principle of least privilege.

🔐 Security

The project uses a dedicated service account rather than relying on a broadly privileged default service account.

The application was configured with the required Google Cloud permissions for accessing AI services and Firestore.

API keys and secrets should never be committed to GitHub.

📸 Application
Coffee Shop Interface

The Streamlit application provides a menu sidebar and an interactive AI barista conversation interface.

Add your screenshot here:

![Coffee Barista Application](screenshots/coffee-barista.png)
📚 What I Learned

Through this project, I learned how to:

Build an AI agent using Google ADK
Integrate Gemini with a Python application
Build a RAG-based workflow
Ground LLM responses using application data
Perform semantic retrieval using vector embeddings
Use Firestore Vector Search
Build interactive AI applications with Streamlit
Deploy Python applications to Google Cloud Run
Configure Google Cloud IAM permissions
Use dedicated service accounts
Work with Google Cloud APIs
Test AI agents for hallucination and constraint handling
🔮 Future Improvements

Potential improvements include:

Real-time menu management
Order placement
Shopping cart functionality
Customer accounts
Order history
Payment integration
Personalized recommendations
Conversation memory
Restaurant inventory integration
Admin dashboard
Production monitoring and analytics
👨‍💻 Author

Hemanth R.S

Computer Science & Engineering
Global Academy of Technology, Bangalore

GitHub: hemanthsom07-sketch

⭐ Project Highlights

AI Agent + RAG + Vector Search + Google Cloud + Streamlit
