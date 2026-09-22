# KUKSOM V10 Deployment

## Backend
```bash
cd server
npm install
export JWT_SECRET="replace-with-a-long-random-secret"
export ADMIN_PASSWORD="replace-with-a-strong-password"
node server.js
```

Windows PowerShell:
```powershell
$env:JWT_SECRET="replace-with-a-long-random-secret"
$env:ADMIN_PASSWORD="replace-with-a-strong-password"
node server.js
```

The API starts on port 3000 unless `PORT` is set.

## Frontend
Open `index.html` or serve it from a web server. In **V10 Result Entry**, set API Base URL to:
`https://YOUR-API-DOMAIN/api`

## Workflow
Collector logs in -> enters election/ward/polling unit/votes -> uploads result sheet -> submits as Pending.
Verifier/Admin reviews -> Verified or Rejected.
Public endpoint returns Verified records only.

## Production checklist
- HTTPS
- strong JWT secret and admin password
- restricted CORS
- PostgreSQL for concurrent production workloads
- object storage for result sheets
- backups
- verified current polling-unit directory
- monitoring and rate limiting
- never expose private submitter data on public endpoints
