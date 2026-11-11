---
status: Active
project: Vesto
---
The goal: after Vesto v1, I can walk an interviewer through every piece of it, in my own words, without notes. I built it myself; Claude helped me learn and review it. Each Sunday I explain what I built this week here, out loud first, then written down.

## The checklist (can I explain this for 2 minutes?)
- [ ] What Vesto is, who it's for, and why the pitch gate exists
- [ ] The architecture: what runs where, how a request flows from the browser to Postgres and the LLM and back
- [ ] The schema: every table, why it exists, and how pitches link to me or an agent
- [ ] Where price data comes from, how it gets loaded, and what happens when the API fails
- [ ] How the AI fund manager review works: the prompt, the structured output, how the score is calculated
- [ ] How an analyst agent works: its tools, how tool calling works, how it decides what to pitch
- [ ] Why the 3 agents behave differently (value vs momentum vs contrarian)
- [ ] How the scorecard measures a thesis being "right," and the weaknesses of that measurement
- [ ] Cost and latency per pitch: how I measure them and what I'd do to cut them
- [ ] Docker and docker compose: what each container does
- [ ] CI: what runs on every push and why
- [ ] Deployment: where it's hosted and how a change gets live
- [ ] One thing I'd do differently and one thing I'd build next

## Weekly log
### Week 1 (10/25)
- What I built:
- How it works, in my words:
- What I still can't explain:
