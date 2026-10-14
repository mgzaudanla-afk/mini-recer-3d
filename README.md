# Mini Racer 3D — Telegram `/game`

A simple mobile-friendly 3D-style driving game using Three.js, launched by a Telegram bot command.

## Files

- `index.html` — the game itself (host this on a public HTTPS website).
- `bot.py` — Telegram bot that responds to `/start` and `/game`.
- `requirements.txt` — Python dependency list.

## 1. Create a Telegram bot

1. Open Telegram and search for **@BotFather**.
2. Send `/newbot` and follow its prompts.
3. Copy the bot token. Keep it private; do not post it in chats or public code.

## 2. Host the game website

The game needs a public **HTTPS** URL because Telegram Web Apps require HTTPS.

Easy option:
1. Create a GitHub repository.
2. Upload `index.html` to the repository root.
3. In repository Settings → Pages, enable GitHub Pages (deploy from the main branch/root).
4. Wait for deployment and copy the published URL, similar to `https://yourname.github.io/repository/`.

You can also use another static host that provides HTTPS. Test the URL in your phone browser first; the game should load and show the START DRIVING screen.

## 3. Configure the Telegram bot domain

In **@BotFather**, use `/setdomain` and select your bot. Enter the domain of your hosted game (for example, `yourname.github.io`, not the full page path if BotFather asks for a domain).

## 4. Run the bot

Python 3.10+ is recommended. On a computer or Android using Termux:

```bash
python -m pip install -r requirements.txt
```

Set the two environment variables. Replace the examples with your own values:

**Linux / macOS / Termux**
```bash
export BOT_TOKEN="PASTE_YOUR_BOT_TOKEN_HERE"
export GAME_URL="https://yourname.github.io/repository/"
python bot.py
```

**Windows PowerShell**
```powershell
$env:BOT_TOKEN="PASTE_YOUR_BOT_TOKEN_HERE"
$env:GAME_URL="https://yourname.github.io/repository/"
python bot.py
```

Keep the terminal/session running while you want the bot to respond. For 24/7 operation, deploy `bot.py` on a Python hosting service that supports a continuously running process and set the same environment variables in that host's settings.

## 5. Play

1. Open your bot chat in Telegram.
2. Send `/game`.
3. Tap **Play Mini Racer 3D**.
4. Tap START DRIVING, then use ◀ and ▶ to steer.

## Troubleshooting

- **“Game website is not configured”**: make sure `GAME_URL` starts with `https://`.
- **Web App button missing or refusing to open**: use a public HTTPS URL and configure the domain in BotFather with `/setdomain`.
- **Blank game screen**: open the hosted page in your phone browser and check your connection. Three.js is loaded from jsDelivr, so the page needs internet access.
- **Bot does not respond**: verify `BOT_TOKEN`, and make sure `python bot.py` is still running.
- **Do not share your bot token**. If it leaks, revoke/regenerate it through BotFather.

## Notes

- This is a starter game. The score and coins are currently stored in the browser session and are not saved to a server or leaderboard.
- The game uses Three.js from a CDN; it is not a fully offline game.
