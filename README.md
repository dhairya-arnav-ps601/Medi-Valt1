# Medi Vault (HTML / CSS / JavaScript)

Pure client-side **HTML, CSS, and JavaScript** rewrite of Medi Vault (all Python/Flask server dependencies removed).

## Features

- **Role-Based Access Control (RBAC)**:
  - `clerk`: Register patients, view directory, upload verified medical documents
  - `doctor`: View records, edit document metadata/notes/versions, add & stop prescriptions, print Rx slips
  - `auditor`: Inspect append-only audit logs with outcome filters, approve/decline staff requests, create users, reset passwords, force logout, disable/enable/soft-delete accounts
  - `patient`: Self-service signup, personal health portal (documents, active/past prescriptions, printable Rx, notifications, profile)
- **Client-Side Persistence & Security**:
  - Records, users, prescriptions, and audit trails stored in `localStorage`
  - Uploaded files (`PDF`, `PNG`, `JPG`, max 5 MB) validated by magic-byte signatures, SHA-256 hashed via Web Crypto, and stored in `IndexedDB`
  - Password hashing via PBKDF2-SHA256 (`crypto.subtle`)
  - 30-minute sliding session timeout, `session_version` invalidation, and 5-attempt login lockout
- **Light / Dark Theme**: Instant toggle persisted in `localStorage` with zero flash

## Demo Accounts (Synthetic Data Only)

All local demo accounts use password `Demo@1234`:
- Staff: `clerk`, `doctor`, `auditor`
- Patient: `asha` (linked to `MRN-1001`)

> **Disclaimer**: Synthetic demo data only. Do not use for real patient records.

## Run Locally

Serve the root folder with any static HTTP server (e.g. `npx serve .` or VS Code Live Server).

## Deploy on Vercel

Configured with `vercel.json` for SPA routing and security headers.
