---
name: find-esim
description: Find and compare a travel eSIM for a trip with the esimoa tools — use when the user asks which eSIM or data plan to get for a destination, trip length, data need, local phone number or several countries.
---

# Find a travel eSIM

1. Work out the trip: destination country (or several countries), number of days, and roughly how much data the user needs. Ask one short question only if the destination or length is missing.
2. Call `search_esims` with the matching filters rather than scanning results:
   - several countries on one trip → `countries` (only plans that work in all of them)
   - needs a phone number for calls or SMS → `local_number: true`
   - wants the fastest network → `network: "local"`
   - heavy use → `unlimited: true`; light use → `data_gb` / `max_data_gb`
   - budget → `max_price_krw`; tethering → `hotspot: true`; 5G → `five_g: true`
   - sort by `price`, `data`, `price_per_gb` or `validity` when the user cares about that
3. If the user is torn between a few plans, call `compare_esims` with 2–5 ids — it returns a side-by-side table and which plan has the lowest price, most data, longest validity and lowest price per GB.
4. Present 3–5 plans in a short table: price (KRW), data, days, provider and notable features (local number, local network, hotspot, 5G). Mention trade-offs plainly.
5. Give each plan's `url` so the user can review and buy it on esimoa.com. Do not claim to purchase anything.
6. If nothing matches, relax one filter at a time and say which one you relaxed.
