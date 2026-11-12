# Deploy affiliate-hub to production (WR #18330)

Everything is wired — one command remains, and it needs the owner's DO token.

## Option A — DigitalOcean App Platform (WR's choice)
```bash
doctl auth init   # paste DIGITALOCEAN_TOKEN (vault: zero_touch_secrets.py)
doctl apps create --spec .do/app.yaml
# then: doctl apps list → grab the live URL
```

## Option B — Any Docker host (Oracle free VM / own machine)
```bash
cp .env.example .env   # fill DATABASE_URL, session secret
docker compose up -d
```

## DNS
Point affiliate.oaudrey.com (Cloudflare dashboard → DNS → CNAME → the app URL).
