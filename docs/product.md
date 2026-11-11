---
status: Active
project: Vesto
due: 2026-10-19
---
Part of [[Project Bootcamp]] (Phase 1). Answer in my own words, rough is fine. This becomes the README intro and my interview answer to "what is it?"

## 1. Who is it for?
College students and early investors who want to learn to invest but end up buying stuff off TikTok or a friend's tip without a real reason.

## 2. Core loop
1. Pick a stock and look at its real price history and fundamentals
2. Write a pitch: buy or sell, why, and what would prove me wrong
3. The AI fund manager scores the pitch. I only trade (paper money) if it's approved
4. My 3 analyst agents (value, momentum, contrarian) pitch their own trades through the same gate
5. As real prices move, Vesto tracks whose theses worked: mine or the agents'
6. I review the scorecard and the agents' reasoning to see what I'm missing

## 3. v1 scope
**In:**
- Real daily prices for ~20 stocks
- My pitch, AI fund manager review, paper trades
- 3 fixed analyst agents using tool calling
- Scorecard: hit rate for me and each agent, plus cost and latency per pitch
- Clean, polished UI (see UI/UX below)
- Docker, CI, deployed, README

**Out (for now):**
- Prediction markets and the C++ exchange (spring)
- Custom agents
- Learn modules and 10-K explainer
- Real money, social features, mobile app

## 4. Success metric
**5-day hit rate:** % of pitches (mine and each agent's) where the stock beat the S&P 500 over the next 5 trading days, in the direction pitched.
- Why this one: objective, only needs daily prices I'm already storing, and results come in after a week, so I'll have real numbers before 11/8
- Supporting numbers on the scorecard: average fund manager score, cost and latency per pitch
- Known weakness (interview answer): 5 days is noisy and short-term. Later I can add longer horizons (30 days) once there's more history

## Data (picked 10/19)
- **Prices:** Massive (formerly Polygon.io) free Basic plan. End-of-day prices, ~2 years of history, 5 requests/min. The grouped daily endpoint returns every ticker in one call
- **Fundamentals (for the value agent):** Finnhub free tier, ~60 requests/min. Confirm the basic financials endpoint is free when signing up
- **Benchmark:** SPY, for the 5-day hit rate
- **Tickers (top 20 S&P 500 companies by weight, as of 10/15/2026, one Alphabet class):** NVDA, AAPL, MSFT, AMZN, GOOGL, AVGO, META, MU, TSLA, LLY, BRK.B, AMD, JPM, XOM, V, JNJ, WMT, ABBV, MA, INTC
- Gotcha: Berkshire's ticker is written differently across APIs (BRK.B vs BRK-B). Handle it in one place

## UI/UX
Goal: it should feel like a real product a recruiter wants to click around in, not a hackathon demo.
- Screens for v1: dashboard (scorecard + positions), stock page (chart + key numbers), pitch composer, review result, agent pitch feed
- Sketch the screens before building them (Figma, paper, or a Claude mockup)
- Use shadcn/ui + Tailwind with one consistent design system (colors, type, spacing) set up in week 1
- Empty, loading, and error states on every screen
- Week 3 includes a polish pass and a README GIF/screenshot

## Decisions so far (10/19)
- Direction: a trainer for making decisions with real market data. I'm the portfolio manager, AI analyst agents pitch alongside me, and every thesis gets scored once the outcome is known. See [[Vesto - Market Research]]
- Agents: fixed styles for v1 (e.g. value, momentum, contrarian). Custom agents come later
- Prediction markets: sports first (fast feedback), awards later. Paper money only, framed as forecasting with calibration scores
- C++: build the prediction market exchange (order book + matching engine), with a market-maker bot pricing off live Kalshi/Polymarket odds
- Priority (decided after the recruiting check): v1 is an applied AI project for FDE / applied AI roles. Agents with tool calling on real data, structured pitches, the AI fund manager as the evaluator, and a scorecard. That's the resume headline. The C++ exchange is a spring bonus, not something the resume depends on
- I build it myself and must be able to walk through every piece: [[Vesto - Walkthrough]]
- Phasing: v1 = stock thesis desk + agents + scorecard. v1.5 = C++ exchange + sports markets. Later = awards, agent leaderboard, LLM Gateway routing

## Open questions
- 
