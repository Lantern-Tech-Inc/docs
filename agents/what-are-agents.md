# What are Agents?

Agents are automated workflows that do your marketing research and content work for you. Instead of manually switching between tools, pulling data, writing briefs, and drafting articles, you describe what you want done and Lantern handles it — step by step, start to finish.

## The core idea

Think of an Agent as a recipe. You pick a series of steps, connect them together, and hit run. Each step does one specific thing — search the web, generate a title, write a draft — and passes its output to the next step automatically.

You can also use **Agentic Mode**, where the AI reads your goal and decides which steps to use, in what order, without you having to define each one manually.

## What agents are good for

| Use case | What the agent does |
|----------|-------------------|
| Blog article creation | Researches keywords, writes a brief, drafts the full article |
| Content gap analysis | Pulls your GSC rankings, identifies low-hanging fruit, suggests titles |
| Competitor research | Crawls competitor pages, summarises their content angle |
| AI search optimisation | Researches what AI assistants surface for your topic, drafts content structured to win those answers |
| Publishing pipeline | Generates content and publishes directly to Sanity CMS |
| Weekly reporting | Pulls GA4 and GSC data, writes a summary, sends to Slack |

## How agents run

When you trigger an agent, it runs in the background on Lantern's servers. You do not need to keep your browser open. When it finishes you get a notification (Slack or email depending on your setup) and you can review the full conversation and outputs in the **Run History** tab.

Each run is logged with:
- Every tool call and its result
- The AI's reasoning at each step
- The full output (article draft, brief, keyword list etc.)
- Duration and status

![Lantern Agents overview](https://cdn.asklantern.com/snapshots.png)

## The difference between Workflow mode and Agentic mode

**Workflow mode** — you define every step in a fixed sequence. The agent always runs those exact steps in that exact order. Great for repeatable, predictable processes.

**Agentic mode** — you give the AI a goal in plain English (e.g. "Write a 2,000-word blog post about agentic marketing that ranks in AI search"). The AI reads the tools available to it and decides which ones to use, how many times, and in what order. It adapts based on what each tool returns. Great for one-off research tasks or when the path to the goal isn't always the same.
