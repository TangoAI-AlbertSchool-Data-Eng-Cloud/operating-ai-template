## What

## Why

Link the decision record or the issue this change implements.

## How it was checked

For a change to `slo/slos.py`: `python slo/build.py` was run, and the
dashboard shows the new objective. For a runbook: the date it was rehearsed on
the lab, the switch used, and what the dashboard showed.

## Checklist

- [ ] No API key, `.env` file or secret
- [ ] Every new figure says its date, the lab's switches and level, and how long it was measured
- [ ] `docs/slos.md` and `slo/slos.py` still agree
- [ ] Reviewed by another group member
