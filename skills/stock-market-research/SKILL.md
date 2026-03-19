# Stock Market Research Skill

## Purpose
Standardized approach for AI to research and report stock market data with proper source attribution and date verification.

---

## Current Date
**Always check:** Today is 2026-03-19 (UTC) unless the user specifies otherwise.

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
1. Use `web_search` with `date_after:"YYYY-MM-DD"` filter to get fresh results
2. Always include the date filter — minimum "yesterday" or "2026-03-18"
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

- [ ] **Date check:** Do I know today's exact date?
- [ ] **Source check:** Can I identify where the data came from?
- [ ] **Freshness check:** Is the data from today or yesterday? (older data must be labeled as such)
- [ ] **Honesty check:** If I don't have the latest closing data, say so explicitly

---

## Output Format

When providing stock market research:

```
**📊 [Market] Market Update — [Date]**

**Key Points:**
- [Data point] | Source: [Website]
- [Data point] | Source: [Website]

**Summary:**
[Brief interpretation]

⚠️ Note: [Any data gaps or things to watch]
```

---

## Critical Rules

1. **Never fabricate data** — if you don't have today's close, say "today's data not yet available"
2. **Always show your work** — cite sources inline
3. **Use web search first** — it's more reliable than direct fetch for this use case
4. **Check dates** — old data must be labeled as old; don't present stale info as current
5. **Admit limitations** — dynamic stock prices require authenticated APIs; web scraping has limits

---

## Example Workflow

**User asks:** "今日美股點睇？"

1. Check current date (2026-03-19)
2. Run web search for "US stock market March 19 2026" with date_after filter
3. Collect data from CNBC/Reuters/RTTNews
4. Format response with sources
5. Clearly state if today's close isn't available yet

