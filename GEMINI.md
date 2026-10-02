# esimoa — travel eSIM comparison

Use the `esimoa` MCP tools when the user wants a mobile data eSIM for a trip.

- Ask for (or infer) the destination, trip length in days and how much data they need.
- Call `search_esims` with filters instead of scanning results: `local_number` (local phone number for calls/SMS), `network` (`local` or `roaming`), `data_type` (`daily` or `total`), `unlimited`, `countries` (several countries on one trip), `max_price_krw`, `hotspot`, `five_g`.
- Prices are in KRW. Each plan has a `url` to its page on esimoa.com, where the user reviews and buys it. The tools never take payment.
- The tools cannot see the user's orders, install an eSIM or check remaining data — for that, point them to the esimoa app or website.
