KUKSOM Election 2027 - V7 Backend & Database Ready Prototype

V7 prepares the system for a real shared online backend.

Architecture:
- users
- wards
- polling_units
- elections
- results
- result_votes
- result_files
- audit_logs

Important:
This ZIP is still a frontend prototype. It does NOT create a live server or online database by itself.
The next production implementation should connect the UI to a secure backend/database, add server-side authentication, hashed passwords, role permissions, file storage and database constraints.

Political/data integrity:
- Keep KUKSOM clearly identified as an independent data collection/monitoring initiative.
- Do not present collected data as official INEC results.
- Verify the authoritative polling-unit directory before production.
