# Pricing Engine (v0.1)

This document defines the core pricing logic of the Dynamic Drink Market system.

The goal is to simulate a demand-driven pricing model where drink prices fluctuate based on real-time ordering activity.

## Core Concepts

Each drink is treated as a dynamic asset with a price that changes over time.

The pricing system is based on:

- Demand (how often a drink is ordered)
- Time (recent activity matters more)
- Constraints (limits to prevent extreme behavior)

## Variables

Each drink contains the following attributes:

- `base_price`: The original fixed price of the drink
- `current_price`: The current dynamic price
- `demand_score`: A value representing recent demand
- `last_updated`: Timestamp of last price update

## Demand Calculation

Demand is calculated based on the number of orders within a recent time window.

Example:

- Time window: last 5 minutes
- Demand score = number of orders in that period

This ensures that only recent activity affects pricing.

## Pricing Formula (v1)

The price is calculated using a linear demand model:

new_price = base_price + (demand_score \* factor)

Where:

- `factor` controls how sensitive the price is to demand

## Constraints

To maintain a stable system, the following limits are applied:

- Minimum price = base_price \* 0.7
- Maximum price = base_price \* 2.0

These limits prevent extreme price fluctuations.

## Price Decay

If a drink is not ordered within the time window, its price gradually returns toward the base price.

This prevents permanent inflation.

Example behavior:

- No orders → demand_score decreases
- Price slowly moves back to base_price

## Update Trigger

Prices are updated when:

- A new order is placed
- A time interval passes (optional future improvement)

In v0.1, price updates occur on each new order event.

## Example Scenario

Base price: $5  
Factor: 0.2

Orders in last 5 minutes: 10

new_price = 5 + (10 \* 0.2) = $7

If no new orders occur, the price will gradually decrease toward $5.

## Future Improvements

- Weighted demand (recent orders matter more)
- Smoothing functions to reduce volatility
- Non-linear pricing models
- Machine learning-based predictions
