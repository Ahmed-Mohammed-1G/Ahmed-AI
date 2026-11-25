# Ahmed AI Mini App setup

The Worker now serves the branded file explorer at `/app` and its authenticated API at `/miniapp/api`.

## One-time configuration

1. Deploy the updated Worker.
2. In Cloudflare Worker **Settings → Variables and Secrets**, add a plain-text variable:
   - Name: `MINI_APP_URL`
   - Value: `https://YOUR-WORKER-DOMAIN/app`
   Use the Worker’s actual HTTPS `workers.dev` address or a custom domain. Keep the `/app` path.
3. Open **@BotFather**, run `/setdomain`, select the Ahmed AI bot, and enter only the hostname from that URL (for example, `your-worker-domain.workers.dev`).
4. In the private chat with Ahmed AI, request the GitHub or Drive file map again. The new **Open professional file explorer** button will appear.

## What it includes

- Official technology marks from Simple Icons CDN for common programming languages and frameworks (HTML5, CSS3, JavaScript, TypeScript, Python, Java, PHP, C/C++, C#, Go, Rust, Ruby, Swift, Kotlin, Vue, SQL, Docker, and more).
- Search, folder navigation, file details, open links, and sending downloads back to Telegram.
- Telegram Web App `initData` HMAC verification on the Worker. Only the configured `ALLOWED_USER_ID` can use the browsing API.
- The existing Telegram inline-keyboard browser remains available as a fallback.

The Mini App reads the existing `browse:<chat id>` session, so request a fresh map from the bot if the browsing session has expired.
