# KUKSOM V14 Deployment

## 1. Server requirements
- Node.js 18+ (20+ recommended)
- HTTPS domain for production
- Persistent disk for SQLite and uploaded result sheets (or migrate to PostgreSQL/object storage)

## 2. Install and start
```bash
cd server
npm install
```

Linux/macOS:
```bash
export JWT_SECRET="REPLACE_WITH_A_LONG_RANDOM_SECRET"
export ADMIN_PASSWORD="REPLACE_WITH_A_STRONG_ADMIN_PASSWORD"
export CORS_ORIGIN="https://your-domain.example"
npm start
```

Windows PowerShell:
```powershell
$env:JWT_SECRET="REPLACE_WITH_A_LONG_RANDOM_SECRET"
$env:ADMIN_PASSWORD="REPLACE_WITH_A_STRONG_ADMIN_PASSWORD"
$env:CORS_ORIGIN="https://your-domain.example"
npm start
```

Default port: 3000. Use `PORT` to change it.

## 3. Pages
- Public: `https://YOUR-DOMAIN/results`
- Admin: `https://YOUR-DOMAIN/admin`
- Root `/` redirects to the public results page content.

The backend serves the public and admin pages from `server/public` and serves `/api/*` from the same origin.

## 4. First login
Use the password configured in `ADMIN_PASSWORD`.
If no environment variable is supplied, the development fallback is `KUKSOM2027`.
Change it before deployment.

## 5. Demonstration workflow
- Admin/Data Collector submits test results.
- Verifier/Admin reviews and verifies them.
- Public page immediately shows only Verified records.
- Use another phone/browser to demonstrate the public page without login.

## 6. Reset after the demo
In `/admin`:
- Open `Demo Reset`.
- Type exactly `RESET DEMO`.
- Confirm.

The protected endpoint deletes:
- results
- party votes
- uploaded result-sheet records/files
- audit logs

It keeps:
- users
- wards
- polling units
- election definitions

Only an authenticated Admin can call the reset endpoint.

## 7. Production hardening
- HTTPS only.
- Strong random JWT secret.
- Strong unique admin password.
- Restrict CORS to the real origin.
- Add reverse proxy (Nginx/Caddy) and process manager (systemd/PM2/Docker).
- Add rate limiting and request logging.
- Use PostgreSQL for multi-user production load.
- Use durable object storage for uploaded result sheets.
- Back up database and files.
- Verify the current authoritative Polling Unit directory before production.
- Do not expose submitter identity or private audit information on public endpoints.
