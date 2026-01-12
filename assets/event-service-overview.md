# Event Registration Service — 1-page overview

**What it is**  
A small web service used for club events to collect registrations and manage waitlists. The goal was simple: submissions should be reliable, and the system should be easy for a teammate to run if I’m not around.

**Stack**  
Node.js / Express • MongoDB • AWS Lightsail • Nginx • PM2

## Key flows

### 1) Registration
- User submits a signup form
- API validates inputs (required fields, basic formatting)
- Record is written to MongoDB
- Response confirms the submission

### 2) Waitlist
- If capacity is reached, new signups go to a waitlist
- Admin can promote users from waitlist as spots open

## Reliability choices (lightweight)
- PM2 used to keep the service running and auto-restart on failure  
- Nginx used as a reverse proxy for stable routing  
- Basic health check endpoint so it’s quick to confirm the service is up  
- Simple runbook written so non-DevOps teammates can deploy/check/restart

## What I learned
- Writing short operational docs (run steps + checks) matters as much as writing code  
- A “boring” checklist prevents most last-minute issues during event rush periods
