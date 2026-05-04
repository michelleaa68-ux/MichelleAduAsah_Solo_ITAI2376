# MichelleAduAsah_Solo_ITAI2376

# MIRA — Multi-Agent Event Decor Intelligence System

A three-agent AI system built for luxury event decor companies that handles client inquiries, creative vision matching, and internal inventory management.

---

## Team

Solo Project — Michelle Adu-Asah

---

## The Problem & Target User

Planning a luxury event involves multiple touchpoints: clients need quick answers about pricing and logistics, they need help translating their vision into a concrete aesthetic, and behind the scenes, decor workers need to check what inventory is available. Most businesses handle all of this manually, which is slow and inconsistent.

**MIRA** solves this by routing each type of need to a specialized agent — one for client Q&A, one for creative direction, and one for internal warehouse access — all in a single system.

**Target users:** Luxury event decor companies and their clients in the Houston metro area.

---

## Option Chosen

**Option B: Multi-Agent System**

This matches the blueprint submitted in the Midterm. The plan did not change — the three-agent structure (MIRA, MIZEL, MILO) was designed from the start and carried through to implementation.

---

## Architecture Overview

MIRA is a rule-based multi-agent system with three distinct agents, each with its own role, logic, and access level. When the system starts, the user selects which agent they need. Client-facing agents (MIRA and MIZEL) are open access. The internal agent (MILO) is passcode-protected so only authorized warehouse workers can enter.

- **MIRA** handles general client questions using keyword-based intent matching. It covers pricing, appointments, location, delivery, booking, and cancellation policies.
- **MIZEL** acts as a creative director. Clients describe their event vision in natural language and MIZEL responds with a tailored color scheme and full mood board.
- **MILO** is a restricted inventory tool for decor workers only. It displays current stock levels and flags items that are running low.

Each agent operates independently — there is no cross-agent communication. The routing logic at the top level determines which agent receives control based on the user's menu selection.

![Architecture Diagram](architecture.png)

---

## Frameworks and Tools

- **Language:** Python 3
- **Platform:** Google Colab (Jupyter Notebook)
- **LLM / AI Framework:** Rule-based logic (keyword matching and conditional branching — no external LLM API required)
- **Memory:** In-session inventory dictionary (MILO); stateless for MIRA and MIZEL
- **Access Control:** Hardcoded passcode for MILO agent
- **Demo Platform:** builder.io project preview

---

## Installation

**Python version:** Python 3.8 or higher

**1. Clone the repository:**
```bash
git clone https://github.com/YourUsername/YourRepoName_ITAI2376.git
cd YourRepoName_ITAI2376
```

**2. Install dependencies:**
```bash
pip install -r requirements.txt
```

> Note: This project uses only Python standard libraries and requires no external API keys. No `.env` setup is needed to run the base system.

**3. (Optional) Set up environment variables:**

If you extend the project to use an LLM API, copy the example file and fill in your keys:
```bash
cp .env.example .env
```

---

## How to Run

**In Google Colab:** Open `agent.ipynb` and run all cells. The system will prompt you in the output cell.

**Locally:**
```bash
jupyter notebook agent.ipynb
```

Then run the single code cell. You will see a menu:

```
  Choose who is using the system:
  1 - Client (talk to MIRA)
  2 - Client (describe vision to MIZEL)
  3 - Worker (access MILO inventory)

  Enter 1, 2, or 3:
```

---

## Example Usage

### Example 1 — MIRA (Client Q&A)

**Input:** `1` → `How much is a birthday party for 60 people?`

**Output:**
```
=======================================================
  MIRA — Client Assistant
=======================================================
  Client asked: how much is a birthday party for 60 people?

  MIRA says:
  Our packages start at $2,500 for intimate gatherings. The Elegance package
  is $2,500–$5,000, the Luxe package is $5,000–$12,000, and the Couture
  package is fully custom quoted based on your vision and guest count.
```

---

### Example 2 — MIZEL (Creative Vision)

**Input:** `2` → `I want something royal and grand with blue and gold`

**Output:**
```
=======================================================
  MIZEL — Creative Visual Agent
=======================================================
  Client vision: I want something royal and grand with blue and gold

  Suggested color scheme: Royal Blue, Gold, and Crisp White

  Mood board:
  For a grand and regal feel, we recommend deep royal blue linen with bright
  gold charger plates and white floral centerpieces featuring hydrangeas and
  white orchids with gold ribbon accents. Tall centerpiece arrangements will
  create that majestic ballroom atmosphere. Gold candelabras at alternating
  tables will add drama and elegance.
```

---

### Example 3 — MILO (Worker Inventory)

**Input:** `3` → passcode: `milo2376`

**Output:**
```
=======================================================
  MILO — Warehouse Inventory System
  ** FOR DECOR WORKERS ONLY **
=======================================================

  Access granted. Current inventory:

  ITEM                      IN STOCK
  -----------------------------------
  Chairs                    150
  Tables                    20
  Charger Plates            200
  Linen Tablecloths         40
  Linen Napkins             300
  Silverware Sets           250
  Floral Arches             3    <-- LOW STOCK
  Candelabras               12
  Uplighting Units          24
  Flower Wall Panels        8    <-- LOW STOCK
```

---

## Known Limitations

- **No LLM backbone:** MIRA and MIZEL use keyword matching, not a language model. Questions that don't contain expected keywords fall through to a generic fallback response.
- **No memory across sessions:** Each run starts fresh. MIRA does not remember previous conversations with a client.
- **Static inventory:** MILO displays inventory but cannot update it. Workers cannot add, subtract, or edit stock counts without editing the code directly.
- **Single-user at a time:** The system handles one interaction per run. There is no multi-user or concurrent session support.
- **Passcode is hardcoded:** The MILO passcode (`milo2376`) is stored in plain text in the notebook. For a production system, this would need to be moved to a secure environment variable.
- **No appointment booking integration:** MIRA references a phone number and email but cannot actually schedule or confirm appointments.

---

## Demo

[Watch the demo here](https://fe5be83cca054a75b5f5d01282c6ab68-main_v2.projects.builder.my)

The demo covers at least three real-world scenarios: a client pricing inquiry (MIRA), a creative vision consultation (MIZEL), and a worker inventory check (MILO).
