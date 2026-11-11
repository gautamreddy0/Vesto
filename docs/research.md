---
status: Active
project: Vesto
created: 2026-10-19
---
Research for [[Vesto - Product Definition]]. Three areas: AI investment analysis, AI agents that trade, and prediction markets. Researched 10/19/2026.

## TL;DR
- **Agents that trade are already shipping at big brokers.** Robinhood, Public, Webull and Alpaca all let AI agents place real orders now. "Agents invest for you" alone is not a differentiator anymore.
- **What's missing is accountability.** Robinhood says it doesn't supervise or audit third-party agents, and the user carries the risk. The public AI trading contests show models acting erratically. Nobody makes agents *justify* trades in a way a person can review and score.
- **That's Vesto's existing idea.** The pitch gate (no trade without a reviewed thesis) works for agents too. Vesto can become the place where humans and agents both have to pitch, and every thesis gets tracked against what actually happened.
- **Prediction markets are huge but mostly sports.** About $45 to 53B/month combined volume in summer 2026, roughly 80% sports. Legally messy at the state level. Best use for Vesto: market-implied probabilities as an analysis input, plus paper-traded event contracts, not real money.
- **Stay paper money.** Managing other people's money with agents is investment adviser territory (Autopilot, for example, is an SEC-registered RIA). Paper trading on real data keeps the project buildable and still impressive.

## 1. AI investment analysis tools
| Tool | What it does | Gap Vesto could fill |
|---|---|---|
| Fiscal.ai (FinChat) | Plain-English Q&A on fundamentals and KPIs | Doesn't judge *your* reasoning |
| Koyfin / TIKR | Terminal-style data, estimates, screeners ($0 to ~$120/mo) | Data workbench, light AI |
| Perplexity Finance | Fast cited answers | Shallow, doesn't see your portfolio |
| Seeking Alpha | Contributor articles + quant grades + AI bull/bear summaries | Quality varies |
| AlphaSense | Filings, transcripts, expert calls for institutions | Enterprise only |
| Danelfin / Kavout / Zen Ratings | Single AI score per stock | Score, not reasoning |
| ARIA Analyst / AlphaVue | Multiple agents argue bull vs bear, or split fundamentals/news/technicals | Newer, closest to the "agent team" idea |
| Walnut | Reads your holdings, keep/trim/exit, never trades | Read-only by design |

Pattern: tools either give you **data** or give you **an answer**. Almost none grade **your thinking** or track whether a thesis was right later.

## 2. AI agents that trade
| Platform | Agent autonomy | Guardrails |
|---|---|---|
| Robinhood Agents (in-app) + Agentic Trading MCP (beta May 2026) | Agents place stock, options, crypto orders | Separate "Agentic account," approvals on by default, but user can turn them off. Robinhood doesn't audit third-party agents |
| Robinhood Cortex | Research digests only, no orders | Gold members |
| Public "Agentic Brokerage" (Mar 2026) | Hosted MCP for Claude/ChatGPT/Perplexity, places orders | Not detailed |
| Webull MCP (Aug 2026) | Places orders within limits | Order caps, read-only mode |
| Interactive Brokers | Drafts orders only | You submit every order |
| Alpaca | Fully automated via API/MCP | Paper trading sandbox, you manage keys |
| Composer | No-code / AI-built rule strategies ("symphonies"), backtest, auto-rebalance | Rules-based, overfitting risk |
| Autopilot | Copy portfolios of politicians, funds, etc. | SEC-registered RIA |

**Alpha Arena (Nof1, Oct to Nov 2025):** six frontier LLMs got $10k each to trade crypto perps with real money, all trades public. Results swung hard. Some models lost a large chunk, and a Qwen model reportedly won with about +22%. Lessons from coverage: opaque reasoning, hallucination risk, and agents on the same base model may all react the same way.

Takeaway: the industry is solving **access** (agents can trade). The open problem is **oversight**: is this agent's reasoning any good, and is it consistent over time?

## 3. Prediction markets
- **Volume:** combined Kalshi + Polymarket went from about $26B (May 2026) to $53B (July, World Cup) to about $45B (Aug). Kalshi holds ~82% share as of August.
- **Mix:** sports is ~78% of Kalshi and ~82% of Polymarket July volume. Crypto is #2 on Kalshi. Econ/finance/weather markets are small but exist.
- **Distribution:** Robinhood, Interactive Brokers (ForecastEx, Kalshi, CME contracts), Crypto.com, Cantor (institutional Kalshi block trading) all offer event contracts.
- **Legal:** 9th Circuit (Aug 28, 2026) said sports event contracts are bets under state law. 3rd Circuit said the opposite in April. Supreme Court review likely. A dozen+ states have moved against Kalshi/Polymarket.
- **AI forecasting:** ForecastBench shows LLMs closing in on human superforecasters (gap ~0.017 Brier in Jan 2026, parity projected around late 2026). Adjusting forecasts toward market prices improved scores. Prophet Arena (ICLR 2026) benchmarks LLMs against live prediction markets.
- **APIs:** Kalshi market data is free and public (events, markets, orderbook, candlesticks). Kalshi has a paper-money demo environment. Polymarket also has public APIs.

## What this means for Vesto (options to decide on)
**A. The thesis desk (recommended direction to pressure-test).** You're the portfolio manager. You and your AI agents both pitch trades. Every pitch, human or agent, goes through the AI fund manager gate, gets a score, and is tracked against reality. Over time you get a leaderboard: whose theses actually work, and is the agent better than me?
- Analysis = research view per stock, including what prediction markets imply (e.g. Fed cut odds, CPI ranges)
- Agents = analyst agents (e.g. value, momentum, macro) that propose pitches you approve or reject
- Prediction markets = tradable on paper as theses with a probability, and a data input

**B. Analysis-first.** Mostly a research tool, agents and prediction markets as features. Safer, less unique.

**C. Agent arena.** Agents compete with paper money and public reasoning, users follow or copy. Fun, but close to Alpha Arena and less "yours."

## Scope warning
Three products in one is too much for a December deadline. Pick one core loop for v1, design the data model so the others plug in later.

## Things to check yourself
- Is a market data API you want free for ~20 tickers daily? (Alpaca paper, Polygon, Alpha Vantage, etc.)
- Kalshi demo account + API key
- Read Robinhood's Agentic Trading guardrails page for ideas on approvals and account separation

## Sources
- [Walnut: Robinhood AI features](https://walnutinvest.com/help/robinhood-ai) (note: Walnut is a competitor)
- [Walnut: Best agentic trading apps 2026](https://walnutinvest.com/resources/best-agentic-trading-apps)
- [Walnut: Best AI stock research tools 2026](https://walnutinvest.com/resources/best-ai-stock-research-tools)
- [Walnut: Composer review](https://walnutinvest.com/resources/composer-review)
- [CNBC: AI agents built to trade 24/7 (Jul 2026)](https://www.cnbc.com/2026/07/28/ai-agents-build-to-trade-24/7-the-future-of-wall-street.html)
- [Pew: prediction market volume doubled May to July 2026](https://www.pewresearch.org/short-reads/2026/09/23/prediction-markets-trading-volume-doubled-between-may-and-july-largely-driven-by-sports/)
- [Shift Markets: Prediction Markets Brief, Aug 2026](https://www.shiftmarkets.com/prediction-markets-brief/august-2026)
- [Token Metrics: Prediction markets go mainstream](https://tokenmetrics.com/blog/prediction-markets-go-mainstream-2026/)
- [Forecasting Research Institute: LLMs closing the gap on superforecasters](https://forecastingresearch.substack.com/p/llms-are-closing-the-gap-on-human)
- [Prophet Arena paper](https://arxiv.org/pdf/2510.17638)
- [Decrypt: Alpha Arena results](https://decrypt.co/345006/ai-crypto-trading-showdown-deepseek-grok-winning-gemini-implodes)
- [Jiemian: Qwen wins Alpha Arena](https://en.jiemian.com/article/13592098.html)
- [Kalshi API getting started](https://prediction.com/blog/kalshi-api-getting-started-guide)
- [Autopilot RIA profile](https://altss.com/profile/autopilot)
