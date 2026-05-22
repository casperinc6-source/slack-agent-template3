# Deploy to Render Now

This project is already prepared for Render.

## Current deployment-safe state

- website works
- PayShap reference flow works
- email automation is disabled until you add a real webhook
- WhatsApp automation is disabled until you add a real webhook
- the app can auto-detect its Render URL from Render environment variables

## Before you deploy

You do NOT need to give anyone your passwords.

You only need your own Render account open in your browser.

## Fastest deploy path

### 1. Put this project in GitHub

Create a repo and upload the `micro-offer-engine` folder.

If you use Git locally:

```bash
cd micro-offer-engine
git init
git add .
git commit -m "Initial deploy"
```

Then create a GitHub repo and push it.

### 2. In Render

1. Log in to Render
2. Click **New +**
3. Click **Blueprint** or **Web Service**
4. Connect your GitHub repo
5. Select the repo containing `micro-offer-engine`

If using **Blueprint**, Render should read `render.yaml`.

If using **Web Service**, use these values:

- **Environment**: `Node`
- **Build Command**: leave blank
- **Start Command**: `node server.js`

### 3. Add environment variables in Render

Add these values:

```txt
APP_SECRET=change-this-to-a-long-random-secret
ADMIN_PASSWORD=change-this-admin-password
PAYMENT_WEBHOOK_SECRET=optional-secret-for-payment-webhooks
OFFER_INTERVAL_HOURS=4
```

You do NOT need `BASE_URL` because the app now auto-detects the Render URL.

### 4. Deploy

Click **Create Web Service** / **Apply Blueprint**.

### 5. After deploy finishes

Render will show your live URL, something like:

```txt
https://campos-technologies-micro-offers.onrender.com
```

Open:

- `/` for the public page
- `/admin` for the admin page

## Admin login after deploy

Use the `ADMIN_PASSWORD` value you set in Render.

## Important note about storage

This app currently stores offers, leads, orders, and payments in local JSON files.

On Render, local filesystem persistence can be limited depending on plan and deploy behavior.
For a more durable production setup later, move storage to:

- Postgres
- Supabase
- Render persistent disk + app changes

## After the site is live

Send me the live Render URL and I can help with:

- final base URL confirmation
- real email webhook integration
- real WhatsApp template webhook integration
- approved Meta template names
