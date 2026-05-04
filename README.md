
---

# MIRA — Multi-Agent Event Decor Intelligence System

MIRA is a three-agent AI system built for luxury event decor companies. It handles client questions, creative direction, and internal inventory — all in one place.

---

## Team

Solo Project — Michelle Adu-Asah

---

## The Problem

Planning a luxury event isn’t just one task — it’s a full workflow.
Clients want quick answers (pricing, booking, logistics), they need help visualizing their event, and internally, workers need access to inventory.

Most of this is still done manually — which is slow and inconsistent.

MIRA fixes that by splitting everything into three focused agents.

**Target users:** Luxury event decor companies and their clients in the Houston area

---

## Approach

**Multi-Agent System (Option B)**

Built exactly from the original plan — three agents (MIRA, MIZEL, MILO), each with a clear role.

---

## Architecture

MIRA is a rule-based system where users choose their role and get routed to the right agent.

* **MIRA** → Client assistant (pricing, booking, FAQs)
* **MIZEL** → Creative agent (vision → mood board + colors)
* **MILO** → Inventory system (workers only, passcode protected)

Each agent runs independently — no overlap, just clean routing.

---

## Tools & Tech

* Python 3
* Google Colab (Jupyter Notebook)
* Rule-based logic (keyword matching + conditionals)
* In-session memory (MILO only)
* Passcode protection for internal access

---

## How to Run

**Colab:** Open `agent.ipynb` and run the cell

**Local:**

```bash
jupyter notebook agent.ipynb
```

Menu:

```
Choose who is using the system:
1 - Client (MIRA)
2 - Client (MIZEL)
3 - Worker (MILO)

Enter 1, 2, or 3:
```

---

## Example Usage

### MIRA — Client Q&A

**Input:**

```
1
How much is a birthday party for 60 people?
```

**Output:**

```
MIRA — Client Assistant

Client asked: how much is a birthday party for 60 people?

Our packages start at $2,500 for intimate gatherings.
Elegance: $2,500–$5,000  
Luxe: $5,000–$12,000  
Couture: custom pricing based on your vision and guest count.
```

---

### MIZEL — Creative Vision

**Input:**

```
2
I want something royal and grand with blue and gold
```

**Output:**

```
MIZEL — Creative Visual Agent

Suggested color scheme:
Royal Blue, Gold, Crisp White

Mood direction:
Deep royal blue linens, gold charger plates, white floral centerpieces
(hydrangeas + orchids), tall arrangements, and gold candelabras for a
dramatic, elegant look.
```

---

### MILO — Inventory (Restricted)

**Input:**

```
3
Enter passcode: milo2376
```

**Output:**

```
MILO — Warehouse Inventory System
Access granted.

ITEM                    IN STOCK
--------------------------------
Chairs                  150
Tables                  20
Charger Plates          200
Linen Tablecloths       40
Floral Arches           3   <-- LOW
Flower Wall Panels      8   <-- LOW
```

---

## Limitations

* No LLM (keyword-based only)
* No memory across sessions
* Inventory is view-only
* Single-user system
* Passcode is hardcoded
* No real booking integration

---

## Demo

[https://fe5be83cca054a75b5f5d01282c6ab68-main_v2.projects.builder.my](https://fe5be83cca054a75b5f5d01282c6ab68-main_v2.projects.builder.my)

