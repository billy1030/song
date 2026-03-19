# Stock Market Research Skill

## Purpose
Standardized approach for AI to research and report stock market data with proper source attribution and date verification.

---

## ⚠️ FIRST STEP: Check the Clock

**BEFORE any data retrieval, ALWAYS run `session_status` to verify the current date/time.**

The system context may be stale. NEVER assume or guess today's date. Check explicitly.

---

## Preferred Data Sources

### 🇺🇸 US Stocks
- **Primary:** Yahoo Finance → https://finance.yahoo.com
- **Fallback:** CNBC, Reuters, Investopedia, Sunday Guardian Live
- **Index codes:** ^GSPC (S&P 500), ^DJI (Dow Jones), ^IXIC (Nasdaq)

### 🇭🇰 HK Stocks
- **Primary:** ET Net → https://www.etnet.com.hk
- **Secondary:** AA Stocks → https://www.aastocks.com
- **Index codes:** ^HSI (Hang Seng Index)
- **Note:** ET Net and AA Stocks block direct web fetch; use web search to find content

---

## Working Methods

### Method 1: Web Search (Recommended)
1. After checking the clock, use `web_search` with `date_after:"YYYY-MM-DD"` filter
2. Always include the date filter — at minimum "yesterday"
3. Pull data from authoritative sources (CNBC, Reuters, RTTNews, etc.)
4. Report source attribution for each data point

### Method 2: Web Fetch
1. Use `web_fetch` for specific article URLs found via search
2. Yahoo Finance pages work but contain dynamic JS — actual quotes may not extract
3. ET Net and AA Stocks return 404/403 — blocked
4. Best for: news articles, analysis pieces, market reports

### Method 3: Yahoo Finance API
- Endpoint pattern: `https://query1.finance.yahoo.com/v8/finance/chart/{SYMBOL}`
- **Status:** BLOCKED — returns 429 Too Many Requests without authentication
- Not usable without user's own API key

---

## Verification Checklist

Before reporting any stock data, confirm:

- [ ] **Clock check:** Did you run `session_status` first to get today's exact date?
- [ ] **Date check:** Is your data from today or yesterday? (older = labeled as such)
- [ ] **Source check:** Can you name where the data came from?
- [ ] **Honesty check:** If you don't have today's close, say "not yet available"

---

## Output Format

```
**📊 [Market] Market Update — [Verified Date from session_status]**

**Key Points:**
- [Data point] | Source: [Website]
- [Data point] | Source: [Website]

**Summary:**
[Brief interpretation]

⚠️ Note: [Any data gaps or things to watch]
```

---

## Critical Rules

1. **Check clock FIRST, always** — Run `session_status` before anything else
2. **Never fabricate data** — if you don't have today's close, say so
3. **Always cite sources** — inline attribution is mandatory
4. **Use web search first** — more reliable than direct fetch
5. **Label stale data** — old news must be labeled "older data"
6. **Admit limits** — dynamic prices need APIs; scrapers have constraints

---

## Example Workflow

**User asks:** "今日美股點睇？"

```
Step 1: Run session_status
→ Confirmed: 2026-03-19 08:33 UTC

Step 2: Run web_search with date_after:"2026-03-18"
→ Query: "US stock market March 19 2026"
→ Results from CNBC, Reuters

Step 3: Format and attribute
→ S&P 500: X points | Source: CNBC
→ Dow Jones: X points | Source: Reuters

Step 4: State freshness clearly
→ ⚠️ Note: US markets close at 9:30 PM HK time; today's close not yet available
```

