# LoopLane

Advanced carpooling platform with safety features, real-time tracking, and carbon reporting.

**Stack:** Node.js + Express + MongoDB (Mongoose) + Socket.IO backend · React 18 + Vite + Tailwind + Redux Toolkit frontend (`client/`)

## Prerequisites

- Node.js >= 18, npm >= 9
- MongoDB (required)
- Redis (optional — distributed caching & rate limiting)
- Solr (optional — fast full-text admin user search)

## Setup

```bash
npm install
cd client && npm install && cd ..
cp .env.example .env   # fill in your values
cp client/.env.example client/.env
```

## Run locally (dev)

```bash
npm run dev            # backend at http://localhost:3000
cd client && npm run dev   # frontend at http://localhost:5173
```

## Run with Docker (Mongo + Redis + Solr + API)

```bash
docker compose up --build
docker compose exec app npm run seed:admin   # first time only
```

- API: http://localhost:3000
- Swagger docs (requires login): http://localhost:3000/api/docs

> `docker-compose.yml` ships dev-only placeholder secrets — replace them for any real deployment.

## Verification

```bash
npm test -- --runInBand   # jest unit tests
npm run build             # build the React client
npm run verify:system     # health, auth, swagger, cache & search checks
```

## Useful scripts

| Command | Purpose |
|---|---|
| `npm run seed:admin` / `seed:sample` | Seed an admin user / sample data |
| `npm run solr:reindex-users` | Index users into Solr |
| `npm run verify:system` | End-to-end system verification |
| `npm run report:db` | DB optimization report |
| `npm run bench:redis` | Redis cache benchmark |

See `.env.example` and `client/.env.example` for all required environment variables (MongoDB, JWT, Cloudinary, Twilio, SMTP, Razorpay, Google Maps).
