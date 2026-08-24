# Operational Management System — Portfolio Showcase

> **Portfolio Showcase**
>
> This repository presents a public, anonymized overview of a larger private
> production system I designed and developed end-to-end. Company-specific
> data, production source code, credentials, and confidential implementation
> details are intentionally excluded.

## Overview

An **ERP-lite operational management platform** built for a manufacturing
environment, replacing manual, spreadsheet- and messaging-based workflows
with a single, real-time, multi-user system used daily across an entire
organization — from the shop floor to the office.

I designed and built this system independently, end-to-end: data model,
business logic, UI, cloud sync architecture, and an AI-assisted engineering
tool for automatic bill-of-materials generation.

## What the system does

The platform covers the full operational lifecycle of a manufacturing
business:

- **Project & Production Management** — track manufacturing projects from
  intake through production, field installation, and completion, with
  per-component status, a multi-stage production pipeline, and field-team
  scheduling.
- **Engineering Drafting & Automatic BOM Generation** — an interactive 2D
  drafting tool that automatically computes a full bill of materials
  (panels, corners, doors, insulation, hardware) directly from a drawn
  floor plan, with live pricing and 3D visualization.
- **AI-Assisted Sketch Interpretation** — hand-drawn floor-plan sketches can
  be photographed and automatically converted into structured drafting data
  using an AI vision model.
- **Warehouse & Procurement** — inventory tracking, supplier management, and
  purchase-order workflows, linked to production consumption.
- **HR** — attendance calendars, shift scheduling, leave tracking, and
  department staffing overviews.
- **Financial / Invoice Control** — milestone-based payment plans that
  automatically flag when a project is ready to be billed, and quote
  tracking with live cost comparisons.
- **Logistics** — fleet, contacts, procedures (with automatic version
  tracking), training records, and regulatory compliance, all with expiry
  alerts.
- **Task Management** — Kanban-style task boards and recurring operational
  routines.

See [docs/modules.md](docs/modules.md) for a full capability breakdown per
module.

## Technical highlights

- **Real-time multi-user sync engine** — every screen reads/writes to a
  local cache as usual; a separate sync layer intercepts changes, diffs
  them against cloud state, and pushes/pulls updates at the
  individual-record level, so two users editing different records never
  overwrite each other.
- **Offline-capable, cloud-backed architecture** — the app is fully usable
  offline and transparently reconciles with the cloud when connectivity
  returns.
- **Automatic BOM engine** — derives exact material quantities, cuts, and
  pricing directly from a geometric floor-plan drawing.
- **AI vision integration** — converts unstructured hand-drawn input into
  structured engineering data.
- **Full RTL (right-to-left) interface**, built for daily use by
  non-technical shop-floor and field staff.

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | React 18, TypeScript, Vite, Tailwind CSS |
| Backend / Data | Supabase (PostgreSQL + Realtime), client-side caching |
| 3D Visualization | Three.js |
| AI | Claude (Anthropic) vision API for sketch interpretation |
| Auth | Supabase Auth |

## Documentation

- [Overview](docs/overview.md) — problem, context, and goals
- [Modules](docs/modules.md) — full feature breakdown per module
- [Workflows](docs/workflows.md) — key end-to-end business workflows
- [Architecture](docs/architecture.md) — technical design decisions

## Screenshots

_Coming soon — screenshots will be added here, reviewed and approved
individually to ensure no business-sensitive information is shown._

## What this repository intentionally does not include

- Production source code
- Real company, customer, employee, or supplier data
- Database schemas, credentials, or API keys
- Any connection to the live production system

---

This is a portfolio artifact. For questions about the project, feel free to
reach out.
