# Dynamic Drink Market (DDM)

> A real-time pricing engine that transforms a bar menu into a simulated stock market.

## Concept

**Dynamic Drink Market (DDM)** is an open-source system that simulates a stock market using a bar's menu. Instead of trading stocks, customers “trade” drinks — and prices fluctuate dynamically based on demand.

The more a drink is ordered within a time window, the higher its price rises. Conversely, drinks with low demand decrease in price, encouraging exploration and strategic ordering.

This creates a gamified, interactive experience for customers while providing businesses with a novel pricing model.

---

## Goals

- Create a **real-time dynamic pricing engine**
- Simulate **market behavior (supply & demand)**
- Provide a **fun and interactive UX** for customers
- Build a **modular and scalable system**
- Open source for experimentation and improvement

---

## Core Features

### Dynamic Pricing

- Prices increase when demand rises
- Prices decrease when demand falls
- Adjustable sensitivity to demand changes

### Time-Based Demand Tracking

- Orders are tracked within configurable time windows (e.g. last 5–10 minutes)
- Prevents permanent price inflation

### Market Stabilization Logic

- Upper and lower price bounds
- Anti-volatility controls
- Optional “market reset” events

### Real-Time Interface

- Live updating menu (TV, tablet, or web app)
- Visual indicators

### Admin Dashboard

- Configure:
  - Base prices
  - Volatility factor
  - Time windows
  - Max/min limits

---

## Pricing Algorithm (Concept)

Each drink has:

- `base_price`
- `current_price`
- `demand_score`

### Example Formula (v1)

```
new_price = base_price * (1 + (demand_score * volatility_factor))
```

Where:

- `demand_score` = orders in last N minutes / average orders
- `volatility_factor` = configurable (e.g. 0.05 – 0.2)

---

### Alternative (More Stable Model)

Use smoothing:

```
new_price = current_price + (alpha * (target_price - current_price))
```

Where:

- `alpha` = smoothing factor (0 < α < 1)

---

## Event Flow

1. Customer orders a drink
2. Backend logs the order
3. Demand score updates
4. Pricing engine recalculates price
5. New price is broadcast in real-time
6. UI updates instantly

---

## Gamification Ideas

- “Market Crash” event (random price drops)
- “Happy Hour” with inverted logic
- Leaderboard of most traded drinks
- Price history graphs

---

## Potential Use Cases

- Bars & restaurants
- Events / festivals
- Interactive exhibitions
- Educational simulations (economics)

---

## Future Improvements

- Machine learning for price prediction
- Customer segmentation
- Multi-location synchronization
- Mobile ordering integration
- Analytics dashboard

---

### Potential Use Cases

- Bars & restaurants (main)
- Coffee shops
- Nightclubs
- Hotels (pool bars, lobby bars, rooftop bars)
- Events / festivals
- Food halls / food courts

## Future Improvements

- Machine learning for price prediction
- Customer segmentation

---

## Project Status

Idea / Concept Phase
🚧 Not yet implemented

---

## Contributing

This project is currently in the ideation stage. Contributions, ideas, and discussions are welcome.

---

## License

MIT License (planned)

---

## Inspiration

Inspired by real-world implementations of “stock market bars” where drink prices fluctuate based on demand.

---

## Author Notes (for future me)

- The key challenge is **balance between chaos and control**
- Too volatile = confusing UX
- Too stable = boring system
- Focus on:
  - Smoothness
  - Predictability (to a degree)
  - Fun factor

Think: _“controlled chaos”_

---

> If you're reading this in the future: yes, this is still a great idea. Build it.
