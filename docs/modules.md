# Modules

A breakdown of each functional area of the platform. All examples below are
generic/illustrative — no real business data is shown anywhere in this
repository.

## Production Management

The operational core of the system.

- Dashboard with live KPIs across all active projects (readiness %,
  components required vs. produced)
- Project detail view: rooms, components, quantities, per-item production
  status, priority, and pricing (with per-project and per-room overrides)
- Production floor view: every active component across every project,
  filterable by production stage and priority
- Visual timeline (Gantt) of all projects
- Drag-and-drop field-team scheduling, with conflict detection against the
  manufacturing schedule
- A dedicated board for a two-stage installation workflow (structure
  installed first, a dependent component measured and manufactured
  separately, then installed later)
- An "exceptions" feed surfacing urgent or defective components sorted by
  deadline
- A "returns" registry that suggests reusing returned/cancelled components
  in new matching projects instead of manufacturing from scratch
- Configurable price lists at the system, project, and room level

## Engineering Drafting & Automatic BOM

- Interactive 2D drawing board for walls and enclosed spaces, with
  automatic space detection
- Automatic computation of the full bill of materials (panel counts and
  sizes, corner pieces, door assemblies, insulation, hardware) directly
  from the drawing
- Live pricing tied to the active price list
- 3D visualization of the modeled structure
- AI-assisted conversion of a photographed hand-drawn sketch into
  structured drafting data
- Printable, per-station production work-order packets generated from the
  BOM

## Warehouse & Procurement

- Stock tracking with computed current inventory from a movement ledger
- Supplier directory
- Purchase orders with a status pipeline
- Configurable recipes linking warehouse consumption to production BOM
  output

## HR

- Monthly attendance calendar with department-level staffing alerts
- Weekly shift scheduling workflow
- Leave request tracking across multiple leave types
- Employee and department directories with headcount vs. target staffing

## Financial / Invoice Control

- Milestone-based payment plans (e.g. upfront / on production readiness /
  on installation / on completion), synced live with actual production and
  installation status
- Automatic flagging of milestones that have matured but not yet been
  billed
- Quote tracking with a live comparison between quoted price and
  system-calculated cost

## Logistics

- Fleet management with expiry tracking (inspection, insurance)
- Categorized contact directory
- A procedures/documentation library with automatic version incrementing
  on file updates
- Training records with expiry tracking
- Regulatory/compliance and licensing tracking
- General follow-up/to-do tracking

## Task Management

- Kanban-style task board with priority and assignment
- Recurring operational routines (daily / weekly / monthly) with
  completion logs
- A consolidated reminders feed across the organization
