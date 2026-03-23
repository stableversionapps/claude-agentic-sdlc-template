---
name: ai-features
description: Implements AI-powered features using Claude API and on-device ML. Covers chat, classification, insights, document processing, and NL search. Privacy-first with graceful degradation.
argument-hint: "chat|classify|insights|ocr|search"
---

# AI Features

Builds privacy-first AI features using Claude API and on-device processing.

## Usage
`/ai-features chat` — Build/enhance AI chat assistant
`/ai-features classify` — Smart classification system
`/ai-features insights` — Predictive insights engine
`/ai-features ocr` — Document OCR pipeline
`/ai-features search` — Natural language search

## Features

### AI Chat Assistant (Claude API)
- Natural language queries against local data
- Multi-turn with persistent context
- Anonymized data only — never raw personal details

### Smart Classification
- On-device keyword matching first (instant, offline)
- Claude-powered classification for ambiguous inputs
- Learn from user corrections (local feedback loop)
- Auto-assign above 90% confidence, suggest below

### Predictive Insights
- Trend forecasting based on historical data
- Anomaly detection
- Risk/threshold alerts
- Opportunity detection
- Pattern recognition

### Document OCR
- Camera/upload -> On-device OCR -> Claude extraction -> Structured data
- 100% on-device OCR processing
- Claude for structured data extraction from text

### NL Search
- Natural language queries parsed by Claude
- Intent -> database query -> results
- Feels like conversation, not database search

## Privacy Rules (MANDATORY)

### NEVER send to Claude API:
- Raw personal identifiers
- Account numbers or credentials
- Specific location data
- Unprocessed personal data

### SAFE to send:
- Aggregated totals and summaries
- Anonymized patterns
- Category names and thresholds
- General domain questions

## Implementation Checklist
- [ ] Privacy-safe prompt construction
- [ ] Proper error handling (network, rate limit, API error)
- [ ] Offline fallback (rule-based alternative)
- [ ] Loading state in UI
- [ ] Response caching where appropriate
- [ ] Rate limiting (client-side throttle)
- [ ] Cost tracking (token usage)
- [ ] User can disable AI features entirely
- [ ] Daily API call budget

## Prompt Engineering
- System prompt establishes domain-appropriate persona
- Request structured JSON responses for reliable parsing
- Keep prompts concise to minimize token usage
- Temperature: 0.3 for analysis, 0.7 for conversational
