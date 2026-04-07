# Development Plan (v0.1)

## Overview

This document outlines the initial development plan for the Dynamic Drink Market (DDM) v0.1.

**Goal:** Validate the dynamic pricing concept with a functional prototype.

---

## Phase 1: Project Setup

### Tasks

| # | Task | Description |
|---|------|------------|
| 1.1 | Initialize Node.js project | Create package.json |
| 1.2 | Install dependencies | Express, TypeScript, types |
| 1.3 | Configure TypeScript | Create tsconfig.json |
| 1.4 | Create project structure | Create src/ and public/ folders |
| 1.5 | Verify empty server | Run basic Express server |

### Files to Create

```
ddm/
├── package.json
├── tsconfig.json
├── src/
│   └── index.ts
└── public/
    └── index.html
```

### Success Criteria

- [ ] `npm install` completes without errors
- [ ] `npm run dev` starts server on port 3000
- [ ] Browser shows basic page at http://localhost:3000

---

## Phase 2: Data Model

### Tasks

| # | Task | Description |
|---|------|------------|
| 2.1 | Define Drink interface | Create types.ts |
| 2.2 | Define Order interface | Create types.ts |
| 2.3 | Create in-memory store | Create data.ts |
| 2.4 | Add sample drinks | Initialize with 3-5 drinks |

### Files to Modify/Create

```
src/
├── types.ts   # Interfaces: Drink, Order
└── data.ts   # In-memory storage + sample data
```

### Success Criteria

- [ ] Drink interface includes: id, name, base_price, current_price, last_updated
- [ ] Order interface includes: id, drink_id, timestamp
- [ ] Sample drinks are initialized on startup

---

## Phase 3: Pricing Engine

### Tasks

| # | Task | Description |
|---|------|------------|
| 3.1 | Implement demand calculation | Count orders in time window |
| 3.2 | Implement price formula | new_price = base + (demand × factor) |
| 3.3 | Add price constraints | Min/max limits (±50%) |
| 3.4 | Implement price decay | Gradual return to base |
| 3.5 | Connect to data store | Integrate with data.ts |

### Files to Modify

```
src/
└── pricing.ts   # Pricing engine logic
```

### Success Criteria

- [ ] Demand score updates on new order
- [ ] Price stays within min/max bounds
- [ ] Price returns to base when no orders

---

## Phase 4: API & Server

### Tasks

| # | Task | Description |
|---|------|------------|
| 4.1 | Create GET /drinks endpoint | Return all drinks with prices |
| 4.2 | Create POST /orders endpoint | Register new order |
| 4.3 | Create GET /drinks/:id endpoint | Return single drink |
| 4.4 | Add CORS configuration | Allow local requests |
| 4.5 | Serve static frontend | Serve public/ folder |

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/drinks | List all drinks |
| GET | /api/drinks/:id | Get drink by ID |
| POST | /api/orders | Create new order |

### Success Criteria

- [ ] GET /api/drinks returns JSON with prices
- [ ] POST /api/orders creates order and updates price
- [ ] Frontend is served at /

---

## Phase 5: Frontend

### Tasks

| # | Task | Description |
|---|------|------------|
| 5.1 | Create drink list display | Show drinks with prices |
| 5.2 | Add order button | Button to place order |
| 5.3 | Add price refresh | Update prices on interval |
| 5.4 | Basic styling | Clean, readable UI |

### Files to Create/Modify

```
public/
├── index.html   # Main page
├── style.css  # Styles
└── app.js    # Frontend logic
```

### Success Criteria

- [ ] Drinks are displayed with current prices
- [ ] Clicking order button creates order
- [ ] Prices update automatically

---

## Phase 6: Testing & Validation

### Tasks

| # | Task | Description |
|---|------|------------|
| 6.1 | Manual testing | Test all features |
| 6.2 | Edge cases | Test empty orders, max/min prices |
| 6.3 | Performance check | Response times |
| 6.4 | Document findings | Note issues and improvements |

### Success Criteria

- [ ] All core features work
- [ ] No critical errors in console
- [ ] Ready for demo

---

## Development Timeline Recommendation

### Week 1: Setup + Data Model (Days 1-3)

- Day 1: Project setup, dependencies
- Day 2: Types and data store
- Day 3: Sample data, verify

### Week 2: Pricing Engine (Days 4-7)

- Day 4-5: Demand calculation
- Day 6: Price constraints + decay
- Day 7: Integration test

### Week 3: API + Frontend (Days 8-12)

- Day 8-9: REST API
- Day 10-11: Frontend
- Day 12: Integration

### Week 4: Testing + Polish (Days 13-14)

- Day 13: Testing
- Day 14: Validation and demo

**Total Estimated Time:** 2-3 weeks

---

## Commands Reference

### Development

```bash
# Install dependencies
npm install

# Run in development mode (with nodemon)
npm run dev

# Build TypeScript
npm run build

# Run production build
npm start
```

### Project Scripts (package.json)

```json
{
  "scripts": {
    "dev": "nodemon --exec ts-node src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js"
  }
}
```

---

## Next Steps

After validating v0.1:

1. **v0.2:** Add real-time updates (WebSockets)
2. **v0.3:** Add database persistence
3. **v1.0:** Production-ready application

---

## Notes

- Keep each phase small and testable
- Commit after each phase
- Get feedback early and often
- Focus on validating the concept, not perfection
