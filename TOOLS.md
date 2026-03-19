# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

## Stock Market Data Sources

### US Stocks
- **Yahoo Finance** → https://finance.yahoo.com
- 用於：S&P 500、Dow Jones、Nasdaq、個股行情

### HK Stocks
- **ET Net** → https://www.etnet.com.hk
- **AA Stocks** → https://www.aastocks.com
- 用於：恒生指數、港股個股行情

### 备注
- ET Net 同 AA Stocks 可能需要 JavaScript 或會 block web fetch，必要時用 web search 再導向去相關頁面
- Yahoo Finance 可以正常 fetch 數據

Add whatever helps you do your job. This is your cheat sheet.
