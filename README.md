# Sentinel — AI-Driven Energy Supply Chain Resilience

**ET AI Hackathon 2026 · Problem Statement 2: AI-Driven Energy Supply Chain Resilience for Import-Dependent Economies**

## What it does

Sentinel is an AI-powered command-center dashboard for India's crude oil supply resilience:

- **Live Disruption Map** — tanker positions and risk status along the Hormuz–India corridor
- **Dark Fleet Detection** — flags vessels with AIS signal gaps consistent with sanction-evasion / dark-fleet behaviour, with an explainable 4-step detection chain
- **Panic Index** — search and social sentiment tracked as a leading indicator of fuel-buying panic, broken down by city
- **AI Reasoning Engine** — the core AI feature. A planner describes a real-world disruption scenario in plain language, and Sentinel calls a live LLM to generate three ranked alternate-supplier recommendations, each with a confidence score and full "why this ranking" reasoning
- **SPR Optimisation** — models India's ~9.5-day Strategic Petroleum Reserve under different drawdown strategies over a 15-day window
- **Data Sources** — maps every module to the real public/commercial API it would run on in production

## How the AI reasoning works

Each scenario is scored across 5 weighted factors: tanker availability, price competitiveness, sanction exposure, transit reliability, and refinery compatibility. The model returns structured JSON which the frontend renders live — no hardcoded fallback data is shown once a live scenario is run successfully.

## Tech stack

- Frontend: HTML / CSS / vanilla JS, Chart.js
- AI: A hosted LLM API, called directly from the browser
- Backend: none — this is a single self-contained HTML file, no build step or server required

## Responsible AI

Every recommendation is advisory only — a human operator reviews the reasoning trail before any real action is taken. This is a decision-support tool, not an autonomous purchasing agent. Factor weightings are shown and are adjustable by a human operator rather than fixed constants.

## Running locally

Open `sentinel-energy-resilience-prototype-v2.html` directly in a browser. All views load with simulated data by default. To see a real result, go to the **AI Reasoning Engine** tab, describe a scenario, and click **Run Live AI Analysis** — this calls the LLM API live (needs network access).

## Files

| File | Description |
|---|---|
| `sentinel-energy-resilience-prototype-v2.html` | The full working prototype |
| `Sentinel_Technical_Document.pdf` | Detailed technical writeup — architecture, real-world data source mapping, judging criteria alignment, limitations and roadmap |

## Status

All data feeds shown are simulated for demo purposes except the AI Reasoning Engine, which is genuinely live. See the Data Sources tab in the app, or Section 5 of the technical document, for exactly what each module would connect to in a real deployment.
