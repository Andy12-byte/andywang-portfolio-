# Event Registration Service — Runbook (quick ops)

This runbook is intentionally short. It covers the minimum steps to keep the service running during an event.

## What’s running where
- Host: AWS Lightsail (single VM)
- Reverse proxy: Nginx
- App process manager: PM2
- Database: MongoDB (same VM or managed instance depending on setup)

## Common checks

### Health check
- Confirm the API responds (or open the health endpoint in a browser)
- If the site loads and submissions succeed, don’t touch anything

### Logs (quick look)
- If submissions fail, check recent app logs first (PM2 logs)
- If requests aren’t reaching the app, check Nginx logs/config

## Restart steps (safe order)
1) Restart the Node process (PM2)
2) If still failing, reload Nginx
3) If database connection errors appear, verify MongoDB is running

## Backup / restore (basic)
- Backup: export MongoDB collections before major changes or before an event
- Restore: import the latest dump if data is missing or corrupted
- Always test restore on a non-production copy if possible

## When to escalate
- Repeated 500 errors during submissions
- Database corruption / missing records
- Suspected credential leaks (rotate keys and take the service offline)
