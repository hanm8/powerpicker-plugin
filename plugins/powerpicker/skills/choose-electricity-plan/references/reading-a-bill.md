# Reading an Australian electricity bill

Layouts differ by retailer, but the same figures are on every bill, usually on page 2 ("Your charges" or "Account summary") rather than the front page.

## Where things are

- **Billing period**: "Billing period", "Supply period" or "For the period". Count the days yourself if only dates are given (include both ends as retailers do; if the bill states a day count, use theirs).
- **Usage lines**: one line per tariff, e.g. "Peak 412.3 kWh @ $0.3245". Rates may be shown per kWh in dollars ($0.3245) or cents (32.45c). Convert to cents.
- **GST**: most bills show rates excluding GST and add GST at the bottom. If the rates are ex-GST, multiply them by 1.1 so they match the tool's GST-inclusive figures. Look for "GST" on the line or "(excl. GST)" in the column header.
- **Supply charge**: "Daily supply charge", "Service to property" or "Supply charge", as days × $/day.
- **Controlled load**: "Controlled load", "CL1"/"CL2", "Off-peak hot water", "Economy" (QLD tariff 31/33 are controlled load). Keep it out of daily usage.
- **Solar**: "Solar feed-in", "Solar credit", "Export" or "Generation", shown as a credit (negative amount).
- **Distributor**: bills name it, usually near the NMI or under "Faults and emergencies" (e.g. "Ausgrid", "Energex", "United Energy"). Use that name as the `network`. If it isn't there, ask the user.
- **Discounts**: "Pay on time discount", "Guaranteed discount", credits. Note them, but compare on undiscounted rates as the tool does, and say the current plan's discount if it has one.

## Unusual bills

- **Estimated read** ("E" next to the reading, or "Estimated"): the usage may be off; say so.
- **Several rate periods in one bill** (a price change mid-bill): use kWh-weighted average rates.
- **Demand charges** (kW, "Demand"): the tool's estimates don't include them; mention it and don't compare the demand part.
- **Embedded networks** (apartment buildings, caravan parks, retirement villages where the "retailer" is the building manager): the tool's plans may not be available; say so.
- **Gas bills or dual-fuel bills**: use only the electricity part.
- **Monthly bills**: fine, but one month is even more seasonal than a quarter.
