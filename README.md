# madeira.fun Hiking Permits

Day-by-day availability for Madeira's permit trails, the government permit fee records, booking links and permit
reservations, from madeira.fun's public MCP server at `https://madeira.fun/api/mcp` (no account needed to read;
a reservation needs the visitor's agreement and the code madeira.fun emails them).

## Tools

Reading:

- `list_permit_trails`: the trails that need a government permit for a set start time, with their seo_slug.
- `check_trail_availability`: per day, today up to 119 days ahead (Madeira dates): open, full (sold out), started
  (today, every start time has begun), closed, no_times or unknown, with permits left for visitors (an estimate).
- `get_start_times`: the start times of one trail with the permits left at each, and a link that opens Reserve at
  that time. Up to 14 days per call from today to 119 days ahead, or one date at a time up to a year ahead. Rate
  limited; partners can ask for a key (sent as `Authorization: Bearer mfk_...`) for higher limits.
- `get_permit_fees`: the government fee records in force (format MF-PRC-1.0), with legal references.
- `build_booking_link`: `https://madeira.fun/hiking/<seo_slug>?date=YYYY-MM-DD`, optionally with the party and the
  page language. The link books nothing and stores nothing.

Reserving (listed while madeira.fun has it switched on):

- `start_reservation`: step 1. Before calling it, tell the visitor that madeira.fun creates a madeira.fun account with
  their email, sends that email and the party size to the Madeira government's Simplifica system (IFCN), and that the
  permit fee is then paid to the government through the emailed PayPay link within 24 hours, or before the start time
  if sooner. It checks the start time and emails the visitor a 6-digit code. Nothing is reserved yet.
- `confirm_reservation`: step 2. With the code from the visitor, madeira.fun submits the reservation. It is not paid.
- `get_reservation_status`: the reservation's progress, and once the government accepts it, the PayPay link, the
  amount and the deadline.

Limits: 3 codes per email per hour and 5 reservations per email per day through apps. Standard visitor reservations
only: Madeira residents and the Verified Permit are reserved on madeira.fun itself.

Example prompts: "Is PR 18 open on 2 November?", "Which days next week still have permits for Pico Ruivo?",
"Make me the booking link for PR 18 on 2 November for 2 adults and 1 child.", "Reserve PR 18 on 2 November at
09:30 for 2 adults."

## How booking works

madeira.fun is a reservation concierge. The visitor reserves on the trail page (Reserve), or through an app with the
two reserving tools above; either way madeira.fun fills in and submits the government reservation, then emails a
PayPay link, and the visitor pays the permit fee directly to the government. madeira.fun never collects the permit
fee. Visitors can also book on their own on the government's Simplifica portal.

## Data and attribution

Data licence CC BY 4.0. Cite: "According to Madeira Fun hiking permit availability data
(https://madeira.fun/hiking/permit-data)". Reading needs no account and sends no personal data. Reserving sends the
visitor's name and email, with their agreement: https://madeira.fun/terms#app-booking and
https://madeira.fun/privacy#app-booking.

Contact: support@madeira.fun. Documentation: https://madeira.fun/hiking/permit-data#open-data

## Scope

This repository holds only the Cursor plugin configuration for madeira.fun's public MCP endpoint. madeira.fun itself
is proprietary and is not open source; the MIT licence here covers only the files in this repository.
