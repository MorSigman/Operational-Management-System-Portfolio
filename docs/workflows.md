# Key Workflows

A few end-to-end workflows that illustrate how the modules connect.

## 1. From sketch to shipped product

1. A hand-drawn floor-plan sketch is photographed and interpreted by an AI
   vision model into structured wall/room data.
2. The result seeds the 2D drafting board, where it is refined.
3. The drafting engine automatically computes the full bill of materials
   and price for the room.
4. The room enters the production pipeline, moving through a multi-stage
   manufacturing process with per-component tracking.
5. Once ready, the room is scheduled for field installation.
6. A shipping form is generated, listing exactly which components/rooms are
   going out and any special handling notes for the field crew.
7. After installation, if a dependent component (such as a door) requires a
   separate on-site measurement, that step and the follow-up manufacturing
   and installation are tracked as their own linked workflow stage.

## 2. Payment milestone lifecycle

1. A payment plan is defined for a project (either a quick template or a
   custom set of milestones), each tied to a real-world trigger: immediate,
   production-readiness, installation-completion, or full project closeout.
2. As the project's actual production/installation status changes
   elsewhere in the system, each milestone's state updates automatically —
   no manual status re-entry.
3. When a milestone's trigger condition is met but it hasn't been invoiced
   yet, it surfaces on a "requires attention" feed for the finance team.
4. Invoice status (sent / paid / overdue) is tracked against each
   milestone, separately from the actual invoice document, which is issued
   through external accounting software.

## 3. Returns and component reuse

1. When a project or room is cancelled or a shipment is returned, its
   components automatically move into a returns registry — no manual
   re-classification needed.
2. When starting a new room with matching dimensions, the system
   proactively surfaces matching components already sitting in the returns
   registry, so they can be reused instead of manufactured from scratch.
3. If the returned status is reversed, the components are automatically
   moved back out of the registry.

## 4. Multi-user real-time collaboration

1. Every screen in the app reads and writes to a local cache, so the UI is
   always instantly responsive, even offline.
2. A background sync layer watches for local changes, compares them
   against the last known cloud state, and pushes only the changed record
   — never a whole-collection overwrite.
3. Changes made by other users arrive over a realtime subscription and are
   merged into the local cache automatically, updating the UI live.
4. Because synchronization happens at the level of a single record, two
   people editing two different projects (or even two different rooms in
   the same project) never conflict with each other.
