# Memo

## Event architecture

- `bonsai/events` is the calendar-facing canonical event ledger.
- `template/event.yaml` is the canonical common Event schema.
- Domain repositories remain the source of truth for their own event data.
- `event-comvu` collects, normalizes, deduplicates, and connects domain data to the calendar ledger.
- Weekly event files live under `events/Wxx.md`.
- Gemini reads the weekly files and can hand them to gws for Google Calendar.
- ICS is not required as the canonical format; the common fields are sufficient.

## Domains

- `idol` → `bonsai/idol-live`
- `owarai` → `bonsai/owarai-live`
- `yose` → `bonsai/yose-db`
- `art` → `bonsai/art-event`
- `it` → connpass
- `dj` → `bonsai/dj-event`
- `festival` → `bonsai/festivals`

## Canonical fields

`id`, `date`, `start`, `end`, `title`, `place`, `address`, `price`, `paid`, `status`, `source`, `note`

## Paid-event rule

- Paid events must be marked `paid: YES`.
- If the price is unknown, use `price: 料金要確認` and `paid: UNKNOWN`.
- Do not infer an unknown fee as free.
