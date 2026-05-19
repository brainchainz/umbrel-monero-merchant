# Monero Merchant for Umbrel

A free, open-source point-of-sale backend for accepting Monero (XMR) payments on Umbrel.

## Requirements

- [Umbrel OS](https://umbrel.com) with the official **Monero** app installed
- A running [MoneroPay](https://moneropay.eu) instance
- Android POS client (optional, for in-person payments)

## Install

Add this repository to your Umbrel community app store:

```
https://github.com/brainchainz/umbrel-monero-merchant.git
```

Then install **Monero Merchant** from the store.

## App Store Files

- `monero-merchant/docker-compose.yml` — services: app_proxy, backend, db, wallet-rpc
- `monero-merchant/exports.sh` — auto-detects Umbrel Monero node credentials, generates secrets
- `monero-merchant/umbrel-app.yml` — Umbrel app metadata
- `monero-merchant/icon.png` — app icon (500x500 PNG)

## What Gets Installed

| Service | Image | Purpose |
|---------|-------|---------|
| backend | `sirjamzalot/monero-merchant-backend:v2.0.0-umbrel7` | Go API + admin dashboard |
| db | `postgres:16-alpine` | PostgreSQL data store |
| wallet-rpc | `sethsimmons/simple-monero-wallet-rpc:latest` | Monero wallet RPC |
| app_proxy | `getumbrel/app-proxy:1.7.0` | Umbrel reverse proxy |

## Configuration

On first install:
1. Set your **Admin Password** for the dashboard login
2. Enter your **MoneroPay Base URL** and **Callback URL**
3. The app auto-detects your Umbrel Monero node credentials — leave overrides blank unless using a custom node

## Admin Dashboard

After install, open the app in Umbrel. Log in with:
- Username: `admin`
- Password: the one you configured

The dashboard shows:
- System status (node sync, wallet balance, MoneroPay health)
- Vendor management
- Invite creation
- Transfer balance between vendors
- Credentials for Android POS client pairing

## License

GPL-3.0 — same as upstream [Monero Merchant](https://github.com/Monero-Merchant/monero-merchant).
