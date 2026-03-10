# SmartCourier AI Platform 📦

> AI-assisted courier logistics platform for D2C and B2B — built to scale to 10M+ shipments/year.

**Live Demo → [View on GitHub Pages](https://yourusername.github.io/smartcourier-platform/)**

---

## What's Inside

| File | Description | Status |
|------|-------------|--------|
| `index.html` | Homepage — links to all tools | ✅ Live |
| `courier-booking.html` | Customer booking app (4-step flow) | ✅ Live |
| `architecture-v2.html` | Full interactive architecture explorer | ✅ Live |
| `architecture-overview.html` | Layer-by-layer system overview | ✅ Live |
| `docs/smartcourier_architecture.docx` | Written architecture brief | ✅ Ready |

---

## Features Built

### Courier Booking App
- 4-step guided booking flow (Route → Parcel → Pickup → Review)
- Live price estimator — chargeable weight calc, GST, pickup fee
- Home pickup with time slots OR self drop-off
- Standard / Express / Same Day delivery options
- Dark & light mode
- Fully responsive — works on mobile and desktop

### Architecture Explorer
- 6 interactive tabs: System Overview, Returns & RTO, Payments, SLA, 3PL Partners, AI Error Prevention
- Clickable components with detail panels
- Full database schema with all 8 tables
- Gap analysis — 10 missing modules identified and designed

---

## System Architecture

```
┌─────────────────────────────────────────────────────┐
│                  CLIENT LAYER                        │
│  D2C Web Portal · Driver App · B2B Agent · Admin    │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│              API GATEWAY (Kong)                      │
│       Auth · Rate Limiting · Routing · SSL           │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│             CORE MICROSERVICES                       │
│  Booking · Tracking · Dispatch · Geo · Notifications │
│  Payments · Returns · SLA · Partner (3PL)            │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│              AI / ML LAYER                           │
│  YOLOv8 Scanner · Route Optimizer · Fraud Detection  │
│  Demand Forecasting · Smart Sorting (Phase 2)        │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│              DATA LAYER                              │
│  PostgreSQL + PostGIS · Redis · Kafka · S3           │
└─────────────────────────────────────────────────────┘
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML/CSS/JS → Next.js |
| Backend APIs | Node.js (Booking, Tracking), FastAPI (AI services), Go (GPS) |
| Database | PostgreSQL + PostGIS, Redis |
| Event Streaming | Apache Kafka |
| AI / ML | YOLOv8, EasyOCR, Google OR-Tools, TensorFlow |
| Mobile Apps | Flutter (Driver + Agent) |
| Notifications | Twilio (SMS), Meta BSP (WhatsApp) |
| Infrastructure | Docker, Kubernetes, AWS / GCP |
| Monitoring | Prometheus, Grafana |

---

## Parcel Lifecycle

```
1. BOOKED → 2. PICKUP SCHEDULED → 3. DRIVER PICKUP → 4. ORIGIN HUB SCAN
     → 5. IN TRANSIT → 6. DESTINATION HUB → 7. OUT FOR DELIVERY → 8. DELIVERED
```

Each stage emits an immutable event to the Shipment History ledger.

---

## Build Roadmap

- [x] Customer booking frontend
- [x] System architecture design
- [x] Database schema (7 core tables)
- [x] Returns & RTO module design
- [x] Payment & COD engine design
- [x] SLA breach management design
- [x] 3PL partner integration design
- [x] AI error prevention layer design
- [ ] Booking & tracking backend (Node.js)
- [ ] Validation rule engine
- [ ] Payment service (Razorpay integration)
- [ ] Returns / RTO service
- [ ] AI parcel photo scanner (YOLOv8 + FastAPI)
- [ ] Real-time GPS tracking (WebSockets)
- [ ] Driver mobile app (Flutter)
- [ ] Admin dashboard
- [ ] B2B corporate portal

---

## Scale Targets

- **10M+** shipments per year
- **5,000+** parcels per hub simultaneously
- **1,000+** drivers online concurrently
- Booking API response **< 200ms**
- Tracking API response **< 100ms**

---

## Project Structure

```
smartcourier-platform/
│
├── index.html                        ← Homepage
├── courier-booking.html              ← Customer booking app
├── architecture-v2.html              ← Full architecture explorer
├── architecture-overview.html        ← Architecture layer overview
├── README.md
│
├── /docs
│   └── smartcourier_architecture.docx
│
├── /backend                          ← Coming Phase 2
│   ├── /booking-service
│   ├── /tracking-service
│   ├── /payment-service
│   ├── /returns-service
│   └── /sla-service
│
├── /ai-models                        ← Coming Phase 3
│   ├── /parcel-scanner
│   └── /route-optimizer
│
└── /mobile-app                       ← Coming Phase 4
    ├── /driver-app
    └── /agent-app
```

---

*Architecture and frontend designed with Claude (Anthropic). Built to Delhivery / BlueDart / Shiprocket enterprise scale.*
