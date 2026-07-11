# Setu — AI Operating System for Construction Supply Chains

**Track:** Supply Chain · **Event:** Kaya AI IIT India Hackathon 2026

> Setu ("bridge") is a live knowledge graph of a construction project's entire material lifecycle, paired with AI engines that read from and write back to that graph — for both the contractor placing orders and the supplier fulfilling them.

---

## Contents of this submission

| File | What it is |
|---|---|
| `Setu_Platform_Deck.pptx` | Full platform pitch deck (14 slides) — problem, architecture, every feature area, comparison, roadmap |
| `Setu_Demo_Page.html` | Interactive, clickable product demo — open it in a browser, no install needed |
| `Setu_Stage1_Proposal.docx` | Written Stage 1 proposal (problem, solution, technical approach, data model) |
| `Setu_Stage1_Deck.pptx` | Original 10-slide Stage 1 submission deck |

| `README.md` | This file |

---

## The problem

Once construction material is ordered, visibility disappears. Nobody can reliably say where a shipment is, whether a vendor will deliver on time, or whether what arrives is even the right material — and these failures compound: a delay, placed with an untracked vendor, can arrive as the wrong (or counterfeit) material, with no backup plan ready. Large construction projects typically run ~20% behind schedule and up to 80% over budget, and the industry's productivity has grown roughly 1% a year for decades.

## The idea

Instead of another dashboard bolted onto spreadsheets, Setu models a project's materials, vendors, shipments, and tasks as **one live graph**, and puts a set of AI engines on top of it that all read and write to that same graph — so a delay one engine predicts instantly updates the trust score another engine computes, with no manual syncing between tools.

---

## Feature map

### Core Engines
- **Risk Engine** — predicts delays and cascading downstream impact, factoring in monsoon and logistics signals.
- **Verify Engine** — vision-language matching of delivery photos against POs, and certificate checks for counterfeit material.
- **Trust Engine** — scores vendor reliability from real WhatsApp/email communication history, not a static rating.
- **Action Engine** — finds substitutes, autonomously drafts vendor outreach, and answers natural-language questions via real graph queries.

### Marketplace
- **Supplier Discovery** — a live map of nearby suppliers with stock, price, and ETA, ranked by the Trust Engine's own scores.
- **Logistics Tracking** — GPS position and fabrication progress, written straight into the graph.
- **Provenance Ledger** — a tamper-evident, QR-linked record for every verified delivery.

### Frontier AI
- **What-If Simulator** — simulates a decision (switch vendor, switch to air freight) before you make it, and shows the cascading cost/schedule impact.
- **Drawing Intelligence** — reads structural drawings directly into the graph, cross-checked against the BOQ — beyond OCR.
- **Vernacular AI** — fine-tuned on 12 major Indian languages (Hindi, Bengali, Telugu, Marathi, Tamil, Gujarati, Urdu, Kannada, Odia, Malayalam, Punjabi, plus English) and their English-mixed forms like Hinglish/Tanglish, where generic English-first models quietly fail.
- **Voice Agent** — places outbound calls to vendors who only respond reliably by phone.

### Insights
- **Real-Time Operations** — a live, always-on view across every site, not a nightly batch report.
- **Analytics & Budget** — on-time delivery rate, procurement cycle time, cost savings, budget variance.
- **Sustainability** — local sourcing %, emissions saved, green-certified vendor count.
- **Why Setu** — a direct comparison against spreadsheets/email and generic AI chatbots.
- **Scalability** — how prediction accuracy is designed to improve as the shared graph grows, from a single site to a federated, cross-company network.

### Two portals, one graph
Setu is split into a **Contractor / Procurement** view and a **Supplier / Vendor** view, switchable from the top bar of the demo. A supplier updating their fabrication status and a contractor watching the Risk Engine react are looking at the same event from two sides — not two disconnected systems.

---

## Running the demo (`Setu_Demo_Page.html`)

1. Open the file in any modern browser (Chrome, Edge, Safari, Firefox). No build step, no server required.
2. **Role bar** (top): switch between **Contractor** and **Supplier** — each gets its own sidebar and set of screens.
3. **Language switcher** (top right): choose from 12 major Indian languages — English, Hindi, Bengali, Telugu, Marathi, Tamil, Gujarati, Urdu, Kannada, Odia, Malayalam, or Punjabi — this controls the language of every AI response on the page.
4. **AI Suggest buttons**: found on the Control Tower, Risk/Verify/Trust engines, the What-If Simulator, Supplier Discovery, and both supplier-side AI screens. Click one to get a real, live suggestion for that specific situation.
5. **Setu Assistant** (floating button, bottom-right): a chat assistant that can answer free-form questions about the shipments, vendors, and risk scores shown in the demo.

### Important: the AI features are real, not scripted
The AI Suggest buttons and the chat assistant make live calls to Claude directly from the page (no API key required — this is handled automatically in Claude-generated artifacts). This means:
- Responses take a few seconds, because they're actually being generated, not pre-written.
- An internet connection is required for these specific features; everything else on the page works offline.
- Responses will vary slightly between clicks, the way a real assistant's would.

---

## Data shown in the demo

All vendor names, scores, shipment IDs, and figures throughout the demo and deck are **illustrative example data**, built to make the product's behavior concrete — they are not from a real project or a real vendor. The Scalability slide's accuracy figures (65% → 94%) are **modeled targets**, not measured results; say "projected" rather than "achieved" when presenting them.

---

## Tech direction (for the real system, beyond this demo)

- **Graph core:** Neo4j AuraDB — Project, PO, SKU, Vendor, Shipment, Site, Task, Certificate nodes, with relationships like `ORDERED_BY`, `DEPENDS_ON`, `DELAYS`, `VERIFIED_AGAINST`.
- **Risk Engine:** a probabilistic/forecasting model over vendor history, weather, and logistics signals — not an LLM, since this is a tabular prediction problem.
- **Verify Engine:** vision-language models for photo/certificate matching.
- **Trust & Action Engines:** LLM-based parsing, drafting, and text-to-Cypher query generation, grounded in the project's own graph rather than general knowledge.
- **Demo front end:** static HTML/CSS/JS, Font Awesome 6 icons, Big Shoulders Display + IBM Plex Sans/Mono typefaces.

## Team

**HUNTERZ**
- Rajpriyan S - CEG, Guindy

Contact: rajpriyanid@gmail.com

---

*Built for the Kaya AI IIT India Hackathon 2026 — Supply Chain track.*
