
# V9 — Connected Workflow

## Goal
Connect the existing KUKSOM dashboard to the V8 API so that:
1. Authorized collectors submit results.
2. Results enter `Pending`.
3. Verifiers approve or reject.
4. Public pages consume verified data.

## Important production rule
The public dashboard must filter to `status = 'Verified'`. Pending/rejected records must never be presented as verified election results.

## Next deployment steps
- Host the Node API on a server.
- Use PostgreSQL for production if multiple concurrent users/large uploads are expected.
- Use object storage for result sheets.
- Set strong environment secrets.
- Configure HTTPS and restricted CORS.
- Add rate limiting and backups.
- Import and verify the authoritative polling-unit directory.
- Connect the frontend forms to the API with authenticated requests.

## Neutral data labeling
The site should say that it is an independent KUKSOM data collection/monitoring initiative and is not INEC. Every public result should show its collection/verification status and source record where appropriate.
