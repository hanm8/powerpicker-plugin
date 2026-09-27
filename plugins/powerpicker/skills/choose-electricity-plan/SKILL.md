---
name: choose-electricity-plan
description: Help someone in Australia pick an electricity plan or solar feed-in tariff. Use when the user uploads or pastes an electricity bill, asks for a cheaper power plan, asks if they're on a good deal, compares retailers (AGL, Origin, EnergyAustralia, etc.), or asks about feed-in tariffs, off-peak hours, or which plan suits solar, a battery or an EV.
---

Use the PowerPicker connector's tools. They cover residential plans in NSW, VIC, QLD, SA, ACT and TAS from the Australian Energy Regulator's plan data, refreshed daily. WA and NT are not covered; say so if the user is there.

## If the user shares a bill (PDF, photo or pasted text)

Read it before asking anything. `references/reading-a-bill.md` says where each figure is and how to handle unusual bills. Pull out:

- Supply address postcode, retailer, plan name
- Billing period (start, end, number of days)
- Grid usage in kWh by tariff (peak / shoulder / off-peak or a single rate), and the rate for each
- Controlled load kWh and rate, if any (kept separate)
- Solar exported in kWh and the feed-in rate, if any
- Daily supply charge
- Distributor (the network company named for faults and emergencies)
- Total amount due and any discounts or credits

Then work out `kwh_per_day` = grid usage kWh (excluding controlled load) ÷ days, and `solar_export_kwh_per_day` = exported kWh ÷ days. Show the user the figures you read in a short list and ask them to correct anything wrong only if a figure was unreadable or ambiguous; otherwise carry on.

Work out what the current plan costs a year from the bill's own rates: (daily supply × 365) + (each usage rate × its kWh ÷ days × 365) − (feed-in rate × exported kWh ÷ days × 365). Leave controlled load out, the same as the tool's estimates, so the two are comparable. Say that a bill covers one season, so a summer or winter bill over- or under-states a typical year.

Never repeat the NMI, account number, name or street address back in your answer.

## Steps

1. **Network.** Call `lookup_network` with the postcode. If it returns more than one network, use the distributor named on the bill; without a bill, ask which distributor is named on it.
2. **Usage.** From the bill as above. Without a bill, ask for daily kWh and solar exports; if they don't know, use 12 kWh a day and say it's a typical figure.
3. **Call `find_plans`** with the postcode, network, `kwh_per_day`, `solar_export_kwh_per_day`, and `limit: 10`. Use `no_conditions: true` unless they have a battery or EV or are open to membership plans.
4. **Check the best ones.** Call `get_plan` for the top two or three. If the bill shows most usage off-peak or at particular times, prefer the plan whose cheap hours match, and say why.
5. **Answer** with:
   - One line up front: how much a year they could save by switching to the best plan, against the current-plan cost you worked out (or "you're already on one of the cheapest" if the saving is under about $50).
   - The top three plans as a short table: retailer, plan, estimated yearly cost, saving vs now, feed-in rate, catches.
   - For time-of-use plans, the cheapest hours to run the dishwasher, washing machine or EV charger.
   - The data date from the tool result, and that the figures are estimates: discounts, sign-up credits, controlled load and demand charges aren't included.
   - The `officialListing` link from `get_plan` so they can confirm on Energy Made Easy (Victorian Energy Compare in VIC) before switching.

Don't recommend a plan whose `conditions` the user doesn't meet (e.g. "Battery needed" for a home without one). Don't give numbers that didn't come from the bill or a tool result.
