# Rebel Ink Tattoos

Same simple deploy style as HairInk — plain Render Web Service, no database setup.

## Deploy on Render

1. Push this folder to GitHub (files at repo **root**).
2. Render → **New → Web Service**
3. Settings:
   - **Build Command:** leave empty (or `echo ok`)
   - **Start Command:** `node server.js`
   - Plan: Free
4. Deploy — no environment variables required.

## First admin

Open **Logs** and find:
```
FIRST ADMIN SETUP REQUIRED. Open /admin-setup?token=...
```
Open that URL and create your admin email/password.

## Optional (recommended)

In Environment, set:
- `JWT_SECRET` — long random string
- `ADMIN_SETUP_TOKEN` — long random string

So they stay the same after restarts.

## Note on data

Members and appointments are saved in `data/*.json` on the server.
On free Render, a full redeploy can reset files. Keep a keep-alive bot on `/api/health` and avoid unnecessary redeploys. For permanent storage, use the Postgres version instead.

## Health

`GET /api/health`
