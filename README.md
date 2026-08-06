# Rahlah — Supervisor dashboard

A static, read-only ops view (`index.html`) — live cars, captain roster, pending private
bookings, recent trips. Talks to the [rahlah-backend](../rahlah-backend) API. No server of
its own.

Consider this repo itself semi-sensitive: the login lives here, but the real security
boundary is the backend's password check. Still, there's no reason to make it any more
discoverable than it needs to be — don't link to it publicly.

## Before deploying

Open `index.html`, find this block near the top of the `<script>` tag, and set it to your
deployed backend's URL:

```js
const CONFIGURED_API_BASE = ''; // e.g. 'https://rahlah-backend.onrender.com'
```

The login itself uses a username/password created on the **backend** (see the backend's
README for how the first supervisor account gets bootstrapped) — this repo doesn't manage
accounts, it just calls the backend's login endpoint.

## Run it locally

```bash
npx serve .
```

## Deploying to Render

`render.yaml` is a **Static Site** Blueprint. On Render: **New → Blueprint**, point it at
this repo, set `CONFIGURED_API_BASE` first.
