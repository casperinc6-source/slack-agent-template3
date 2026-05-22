# Render Fix

If Render says:

```txt
Error: Cannot find module '/opt/render/project/src/server.js'
```

then your repo root is one level above the actual app.

## Fastest fix in Render dashboard

Open your service settings and change:

### Option A — easiest
- **Start Command**: `node micro-offer-engine/server.js`

### Option B — cleaner
- **Root Directory**: `micro-offer-engine`
- **Start Command**: `node server.js`

Then redeploy.

## Repo fix included

This repo now also includes a root-level `server.js` shim, so if you push the latest changes, `node server.js` from the repo root will also work.
