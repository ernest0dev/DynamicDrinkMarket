# Tech Stack (v0.1) - FINALIZED

## Finalized Stack

| Layer | Technology | Version |
|-------|-----------|---------|
| **Language** | TypeScript | ^5.x |
| **Runtime** | Node.js | ^20.x |
| **Server** | Express.js | ^4.x |
| **Frontend** | HTML + Vanilla JS | - |
| **Data** | In-memory | - |
| **Development** | ts-node, nodemon | ^10.x, ^3.x |

### Project Structure

```
src/
├── index.ts         # Entry point (Express server)
├── types.ts       # Data models & interfaces
├── pricing.ts    # Pricing engine logic
├── data.ts        # In-memory data store
├── api.ts         # REST API endpoints
└── public/       # Frontend static files
    ├── index.html
    ├── style.css
    └── app.js
```

### Dependencies

```json
{
  "dependencies": {
    "express": "^4.21.0",
    "cors": "^2.8.5"
  },
  "devDependencies": {
    "typescript": "^5.6.0",
    "ts-node": "^10.9.2",
    "nodemon": "^3.1.4",
    "@types/node": "^22.0.0",
    "@types/express": "^5.0.0",
    "@types/cors": "^2.8.17"
  }
}
```

---

## Purpose

This document defines the technological approach for building the Dynamic Drink Market (DDM) system.

---

## Application Scope (v0.1)

The initial version of the system will:

- Simulate order events
- Execute pricing logic
- Produce observable outputs
- Run as local on-premise application (not web/Cloud)
- Provide control panel for business users

---

## Clarifications

### What This Project Is NOT

| Concept | Reality |
|---------|----------|
| **Web development** | Uses browser for convenience, but runs locally |
| **SaaS** | On-premise, not hosted on internet |
| **Customer-facing** | Business internal use, not for end customers |

### How It Works

```
┌─────────────────┐      ┌──────────────────┐
│   NEGOCIO        │      │  DDM (local)     │
│ (Bar/Restaurant)│ ──── │  - Panel control │
│                  │      │  - Server local │
│   Camarero      │      │  - Red local     │
│   Caja          │      │  - No internet   │
└─────────────────┘      └──────────────────┘
```

---

## Architecture (v0.1)

```
src/
├── index.ts      # Servidor Express (entry point)
├── types.ts     # Interfaces de datos
├── pricing.ts  # Motor de precios
├── data.ts     # Almacenamiento en memoria
├── api.ts      # Endpoints REST
└── public/   # Archivos estáticos
    ├── index.html
    ├── style.css
    └── app.js
```

---

## Future Considerations

| Area | Technologies |
|------|---------------|
| Database | SQLite, PostgreSQL |
| Real-time | WebSockets |
| Desktop | Electron |
| Deployment | Docker |
