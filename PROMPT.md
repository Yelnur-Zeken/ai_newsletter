# Jobescape AI Agent — Daily Brief Instructions

## SOURCES TO FETCH (yesterday's news only)

### Direct news pages — use WebFetch, extract items from yesterday:
1. https://llm-stats.com/ai-news — LLM model releases (PRIMARY)
2. https://llm-stats.com/llm-updates — model updates
3. https://aiflashreport.com/ — daily AI flash report
4. https://www.artificialintelligence-news.com/ — AI industry news
5. https://aichief.com/news/ — AI news roundup
6. https://crescendo.ai/news/latest-ai-news-and-updates — AI updates
7. https://venturebeat.com/ai/ — VentureBeat AI
8. https://www.therundown.ai/ — daily AI newsletter
9. https://www.marktechpost.com/ — AI research and tools
10. https://unite.ai/ — AI tools and news
11. https://buttondown.com/ainews/archive — AI newsletter archive
12. https://huggingface.co/papers — latest AI papers (fresh daily)
13. https://www.producthunt.com/topics/artificial-intelligence — new AI products
14. https://kersai.com/ — AI breakthroughs
15. https://the-decoder.com/ — AI news
16. https://simonwillison.net/ — AI developer news
17. https://techcrunch.com/category/artificial-intelligence/ — TechCrunch AI
18. https://devflokers.com/blog/ai-news-last-24-hours-april-2026-model-releases-breakthroughs — 24h roundup

### Hacker News (free API, no key):
https://hn.algolia.com/api/v1/search_by_date?query=AI+LLM+GPT+Claude&tags=story&hitsPerPage=30
Filter by created_at = yesterday. Keep stories with points > 15.

### Reddit (free JSON, no key):
- https://www.reddit.com/r/artificial/new.json?limit=30
- https://www.reddit.com/r/ChatGPT/new.json?limit=25
- https://www.reddit.com/r/singularity/new.json?limit=20
- https://www.reddit.com/r/MachineLearning/new.json?limit=20
Use header: User-Agent: JobescapeBot/1.0
Filter by created_utc = yesterday. Keep score > 30 or num_comments > 15.

### RSS feeds (free, parse XML, keep pubDate = yesterday):
- https://tldr.tech/api/rss/ai
- https://www.deeplearning.ai/the-batch/feed/
- https://jack-clark.net/feed/
- https://www.bensbites.com/feed
- https://aiweekly.co/issues.rss

### WebSearch fallback:
- AI news YESTERDAY model release
- AI tool launch YESTERDAY
- AI side hustle earn money YESTERDAY
- viral AI trending YESTERDAY
- EdTech AI app YESTERDAY

## DASHBOARD SECTIONS

1. SIGNALS (4 cards): biggest story, viral moment, audience barrier, key trend — each with arrow what it means for Jobescape
2. TEACH TODAY (4 items): new tools for app, difficulty tag, monetization angle
3. SIDE HUSTLE (5 items): earning opportunities, income range badge
4. CONTENT HOOKS (5 items): social media angles labeled: максимальный охват / вирусный / образовательный / закрытие страха / инспирейшн
5. COMPETITORS (4 items): EdTech/AI learning moves with signal level
6. AUDIENCE (4 items): fears/questions from Reddit+HN + product insight box
7. TOOLS OF DAY: pill grid with NEW/UPGRADE/TREND badges

## FILTER RULES
INCLUDE: AI tools anyone can use, side hustle opportunities, viral moments, user fears, EdTech competitor moves.
EXCLUDE: enterprise M&A, chip benchmarks, cloud pricing, regulatory compliance.

## DESIGN
Dark theme. bg=#08080f card=#0f0f1a card2=#141420 border=#1e1e30 purple=#a78bfa teal=#4fd1c5 orange=#f6a623 red=#f56565 green=#48bb78 yellow=#ecc94b text=#e2e8f0 muted=#64748b
All text in Russian.

## SCREENSHOT & TELEGRAM DELIVERY

After git push, take a screenshot of the dashboard and send it to Telegram:

Step A — Install playwright if not available:
pip install playwright 2>/dev/null; playwright install chromium 2>/dev/null

Step B — Take screenshot (save as /tmp/dashboard.png):
python3 << 'PYEOF'
from playwright.sync_api import sync_playwright
with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page(viewport={"width": 1400, "height": 900})
    page.goto("PAGES_URL/FILE_NAME")
    page.wait_for_timeout(3000)
    page.screenshot(path="/tmp/dashboard.png", full_page=True)
    browser.close()
PYEOF

Step C — Send photo to Telegram (replace YESTERDAY and FILE_NAME with actual values):
curl -s -X POST "https://api.telegram.org/bot8464854973:AAE290FwWKEUupoNDmg9j9TxUXUd6dgEMnQ/sendPhoto" \
  -F chat_id=5597477252 \
  -F photo=@/tmp/dashboard.png \
  -F "caption=☀️ AI Brief — YESTERDAY

🔥 [главный инсайт дня]
🛠 Новых инструментов: N
💰 [топ side hustle]

🔗 https://yelnur-zeken.github.io/ai_newsletter/FILE_NAME"

If screenshot fails for any reason, fall back to sending text-only message with the link.
