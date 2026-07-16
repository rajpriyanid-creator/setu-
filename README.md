# Setu — AI Operating System for Construction Supply Chains

**Track:** Supply Chain · **Event:** Kaya AI IIT India Hackathon 2026

> Setu ("bridge") is a live knowledge graph of a construction project's entire material lifecycle, paired with AI engines that read from and write back to that graph — for both the contractor placing orders and the supplier fulfilling them.

---

## Links

| | |
|---|---|
| 🎥 **Demo video** | [youtu.be/GPjfADO_CgA](https://youtu.be/GPjfADO_CgA) |
| 📊 **Pitch deck** | [Google Slides](https://docs.google.com/presentation/d/1UZln-6WqCKxdaNWDlVGYb-T88fRW2J18/edit?usp=drive_link&ouid=115713157852702237388&rtpof=true&sd=true) |
| 🖥️ **Live demo** | Download [`Setu-demo.html`](./Setu-demo.html) below, or open it via a Claude-hosted artifact link for full AI functionality (see [note below](#about-the-live-ai-features--read-before-demoing)) |

## Try the demo

Download [`Setu-demo.html`](./Setu-demo.html) and open it in any modern browser (Chrome, Edge, Safari, Firefox). No build step, no server, no install.



---

## What's in this repository

| File | What it is |
|---|---|
| `Setu-demo.html` | Interactive, clickable product demo — every screen, both role views, and the live AI features described below |
| `README.md` | This file |

The full platform pitch deck ([linked above](#links)) and demo video are part of the hackathon submission and live outside this repo.

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

## Using the demo

1. **Role bar** (top): switch between **Contractor** and **Supplier** — each gets its own sidebar and set of screens.
2. **Language switcher** (top right): choose from 12 major Indian languages — this controls the language of every AI response on the page.
3. **AI Suggest buttons**: found on the Control Tower, Risk/Verify/Trust engines, the What-If Simulator, Supplier Discovery, and both supplier-side AI screens.
4. **Setu Assistant** (floating button, bottom-right): a chat assistant that answers free-form questions about the shipments, vendors, and risk scores shown in the demo.

### About the live AI features — read before demoing

The AI Suggest buttons and the chat assistant call the Anthropic API (`api.anthropic.com/v1/messages`) directly from the page, with no API key embedded in the file. This is intentional: it's designed to run inside a **Claude-hosted artifact**, where Anthropic supplies the credentials for that session automatically — no key management needed.

**What this means in practice:**
- **Viewed inside a Claude.ai artifact / shared Claude link:** the AI Suggest buttons and the chat assistant work live — real, un-scripted responses, in whatever language is selected.
- **Opened as a local file, exactly as described in "Try the demo" above:** the rest of the UI (navigation, role switching, both portals, all static data) works perfectly, but the AI Suggest and chat buttons will show *"Couldn't reach the AI service"* — the request has no authorization and will be rejected.

**If you're demoing this live to judges,** use the Claude-hosted artifact link (not a downloaded local file) so the AI features actually respond. If you want the AI features to also work for anyone who downloads and opens the raw HTML, you'd need a small backend that holds your API key server-side and proxies these requests — never embed a real API key in client-side JavaScript, since anyone viewing source could extract and misuse it.

---

## Data shown in the demo

All vendor names, scores, shipment IDs, and figures throughout the demo are **illustrative example data**, built to make the product's behavior concrete — they are not from a real project or a real vendor. The Scalability screen's accuracy figures (65% → 94%) are **modeled targets**, not measured results — say "projected" rather than "achieved" when presenting them.

---

## Tech direction (for the real system, beyond this demo)

- **Graph core:** Neo4j AuraDB — Project, PO, SKU, Vendor, Shipment, Site, Task, Certificate nodes, with relationships like `ORDERED_BY`, `DEPENDS_ON`, `DELAYS`, `VERIFIED_AGAINST`.
- **Risk Engine:** a probabilistic/forecasting model over vendor history, weather, and logistics signals — not an LLM, since this is a tabular prediction problem.
- **Verify Engine:** vision-language models for photo/certificate matching.
- **Trust & Action Engines:** LLM-based parsing, drafting, and text-to-Cypher query generation, grounded in the project's own graph rather than general knowledge.
- **Demo front end:** static HTML/CSS/JS, Font Awesome 6 icons, Big Shoulders Display + IBM Plex Sans/Mono typefaces.

---

## Team

**HUNTERZ**
- Rajpriyan S — CEG, Guindy

Contact: rajpriyanid@gmail.com

---

*Built for the Kaya AI IIT India Hackathon 2026 — Supply Chain track.*
