# 🚀 YouTube Viral Content Automation with n8n

An end‑to‑end automation system that scrapes trending YouTube videos, scores their viral potential, generates AI‑powered scripts and titles, and delivers real‑time alerts via Telegram.

## 📌 Features
- **Apify Scraping** – Fetches latest videos by keyword every 8 hours.
- **Viral Detection Algorithm** – Calculates outlier score, velocity, and momentum.
- **AI Analysis** – Gemini identifies trending angles; OpenAI analyzes thumbnails and generates titles.
- **Script Generation** – Creates complete YouTube Short scripts with hooks and CTAs.
- **Telegram Alerts** – Real‑time validation, daily reports, and A/B performance summaries.
- **Google Sheets Logging** – Full historical tracking and dashboarding.

## 🧰 Tech Stack
- n8n (Workflow Automation)
- Apify YouTube Scrapers
- Google Gemini & OpenAI GPT‑4o
- Telegram Bot API
- Google Sheets API

## 🚦 How to Use
1. Import `workflow.json` into your n8n instance.
2. Add your API keys for Apify, OpenAI, Gemini, Telegram, and Google Sheets.
3. Activate the workflow and optionally trigger via form or schedule.
   
## 📊 Workflow Architecture Diagram

```mermaid
flowchart TB
    subgraph Triggers["⏰ Triggers"]
        S1["Every 8 Hours"]
        S2["Daily at 9 AM"]
        S3["Daily at 6 PM"]
        S4["Weekly A/B Report"]
        T1["Telegram Bot"]
        F1["Form Trigger"]
    end

    subgraph DataIngestion["📡 Data Ingestion"]
        A1["Apify Keyword Search"]
        A2["Ad‑hoc Apify Search"]
        A3["Read My Videos Sheet"]
        T2["Transform Apify Data"]
    end

    subgraph ViralDetection["🔍 Viral Detection Pipeline"]
        F2["Pre‑Filter Noise"]
        C1["Calculate Outlier Score"]
        C2["Calculate Viral Metrics"]
        C3["Apply Adaptive Scoring"]
        I1["Top 10% Percentile?"]
    end

    subgraph AIAnalysis["🧠 AI Analysis"]
        G1["Gemini: Viral Potential"]
        O1["OpenAI: Thumbnail Desc"]
        H1["Fetch Transcript"]
        O2["OpenAI: Title Gen"]
        G2["Gemini: Script Gen"]
    end

    subgraph Outputs["📤 Outputs & Logging"]
        GS1["Save to Sheets (Viral Videos)"]
        GS2["Save Scripts"]
        GS3["Performance Tracking"]
        GS4["A/B Report History"]
        TG1["Telegram: Filtered Videos"]
        TG2["Telegram: Idea Validation"]
        TG3["Telegram: Daily Report"]
        TG4["Telegram: A/B Report"]
        TG5["Telegram: Performance"]
    end

    S1 --> A1
    F1 --> A2
    A1 & A2 --> T2 --> F2 --> C1 --> C2 --> C3
    C3 --> TG1 --> GS1 --> I1
    I1 -- Yes --> G1 --> GS1 --> O1 --> H1 --> O2 --> G2 --> GS2
    I1 -- No --> GS1

    S2 --> A3 --> GS3 --> TG5

    S3 --> GS1 --> TG3

    S4 --> GS1 & GS2 & GS3 --> TG4 --> GS4

    T1 --> TG2

    style Triggers fill:#f9f,stroke:#333,stroke-width:2px
    style DataIngestion fill:#e1f5fe,stroke:#333
    style ViralDetection fill:#fff3e0,stroke:#333
    style AIAnalysis fill:#e8f5e9,stroke:#333
    style Outputs fill:#f3e5f5,stroke:#333
```

## 📸 Screenshots
*(Add images of the workflow canvas and Telegram messages)*

## 📄 License
MIT
