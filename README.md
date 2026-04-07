# Dynamic Drink Market (DDM)

> A real-time pricing engine that transforms a bar menu into a simulated stock market.

---

## Overview

Dynamic Drink Market (DDM) is an open-source system that simulates a stock market using a bar's menu.

Instead of trading stocks, customers “trade” drinks — and prices fluctuate dynamically based on demand in real time.

The more a drink is ordered, the higher its price rises. Drinks with lower demand decrease in price, creating a dynamic and interactive experience.

---

## Goals

- Build a **real-time dynamic pricing engine**
- Simulate **supply & demand behavior**
- Create a **gamified user experience**
- Design a **scalable and modular system**
- Enable **experimentation through open source**

---

## Core Features

- Dynamic pricing based on demand
- Time-based demand tracking
- Market stabilization mechanisms
- Real-time updates
- Configurable system parameters

---

## How It Works (High-Level)

1. A customer orders a drink
2. The system records the order
3. Demand metrics are updated
4. Prices are recalculated
5. Updated prices are reflected in real time

---

## Documentation

Detailed technical documentation is available in the `/docs` directory:

| Document | Description |
|----------|-------------|
| [System Overview](docs/system-overview.md) | Problem, approach, system flow, and core components |
| [Pricing Engine](docs/pricing-engine.md) | Demand calculation, pricing formula, and constraints |
| [Data Model](docs/data-model.md) | Drink and Order entities, relationships, and data structures |
| [Tech Stack](docs/tech-stack.md) | Technology decisions and future considerations |

---

## Use Cases

- Bars & restaurants
- Coffee shops
- Events & festivals
- Interactive experiences
- Educational simulations

---

## Project Status

Concept / Early Development  
🚧 Not yet implemented

---

## Contributing

This project is currently in the ideation phase.  
Ideas, feedback, and discussions are welcome.

---

## License

MIT (planned)

---

## Inspiration

Inspired by real-world “stock market bars” where drink prices fluctuate based on demand.

---

## Author Notes

The core challenge of this project is achieving:

> **Controlled chaos**

- Too volatile → confusing
- Too stable → boring

The goal is to find the perfect balance between both.

---

> If you're reading this in the future: yes, this is still a great idea. Build it.
