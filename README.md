# Norvane Finance's complaint platform: group repo

This repository is your group's copy of **Norvane Finance's complaint
platform**, the running case of the *Operating AI Systems at Scale* course.
Norvane Finance is a fictional European consumer-finance company; the
complaints its platform handles are real, written by consumers to the US
Consumer Financial Protection Bureau (CFPB) and published in the public
domain.

The platform runs on your laptop with Docker: a large language model (LLM)
reads each complaint and routes it to a team, people answer it, and a
15-business-day clock runs. Your group **operates** it: you set its service
level objectives (SLOs), write what to do when they burn, watch it from the
inside, document it for a regulator, and organise the team that runs it. At
the end you defend those choices, as the team that would be woken at three in
the morning.

## Team

| Name | GitHub | Role |
|---|---|---|
| | | |
| | | |
| | | |
| | | |

## How this repo grows

| Lesson | What your group adds | Where |
|---|---|---|
| L01 · SRE for AI | Service level objectives and their error budgets, three runbooks, the degradation hierarchy, the on-call charter, a first decision record | `docs/slos.md`, `slo/slos.py`, `docs/runbooks/`, `docs/degradation.md`, `docs/on-call-charter.md`, `docs/adr/` |
| L02 · Observability at scale | The platform instrumented end to end, the observability dashboard, a blameless post-mortem, one chaos experiment | the lab, `docs/` |
| L03 · Governance and the EU AI Act | A model card and data sheet, the AI Act classification and its gap analysis, for Norvane Finance's credit model | `docs/` |
| L04 · The AI platform team | The team structure and its RACI (who is Responsible, Accountable, Consulted, Informed), the operational maturity assessment | `docs/` |
| L05 · Review | Project clinic: what the defence will ask | |
| L06 · Project defences | What your group defends | |

Starter files for later lessons arrive as **pull requests** opened by the
teaching team. Review and merge them like any other change.

## How we work

- **Every change goes through a pull request,** reviewed by another member
  before it reaches `main`.
- **One decision, one record** in `docs/adr/`: an objective, an alert, a
  degradation rule, a rota. Every member writes at least one. At the oral
  defence, each of you defends one of the group's choices, unprepared.
- **The commit history is graded.** Commit in small steps, with messages that
  say why.
- **A runbook nobody has rehearsed is a guess.** Every runbook says when it
  was last run on the lab, with which switch, and what the dashboard showed.
- **Every figure says where it came from:** the date, the lab's switches and
  level, and how long you measured.

## Start the lab

Docker Desktop running, then in a terminal, in this folder:

```bash
docker compose up -d --build
```

Grafana's dashboard is at http://localhost:3000, Prometheus's alerts at
http://localhost:9090/alerts. Everything else (changing a port, the fault
switches, the degradation levels, regenerating the SLOs, the optional real
model) is in [`LAB.md`](LAB.md).

## Layout

```
compose.yaml, Dockerfile   the lab: nine containers
lab/                       the platform's services and the simulated world
slo/slos.py                your SLOs: the one file to edit (slo/build.py writes the rest)
prometheus/, grafana/      generated rules and dashboard, and their settings
data/                      the 8,000 complaints and where they come from
docs/
  slos.md                  your objectives and error budgets, in words
  runbooks/                one runbook per failure, and why these three
  degradation.md           the four levels, and what each loses
  on-call-charter.md       who is woken, for what, and what happens after
  adr/                     one decision record per decision
LAB.md                     how to run, break and degrade the lab
```

## Keys

The lab needs no key: its LLM is a stand-in that costs nothing. If you point
it at a real model (`LAB.md`), the key goes in a `.env` file, which
`.gitignore` already excludes; copy `.env.example` to start one. **If a key
reaches GitHub, even for a minute, tell the teaching team at once** so it can
be revoked. Deleting the commit does not help: the key has already been
copied.

## Data

The complaints are from the CFPB's Consumer Complaint Database, in the public
domain; `data/README.md` says which export, how the sample was drawn, and what
was removed. Some letters still name real companies: never quote one in your
documents.

## Ownership

**No licence is granted for this repository.**
- **The template:** this README, the lab, the `docs/` templates and the folder
  structure remain the course author's intellectual property. Do not reuse
  them outside the course.
- **Your work:** what your group writes here belongs to your group.
