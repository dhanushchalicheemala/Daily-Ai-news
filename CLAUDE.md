# Daily AI News — Agent Instructions

This repo publishes a daily AI news digest as a markdown file.

## Branch & Push Rules

- Always commit and push directly to **`main`**.
- Do NOT create a new branch. If the session assigns a feature branch, push to `main` anyway.
- Use: `git push -u origin main`

## Daily Workflow

1. Research today's AI news (startups, funding, breakthroughs, new tools, model releases, company updates).
2. Create a markdown file named `YYYY-MM-DD.md` (today's date) in the repo root.
3. Organise content into sections: **Startups & Funding**, **IPOs & Corporate Moves**, **New Models & Tools**, **Breakthroughs & Research**, **Company & Product Updates**.
4. Include a brief description and a source link for every item.
5. Commit with message: `AI news for YYYY-MM-DD`
6. Push to `main`.
7. After a successful push, send the iMessage notification (see below).

## iMessage Notification (via Pushcut)

After every successful push, call this webhook to deliver a summary to iMessage:

```bash
curl -s -X POST "https://api.pushcut.io/BrTmPX4JXGCQap4NYsg5C/notifications/My%20First%20Notification" \
  -H "Content-Type: application/json" \
  -d "{\"title\": \"Daily AI News — $(date +%Y-%m-%d)\", \"text\": \"Today's AI news digest has been published to GitHub. Check the repo for the full summary.\"}"
```

If the push fails, do not send the notification.
