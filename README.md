# PowerPicker for Claude

Compare Australian electricity plans and solar feed-in tariffs inside Claude, priced for your own home. Upload a power bill, or just give your postcode and daily usage, and Claude ranks every current residential plan in NSW, VIC, QLD, SA, ACT and TAS by estimated yearly cost and tells you how much you could save.

The plugin is in [`plugins/powerpicker`](plugins/powerpicker). It bundles the PowerPicker MCP connector (`https://powerpicker.com.au/api/mcp`) and a skill that reads your bill and compares plans.

## Install

- **Claude (claude.ai, desktop, mobile):** Customize → Plugins → Add → Add marketplace, and enter `hanm8/powerpicker-plugin`. Then install **powerpicker** and connect it on the plugin's Connectors tab.
- **Claude Code:**
  ```bash
  claude plugin marketplace add hanm8/powerpicker-plugin
  claude plugin install powerpicker@powerpicker
  ```
- **Connector only (Claude or ChatGPT):** add a custom connector with the URL `https://powerpicker.com.au/api/mcp`. No account or API key needed.

More at https://powerpicker.com.au/ai-assistants.

## Data

Plan data comes from the Australian Energy Regulator's Energy Product Reference Data, refreshed every morning. Your bill is read by Claude in the conversation and never sent to PowerPicker. See [plugins/powerpicker/README.md](plugins/powerpicker/README.md) for what the connector receives.

This repository is a copy of the `plugin/` folder in PowerPicker's site repository; changes are made there and synced here.
