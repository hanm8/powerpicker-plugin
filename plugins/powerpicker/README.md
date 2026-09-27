# PowerPicker

Compare Australian electricity plans and solar feed-in tariffs inside Claude, priced for your own home.

## Use it

Ask something like "I'm in 2150, we use about 14 kWh a day and export 8 kWh of solar. Which plan is cheapest?" or upload a power bill (PDF or photo). Claude reads your usage, rates and current plan from it, looks up your network, ranks every current residential plan in NSW, VIC, QLD, SA, ACT and TAS by estimated yearly cost, checks the best ones hour by hour, tells you how much you could save against your current plan, and links to each plan's official Energy Made Easy listing so you can confirm before switching.

## What's included

- **PowerPicker connector** (`https://powerpicker.com.au/api/mcp`): three read-only tools, `lookup_network`, `find_plans` and `get_plan`.
- **choose-electricity-plan skill**: the steps Claude follows to read your bill, pick the right network and explain the result.

## Data

Plan data comes from the Australian Energy Regulator's Energy Product Reference Data and is refreshed every morning. Estimates leave out discounts, sign-up credits, controlled load and demand charges.

Your bill is read by Claude in the conversation and never sent to PowerPicker. The connector receives only the postcode, usage figures and filters you give it. It needs no account, stores nothing and does not log postcodes.
