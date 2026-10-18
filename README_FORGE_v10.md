# Vertascan FORGE v10 — Workspace Movement Controls

## Updated
- Space Lab 2D: prevent right-click editing; pointer-specific gesture handling; cancellation rollback; normalized wheel zoom; horizontal trackpad scrolling; context menu suppression.
- Space Lab 3D: orbit / pan distinction (left orbit, middle/right/Shift pan), pointer capture, drag-versus-pick suppression, normalized zoom.
- Unified Model: Move activates only when the pointer starts over the intended object; no accidental move of an earlier selection; duplicate gesture guard.
- Solid Lab: gesture ownership and drag cleanup on focus loss.

## Default interactions
- Wheel: zoom near pointer where supported.
- Middle/right drag: pan in supported editors.
- Space + drag: pan in Unified Model / Solid Lab.
- Space Lab 3D: left drag orbit; middle/right/Shift drag pan.
- Escape: abandon unfinished Unified Model polygon operation.

## Limitations
- Legacy Space Lab 3D depends on pinned Three.js for enhanced rendering; its native fallback remains.
- A production browser regression suite and complete integration across all legacy CAD editors remain outstanding. No industrial-grade CAD or complete IFC roundtrip implied.
