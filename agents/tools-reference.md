# Tools Reference

Every tool available in the Lantern Agent Builder, what it does, and what you can configure.

---

## AI

### Prompt LLM

Send a custom prompt to any AI model and get a generated response back.

**When to use it:** Any time you need the AI to analyse, summarise, rewrite, classify, or generate text based on inputs you provide.

| Setting | What it does |
|---------|-------------|
| Prompt | Your instruction to the AI. Use `{{variable}}` to include outputs from previous steps. |
| Model | Choose which AI model to use (GPT-4o, GPT-4o Mini, Gemini Pro, etc.) |

**Output:** The AI's text response.

---

## Web Research

### Get Sitemap

Fetches a list of all URLs from an XML sitemap file.

**When to use it:** When you want to inventory all pages on a website before crawling or analysing them.

| Setting | What it does |
|---------|-------------|
| Sitemap URL | The full URL to the sitemap.xml file |

**Output:** A list of URLs found in the sitemap.

---

### Get Pages from Sitemap

Like Get Sitemap but with filtering — retrieve and filter URLs from a sitemap based on patterns you specify.

**When to use it:** When you only want URLs that match a certain path pattern (e.g. only blog posts).

| Setting | What it does |
|---------|-------------|
| Sitemap URL | The full URL to the sitemap.xml file |
| Filter | Optional URL path filter |

**Output:** A filtered list of URLs.

---

### Get Web Content

Crawls a web page and extracts its text content.

**When to use it:** When you need to read what's on a specific page — competitor analysis, reading source material, scraping data.

| Setting | What it does |
|---------|-------------|
| Page URL | The URL to crawl |
| Scraping method | Quick Capture (fast) or Full Render (runs JavaScript) |
| Output format | Text or Markdown |
| Extract main content | Strip navigation, footers, and boilerplate |

**Output:** The extracted text content of the page.

---

### Perplexity Search

Search the web using Perplexity AI, which returns summarised answers with cited sources.

**When to use it:** When you want to research a topic and get a synthesised answer — great for understanding what AI search engines currently know and how they answer questions.

| Setting | What it does |
|---------|-------------|
| Prompt | Your search query or question |
| Model | Sonar Pro (most capable) or Sonar (faster) |

**Output:** An AI-generated answer with source citations.

---

### Google SERP Results

Fetches the current Google search results for a keyword.

**When to use it:** To see which pages currently rank for a given query, or to understand the competitive landscape before writing content.

| Setting | What it does |
|---------|-------------|
| Search query | The keyword to search |
| Number of results | How many results to return (up to 100) |
| Country | Target country for location-specific results |
| Language | Target language |

**Output:** A list of ranking pages with their titles, URLs, and snippets.

---

### People Also Search For

Fetches the "People also search for" related queries from Google for a given keyword.

**When to use it:** To discover related topics, sub-topics, and semantic variations of your target keyword — useful for building out content clusters.

| Setting | What it does |
|---------|-------------|
| Search query | Your seed keyword |
| Country | Target country |
| Language | Target language |

**Output:** A list of related search queries.

---

## SEO Research

### DataForSEO

Retrieves keyword search volume, competition level, and CPC data from Google Ads via the DataForSEO API.

**When to use it:** When you want real search volume numbers before committing to a content topic.

> **Note:** DataForSEO draws on Google Ads data. Very new or niche terms (e.g. emerging tech concepts) may return no data because Google Ads has not indexed enough searches for them yet. Try broadening the keyword in that case.

| Setting | What it does |
|---------|-------------|
| Keyword | The seed keyword to research |
| Location | Target country (default: United States) |
| Language | Target language (default: English) |
| Limit | Maximum number of keyword ideas to return |

**Output:** A table of keyword ideas with search volume, competition score, competition level, and estimated CPC.

---

## Content Generation

### Get Title Suggestions

Generates a list of potential article titles for a given topic.

**When to use it:** Early in a content workflow, before writing a brief or draft, to decide which angle to take.

| Setting | What it does |
|---------|-------------|
| Topic | The subject you want titles for |
| Count | How many title suggestions to generate |
| Tone | Informational, conversational, persuasive, etc. |
| AI Model | Which model to use |

**Output:** A numbered list of title options.

---

### Content Brief

Creates a structured content brief for an article — covering target audience, key angles, suggested headings, and recommended sources.

**When to use it:** Before writing a draft. A good brief dramatically improves the quality of the generated article.

| Setting | What it does |
|---------|-------------|
| Topic | The subject to write about |
| Target audience | Who the article is for |
| Tone | The voice and style |
| AI Model | Which model to use |

**Output:** A structured brief with headings, talking points, and guidance for the writer (or the Draft Article step).

---

### Draft Article

Writes a first draft of an article based on a brief you provide.

**When to use it:** When you have a content brief (either from the Content Brief step or written manually) and want a full draft.

| Setting | What it does |
|---------|-------------|
| Brief | The content brief — use `{{step_N.output}}` to pull from a previous step |
| Word count | Target length |
| Tone | Voice and style |
| AI Model | Which model to use |

**Output:** A complete article draft in Markdown.

---

### Generate Article

Produces a complete, polished article in a single step — no separate brief needed.

**When to use it:** When speed matters more than maximum control, or as an end-of-pipeline step that receives rich context from multiple preceding steps.

| Setting | What it does |
|---------|-------------|
| Brief | Instructions and context for the article |
| Word count | Target length |
| Tone | Voice and style |
| AI Model | Which model to use (GPT-4o recommended for long-form) |

**Output:** A complete article in Markdown.

---

## Knowledge Base

### Search Knowledge Base

Searches your Lantern knowledge base for content related to a query.

**When to use it:** When your agent needs to reference your own saved research, past articles, or brand guidelines before generating new content.

| Setting | What it does |
|---------|-------------|
| Query | What to search for |
| Knowledge base | Which knowledge base to search |

**Output:** Relevant excerpts retrieved from your knowledge base.

---

### Upload to Knowledge Base

Saves content into your knowledge base so it can be retrieved by future agents.

**When to use it:** At the end of a research pipeline — store everything the agent found so future agents can use it without re-running the research.

| Setting | What it does |
|---------|-------------|
| Content | The text to save — use `{{step_N.output}}` to save a previous step's output |
| Knowledge base | Which knowledge base to store it in |

**Output:** Confirmation that the content was saved.

---

## Integrations

### Get GA4 Data

Pulls sessions, pageviews, and AI referral metrics from your connected Google Analytics 4 property.

**When to use it:** When building a reporting agent, or when you want to feed real performance data into a content strategy prompt.

| Setting | What it does |
|---------|-------------|
| Brand | The connected GA4 property to pull from |
| Date range | How far back to look (7 days, 28 days, 3 months, etc.) |

**Output:** A data object with traffic metrics by page and channel.

---

### Get GSC Rankings

Fetches keyword positions, impressions, clicks, and CTR from your connected Google Search Console property.

**When to use it:** To find which keywords you're ranking for (and where), identify quick-win opportunities, or feed ranking data into a content gap analysis.

| Setting | What it does |
|---------|-------------|
| Brand | The connected GSC property to pull from |
| Query filter | Optional — filter to keywords containing this string |

**Output:** A list of keywords with position, impressions, clicks, and CTR.

---

### Slack Notify

Sends a message to a Slack channel.

**When to use it:** At the end of a workflow to notify your team that a run is complete, or to send a summary to a channel for review.

| Setting | What it does |
|---------|-------------|
| Brand | The connected Slack workspace |
| Message | The message text — use `{{step_N.output}}` to include content from the run |

**Output:** Confirmation that the message was sent.

---

### Sanity Write

Creates or updates a draft document in your Sanity Studio dataset.

**When to use it:** As the final step in a content pipeline to push a generated article directly into your CMS as a draft ready for editorial review.

| Setting | What it does |
|---------|-------------|
| Content | The article content to write |
| Document type | The Sanity schema type to create |
| Title | The document title |

**Output:** The Sanity document ID of the created/updated draft.

---

## Control Flow

### Wait for Approval

Pauses the workflow and sends an approval request via Slack or email. The workflow only continues once a human approves it.

**When to use it:** Before publishing content or sending a customer-facing message. Keeps a human in the loop without requiring them to manually trigger the next step.

| Setting | What it does |
|---------|-------------|
| Instructions | What you want the reviewer to check or decide |
| Timeout | How long to wait before the approval request expires (hours) |

**Output:** The review decision (Approved / Rejected) and any comment the reviewer left.
