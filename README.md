# Quality Speakers — Vercel Backend (Next.js)

This repo is ready to **Import to Vercel** or **Upload to GitHub**. It exposes:

- `POST /api/speaking-outreach` — start/stop the campaign (no DB required)
- `GET  /api/speaking-outreach?userId=...` — fetch campaigns + simple stats

> NOTE: This uses in-memory mock storage so it runs without a database.
> You can later swap `lib/db.ts` with Prisma/Postgres if you want.

## Quick Deploy
1. Upload this folder to a GitHub repo (or import directly in Vercel).
2. In Vercel: **Add New → Project → Import Git Repository** → **Deploy**.
3. Test:
   ```bash
   curl -X POST https://YOUR-PROJECT.vercel.app/api/speaking-outreach      -H "content-type: application/json"      -d '{"action":"start","userId":"demo-user","outreachConfig":{"speakingTopics":"Leadership","linkedinKeywords":"event organizer"}}'
   ```

## Env (optional)
Create `.env` or set in Vercel Project Settings:
```
MAKE_WEBHOOK_URL=
MAKE_API_KEY=
VAPI_API_KEY=
VAPI_API_URL=https://api.vapi.ai
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_PHONE_NUMBER=
CALENDLY_API_KEY=
CALENDLY_API_URL=https://api.calendly.com
```

## Where to connect Lindy
- Webhook/callback URL → `https://YOUR-PROJECT.vercel.app/api/speaking-outreach` (POST with `{ "action": "start" | "stop" }`)
- From Lindy code/HTTP step, you can also POST here to trigger a run.
