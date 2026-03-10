# Agent Examples

Ready-to-use agent recipes for the most common content and marketing workflows. Each example lists the exact steps to add, how to configure them, and what you'll get out.

---

## Example 1 — Blog Article Pipeline

**What it does:** Takes a topic, researches keywords and related questions, generates a content brief, and writes a full draft article.

**Steps:**

1. **DataForSEO** — keyword research
   - Keyword: `{{topic}}`
   - Limit: 25

2. **People Also Search For** — find related angles
   - Query: `{{topic}}`

3. **Get Title Suggestions** — decide the best angle
   - Topic: `{{topic}}`
   - Count: 10
   - Tone: informational

4. **Content Brief** — structure the article
   - Topic: `{{topic}}`
   - Tone: informational

5. **Draft Article** — write it
   - Brief: `{{step_4.output}}`
   - Word count: 2000
   - Tone: informational

**Input fields to add:** `Topic`

**Output:** A 2,000-word article draft in Markdown, ready for editing and publishing.

---

## Example 2 — AI Search Optimisation Article

**What it does:** Researches what AI assistants currently say about a topic using Perplexity, then writes a long-form article structured to win AI search answers.

**Steps:**

1. **Perplexity Search** — see what AI currently says
   - Prompt: `What do people want to know about {{topic}}? What are the key questions and answers?`
   - Model: Sonar Pro

2. **Google SERP Results** — see who ranks today
   - Query: `{{topic}}`
   - Results: 10

3. **Content Brief** — structure for AI search
   - Topic: `Create a content brief for an article about {{topic}} optimised to rank in AI search engines like ChatGPT, Perplexity, and Google AI Overviews. Base the structure on this research: {{step_1.output}}`

4. **Generate Article** — write the full piece
   - Brief: `{{step_3.output}}`
   - Word count: 2500
   - AI Model: GPT-4o

**Input fields to add:** `Topic`

**Output:** A long-form article built around the questions and answers that AI assistants surface for your topic.

---

## Example 3 — Competitor Page Analysis

**What it does:** Crawls a competitor's page, summarises their content angle, and suggests how you could write a better version.

**Steps:**

1. **Get Web Content** — crawl their page
   - Page URL: `{{competitor_url}}`
   - Extract main content: Yes

2. **Prompt LLM** — analyse it
   - Prompt: `Analyse this competitor article and identify: (1) their main angle and argument, (2) gaps and topics they missed, (3) weaknesses in their coverage. Article: {{step_1.output}}`
   - Model: GPT-4o Mini

3. **Content Brief** — write a better brief
   - Topic: `Write a content brief for an article on the same topic as this competitor article that is significantly better. Competitor analysis: {{step_2.output}}`

4. **Draft Article**
   - Brief: `{{step_3.output}}`
   - Word count: 2000

**Input fields to add:** `Competitor URL`

**Output:** An analysis of the competitor's content and a draft article that improves on it.

---

## Example 4 — Weekly SEO Report to Slack

**What it does:** Pulls your GSC keyword rankings and GA4 traffic data, summarises the highlights, and sends the summary to a Slack channel every week.

**Steps:**

1. **Get GSC Rankings** — pull keyword positions
   - Brand: (select your GSC connection)
   - Date range: 7 days

2. **Get GA4 Data** — pull traffic metrics
   - Brand: (select your GA4 connection)
   - Date range: 7 days

3. **Prompt LLM** — write the summary
   - Prompt: `You are a marketing analyst. Write a concise weekly SEO performance summary (max 300 words) suitable for a Slack message. Cover: top performing pages, notable keyword movements, AI referral traffic trends. Data: GSC rankings: {{step_1.output}} GA4 traffic: {{step_2.output}}`
   - Model: GPT-4o Mini

4. **Slack Notify** — send it
   - Message: `{{step_3.output}}`
   - Brand: (select your Slack connection)

**Input fields to add:** None — schedule this agent to run weekly via the trigger settings.

**Output:** A plain-English summary of your SEO performance delivered straight to your Slack channel.

---

## Example 5 — Content to CMS Pipeline

**What it does:** Generates a finished article and publishes it as a draft directly to your Sanity CMS.

**Steps:**

1. **Content Brief**
   - Topic: `{{topic}}`
   - Target audience: `{{audience}}`
   - Tone: conversational

2. **Generate Article**
   - Brief: `{{step_1.output}}`
   - Word count: 1500
   - AI Model: GPT-4o

3. **Wait for Approval** — human review before publishing
   - Instructions: `Review this article draft before it goes to Sanity. The topic is {{topic}}.`
   - Attach: `{{step_2.output}}`
   - Timeout: 48 hours

4. **Sanity Write** — publish to CMS
   - Content: `{{step_2.output}}`
   - Document type: post
   - Title: (AI will infer from the article)

**Input fields to add:** `Topic`, `Audience`

**Output:** A published draft in Sanity, with a human approval gate before it lands in the CMS.

---

## Example 6 — Knowledge Base Builder

**What it does:** Crawls a URL, extracts the content, and saves it to your knowledge base so future agents can reference it.

**Steps:**

1. **Get Web Content**
   - Page URL: `{{url}}`
   - Extract main content: Yes

2. **Prompt LLM** — clean and summarise
   - Prompt: `Summarise this page into a concise, well-structured reference document. Include key facts, claims, and data points. Source: {{step_1.output}}`
   - Model: GPT-4o Mini

3. **Upload to Knowledge Base**
   - Content: `{{step_2.output}}`
   - Knowledge base: (select your knowledge base)

**Input fields to add:** `URL`

**Output:** The page's content is stored in your knowledge base and available to all future agents.

---

## Tips for building your own

- **Chain outputs.** The most powerful agents pass one step's output into the next. Use `{{step_N.output}}` in your prompts and configurations.
- **Start with research, end with content.** A good pattern: research steps first (SERP, Perplexity, DataForSEO), then a brief step, then the article step.
- **Use Agentic Mode for exploration.** When you're not sure of the right steps, use [Agentic Mode](agentic-mode.md) and let the AI figure out the path.
- **Add approval gates for anything customer-facing.** Always put a Wait for Approval step before Slack notifications to customers or CMS publishes.
