Product Requirements Document (PRD): Trip Fuel Split Calculator (Web)
1) Overview
A mobile-first website that helps groups (friends, students, coworkers, families, travel groups) split fuel costs fairly and quickly for a shared trip. Users enter distance, vehicle mileage, fuel price, and number of people and the site outputs:
* Total fuel cost
* Each person pays (equal split)
* A copyable, WhatsApp/text-ready summary to reduce awkwardness and eliminate manual calculation.
2) Problem Statement
After a trip, people often avoid asking others for money because it feels awkward. Even when they do, calculating fuel cost manually is annoying and error-prone. Users want a neutral, simple tool that produces a clear split they can copy/paste into group chat.
3) Goals and Success Metrics
Goals
* Calculate accurate fuel cost and equal split in < 15 seconds
* Make sharing frictionless (copy button + WhatsApp share)
* Feel lightweight and trustworthy (no login required)
Success Metrics (MVP)
* ≥ 70% of users who calculate also click Copy/Share
* Median time-to-result < 20 seconds
* Low bounce on calculator page (implies clarity)
4) Target Users
* Primary: Anyone splitting ride fuel costs with a group (friends/students/coworkers/families)
* Primary scenario: After the trip (final numbers)
* Secondary scenario: Before the trip (estimate)
5) Key Use Cases
1. Post-trip final split: Enter actual distance + fuel price, get final amount per person, share in WhatsApp.
2. Pre-trip estimate: Enter expected distance and current fuel price to estimate how much each person should budget.
3. Quick re-calc: Change people count, mileage, or price and instantly update results.
6) Scope
In scope (MVP)
* Inputs: distance, mileage, fuel price, people count
* Output: total cost, cost/person
* Rounding options (e.g., nearest ₹1 / ₹5 / ₹10)
* Copy summary (one tap)
* Optional “Include owner” label text (even if cost split remains equal)
Out of scope (for MVP)
* Multi-leg trips, tolls, food, lodging
* Unequal splits, seat-based weighting, per-person distance
* Payments collection, reminders, user accounts
7) Functional Requirements
7.1 Calculator Inputs
* Distance (number) — unit: km (default)
* Mileage (number) — unit: km/l
* Fuel price (number) — currency symbol shown (e.g., ₹), unit: per liter
* People in vehicle (integer ≥ 1)
Validation
* Distance > 0
* Mileage > 0
* Fuel price > 0
* People ≥ 1
* Show inline errors and disable “Calculate” if invalid.
7.2 Calculation Logic
* Fuel used (liters) = distance / mileage
* Total cost = fuelUsed * fuelPrice
* Split per person = totalCost / people
Rounding (configurable)
* Default: round to nearest ₹1 (or nearest 1 unit)
* Options: exact (2 decimals), nearest 1, nearest 5, nearest 10
* Display both:
    * “Total fuel cost” (can remain precise to 1–2 decimals)
    * “Each person pays” (rounded per chosen rule)
7.3 Output + Sharing
On calculate, show:
* Total Cost
* Distance
* Mileage
* Fuel Price
* People
* Split line: “Each person pays: ₹X”
* Extra line: “(N people paying including owner)” (text only)
Copy Button
* One tap copies a formatted block like:
TRIP COST SPLIT
Total Cost: ₹322.2 Distance: 120 km Mileage: 40 km/l Fuel Price: ₹107.4/l People: 3
SPLIT: Each person pays: ₹107 (3 people paying including owner)
WhatsApp Share
* “Share to WhatsApp” button uses wa.me share link with prefilled text.
7.4 Reset / Recalculate
* “Reset” clears all inputs to defaults
* Changes to inputs can auto-update results or require “Calculate” (MVP recommendation: keep the button + allow Enter key)
8) UX / UI Requirements (based on your reference)
* Mobile-first layout; centered card on desktop
* Background: cream (bg-cream: rgb(244,239,234))
* Text: ink (text-ink: rgb(56,56,56))
* Font pairing:
    * Body: Inter (or system)
    * UI labels / headings: mono style (Aeonik Mono / Space Mono fallback)
* Clear sections:
    1. Trip Details (Distance, Mileage)
    2. Fuel Price (preset tabs optional: Petrol/Diesel/Custom)
    3. People
    4. Configuration (Include owner checkbox, rounding dropdown)
    5. Primary CTA button “CALCULATE SPLIT”
    6. Results area + Copy summary
* Accessibility:
    * Keyboard accessible inputs/buttons
    * Visible focus states
    * High contrast for primary actions
9) Non-Functional Requirements
* Loads fast (single page, minimal JS)
* Works well on mobile Safari/Chrome
* No login; no personal data required
* Offline-friendly optional (PWA later)
* Basic analytics events (optional): calculate, copy, share
10) MVP Release Plan
MVP (v1)
* Core calculator + rounding + copy + WhatsApp share
* Responsive layout matching your reference style
v1.1
* Unit toggle (km/mi, km/l vs mpg)
* Remember last used values (localStorage)
* “Estimate vs Final” small toggle text
v2
* Add tolls/parking, custom extras
* Unequal split options (owner pays 0 / owner pays less / per-seat weights)
* Trip history (optional)
11) Risks & Mitigations
* Confusion about mileage units: show unit labels next to fields and tooltips.
* Rounding disputes: show rounding selection clearly; optionally show “exact per-person” in small text.
* Fuel price varies by location: allow custom input always; presets optional.

