HAHAHOST - repaired starter package

IMPORTANT SECURITY
- No Telegram bot token is included in this repository.
- The token that was hard-coded in the older source should be revoked in @BotFather.
- Generate a new token and set it as the BOT_TOKEN environment variable in the hosting dashboard.
- Set ADMIN_ID to your numeric Telegram user ID. The source defaults to 5427735251; change it in the host environment if needed.
- Never commit BOT_TOKEN, .env files, database files, or user uploads to GitHub.

Files
- HAHAHOST.py: Telegram hosting bot source
- requirements.txt: Python dependencies

Run locally / on a VPS
1. python -m venv venv
2. Activate the venv
3. pip install -r requirements.txt
4. Set BOT_TOKEN and ADMIN_ID environment variables
5. python HAHAHOST.py

Hosting notes
- This bot runs user-uploaded Python scripts as subprocesses. Only deploy where this is explicitly allowed.
- Run untrusted uploaded scripts in isolated containers with strict CPU, memory, filesystem, and network limits. This source does not provide a full security sandbox.
- The process guard now treats Linux zombie processes as dead and uses a smaller Telegram handler thread pool. This helps with false-running states and thread contention, but cannot automatically identify every logically hung user script.
- SQLite and uploaded files live on the local filesystem. On platforms with ephemeral storage, data can disappear on restart/redeploy unless persistent storage is configured.
- Keep one active instance of the Telegram bot per token; multiple instances can cause Telegram polling conflicts.
