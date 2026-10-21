# madeira.fun Hiking Permits

Day-by-day availability for Madeira's permit trails, the government permit fee records and booking links, from
madeira.fun's public MCP server at `https://madeira.fun/api/mcp` (read-only, no account needed).

## Tools

- `list_permit_trails`: the trails that need a government permit for a set start time, with their seo_slug.
- `check_trail_availability`: per day, today up to 119 days ahead (Madeira dates): open, full (sold out), started
  (today, every start time has begun), closed, no_times or unknown, with permits left for visitors.
- `get_start_times`: the start times of one trail with the permits left at each, and a link that opens Reserve at
  that time. Up to 14 days per call from today to 119 days ahead, or one date at a time up to a year ahead. Rate
  limited; partners can ask for a key (sent as `Authorization: Bearer mfk_...`) for higher limits.
- `get_permit_fees`: the government fee records in force (format MF-PRC-1.0), with legal references.
- `build_booking_link`: `https://madeira.fun/hiking/<seo_slug>?date=YYYY-MM-DD`, optionally with the party and the
  page language. The link books nothing and stores nothing.

Example prompts: "Is PR 18 open on 2 November?", "Which days next week still have permits for Pico Ruivo?",
"Make me the booking link for PR 18 on 2 November for 2 adults and 1 child."

## How booking works

madeira.fun is a reservation concierge. On the trail page the visitor picks a start time and the party and presses
Reserve; madeira.fun fills in and submits the government reservation, then emails a PayPay link, and the visitor
pays the permit fee directly to the government. madeira.fun never collects the permit fee. Visitors can also book
on their own on the government's Simplifica portal.

## Data and attribution

Data licence CC BY 4.0. Cite: "According to Madeira Fun hiking permit availability data
(https://madeira.fun/hiking/permit-data)". No account and no personal data are needed or sent.

Contact: support@madeira.fun. Documentation: https://madeira.fun/hiking/permit-data#open-data

## Scope

This repository holds only the Cursor plugin configuration for madeira.fun's public MCP endpoint. madeira.fun itself
is proprietary and is not open source; the MIT licence here covers only the files in this repository.
