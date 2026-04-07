# Data Model (v0.1)

## Purpose

This document defines the core data structures used in the Dynamic Drink Market (DDM) system.

The goal is to represent drinks, orders, and demand-related data in a way that supports dynamic pricing and future scalability.

---

## Core Entities

The system is based on two primary entities:

- Drink
- Order

These entities are sufficient for the initial version (v0.1) of the system.

---

## Drink Entity

Represents a product whose price changes dynamically.

### Structure

```json
{
  "id": 1,
  "name": "Beer",
  "base_price": 5.0,
  "current_price": 5.0,
  "last_updated": "2026-04-05T12:00:00Z"
}
```

### Fields

- id: Unique identifier
- name: Name of the drink
- base_price: Original static price
- current_price: Current dynamic price
- last_updated: Timestamp of last price update

## Order Entity

Represents a single purchase event.

### Structure

```json
{
  "id": 101,
  "drink_id": 1,
  "timestamp": "2026-04-05T12:01:00Z"
}
```

### Fields

- id: Unique identifier
- drink_id: Reference to the associated drink
- timestamp: Time when the order was placed

## Relationships

One Drink can have many Orders
Each Order belongs to one Drink

Relationship type:
Drink (1) ──── (N) Order

## Demand Representation

In v0.1, demand is not stored directly as a field.

Instead, it is calculated dynamically:

- Count the number of orders for a drink
- Within a defined time window (e.g. last 5 minutes)

Example:
SELECT COUNT(\*)
FROM orders
WHERE drink_id = 1
AND timestamp >= NOW() - INTERVAL 5 MINUTES

This value becomes the demand_score.

## Data Handling (v0.1)

In the initial version:

Data can be stored in memory
No database is strictly required
Simple arrays or collections are sufficient

Example:

```javascript
drinks = [];
orders = [];
```

## Future Extensions

The data model may evolve to include:

### Additional fields for Drink

- min_price
- max_price
- volatility_factor

### New entities

- User (to track behavior)
- Transaction (for financial tracking)
- PriceHistory (to store historical price changes)

### Analytics support

- Aggregated demand metrics
- Time-series data for visualization

## Design Considerations

- The model should remain simple in early stages
- Avoid storing redundant data (e.g. demand_score)
- Favor calculated values over stored ones when possible
- Ensure compatibility with relational databases

## Scalability Notes

As the system grows:

- Move from in-memory storage to relational databases (e.g. PostgreSQL)
- Introduce indexing for faster queries
- Consider caching demand calculations for performance
