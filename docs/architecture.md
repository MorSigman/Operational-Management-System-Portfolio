# Architecture

## High-level design

The application is a client-heavy single-page app with no dedicated
backend server. All business logic lives in the frontend; a managed
Postgres backend provides persistence, authentication, and realtime
change notifications.

```
React / TypeScript UI
        │
        ▼
Local cache layer (instant read/write, offline-first)
        │
        ▼
Sync engine (diff + per-record push/pull)
        │
        ▼
Managed Postgres backend (data, auth, realtime)
```

## Local-first, cloud-synced

Every module reads and writes through a small local storage abstraction,
exactly as if the app had no backend at all — this keeps the UI instantly
responsive regardless of network conditions and makes the app fully usable
offline (e.g., on a shop floor with unreliable connectivity).

A separate sync layer sits behind that abstraction and is invisible to the
UI code:

- it intercepts every local write
- diffs it against the last known cloud state
- pushes only the changed record upstream (never a bulk overwrite of a
  whole collection)
- subscribes to realtime changes from the backend and merges remote
  updates back into the local cache, with self-echo suppression so a
  client never re-applies its own change

This design means concurrent edits by different users are naturally
conflict-free as long as they touch different records — there is no
last-write-wins race at the collection level.

## Authentication & access

Authentication is handled by the backend's managed auth service. The
frontend never talks to the database directly with elevated privileges —
all access is scoped to the authenticated user's session, with
authorization enforced server-side rather than trusted to the client.

## Engineering drafting & BOM engine

The drafting tool models a room as a set of walls and detects enclosed
spaces automatically. From that geometric model, a dedicated calculation
engine derives:

- exact panel counts and dimensions for walls and roof
- corner piece requirements, including diagonal/angled corners
- door assembly specifications (frame, leaf type, dimensions)
- insulation and hardware quantities

Pricing is computed live from the same model, using a layered price-list
system (system default → project override → room adjustment).

## AI-assisted input

A vision-capable AI model is used as an input method, not as a core system
dependency: it converts a photographed hand-drawn sketch into the same
structured wall/room data format the drafting board already understands,
so the rest of the pipeline (BOM, pricing, 3D preview) is unaffected by
whether the input came from AI interpretation or manual drawing.

## 3D visualization

A lightweight 3D renderer builds a real-time preview of the modeled
structure (walls, panels, doors, roof/floor) directly from the same
geometric model used for the BOM calculation, so the visualization is
always consistent with the computed bill of materials.
