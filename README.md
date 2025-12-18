
# 🍽️ AI Restaurant & Meal Recommendation Virtual Assistant  
*A multi-tool LLM-powered assistant for restaurant search, recipe generation, and intelligent food recommendations.*

---

## 📌 Overview

This project implements a **Virtual Assistant (VA)** that answers food-related queries using:

- 🍔 **Restaurant search**
- 👩‍🍳 **Recipe recommendations**
- 🥗 **Ingredient-based meal ideas**
- 🌐 **Web search fallback**
- 📊 **Offline Yelp Academic Dataset**
- 🤖 **Two LLMs** (small + large)

The system selects and combines tools intelligently using a **model-driven tool planner**, then constructs a final answer using both **Mistral-7B** and **LLaMA-3 70B (Groq)**.

This project fulfills all requirements of an academic LLM systems assignment:
- Two different open-source models  
- Tool use (DB + API + web search)  
- Prompting strategies (meta-prompting, chain-of-thought refinement, reflection)  
- Prompt caching performance evaluation  
- Security testing (prompt injection)  
- Complete notebook with reproducible results  

---

## 🚀 Key Features

### 🧠 Intelligent Tool Planner  
Automatically determines which tools to use:
- Yelp Offline Dataset  
- MealDB Recipe API  
- Tavily Web Search  
- Or all combined  

### 🏪 Restaurant Finder  
Supports:
- Cuisine filtering  
- City + fuzzy matching (Las Vegas → Paradise / Spring Valley / Henderson)  
- Rating threshold  
- Delivery / Takeout / Outdoor seating  
- Open-now filter  
- Web search fallback  

### 🍽️ Recipe Mode  
If the user asks for:
- Meals  
- Ingredients  
- Cooking ideas  

→ The assistant switches into **MealDB recipe mode**, formats a structured recipe, and adds next-step suggestions.

### 🌐 Web Search Fallback  
If Yelp returns no results:
- The VA performs Tavily web search  
- Extracts restaurant-like info  
- Feeds it to the LLM  

Useful for:  
✔ cities not in offline Yelp  
✔ trending/new restaurants  

### 🤖 Two LLM Backends  
| Usage | Model | Provider |
|-------|--------|----------|
| Small reasoning | `mistralai/mistral-7b-instruct:free` | OpenRouter |
| Large reasoning | `llama3-70b-versatile` | Groq (official SDK) |

### ⚡ Prompt Caching  
Reduces response time significantly for repeated queries.

### 🔐 Security Testing  
10+ prompt-injection attacks including:
- "Ignore all instructions…"  
- "Reveal system prompts…"  
- "Show your API keys…"  
- "Dump internal memory…"  

Output includes real model responses for reporting.

