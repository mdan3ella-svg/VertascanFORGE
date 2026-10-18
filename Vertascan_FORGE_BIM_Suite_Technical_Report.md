# Vertascan FORGE BIM Suite
## Technical report · Release 12
**Define. Iterate. Produce.**

### Executive summary
Vertascan FORGE BIM Suite is a lightweight, browser-hosted architectural concept design suite combining five specialized workspaces: Unified Model, Solid Lab, Space Lab, Drafting, and BIM Studio. It is best suited to feasibility, schematic architectural design, architectural education, early BIM component modeling, and presentation-oriented documentation. It is not yet a replacement for a certified production BIM/CAD platform.

### Software architecture
- **Delivery:** Standalone HTML shell with embedded workspace engines; usable on GitHub Pages. Some 3D dependencies require an internet connection.
- **Shared project foundation:** Unified Model and Solid Lab store separate semantic collections in a versioned project record, commit edits transactionally, and share history and recovery. A shared project document does not mean their objects are automatically equivalent.
- **Legacy workspaces:** Space Lab, Drafting, and BIM Studio operate as isolated embedded applications with their own native states and histories. Their project data can be backed up by the host, but direct geometric change propagation is not implemented.
- **Geometry:** Existing conceptual geometry and limited Boolean/NURBS demonstration functions. No integrated exact OpenCascade B-rep kernel.
- **Interoperability:** Native project JSON and workspace-level drawing/model export tools are available. Complete IFC import/export and validated round trips are not supported.
- **Quality:** Source-level syntax checks have been performed; comprehensive browser, performance, accessibility, geometry, and data-loss regression testing remains necessary.

### Workspace capabilities
| Workspace | Main purpose | Recommended use | Caution |
|---|---|---|---|
| Unified Model | Conceptual BIM components and synchronized plan/3D representation | Walls, slabs, columns, room concepts, quantities | Limited hosting and cross-workspace dependencies |
| Solid Lab | Primitive 3D geometry, basic Boolean studies, NURBS curves | Test forms and volume relationships | Not exact general B-rep |
| Space Lab | Spatial arrangement and massing studies | Brief, program, site feasibility, adjacency | No automatic BIM coordination with Unified Model |
| Drafting | 2D drawing, layers, hatches, annotation | Schematic diagrams and preliminary documentation | Validate scale, snaps, dimensions and plots |
| BIM Studio | Building-system concept workflows | Levels, preliminary structural and MEP design | Independently stored, not construction-authoritative |

### Use case A — Preliminary site feasibility
1. Define the project brief, site constraints, target program and approximate levels outside the app.
2. Open **Space Lab**. Sketch a footprint and arrange preliminary spaces or volumes.
3. Check approximate fit, circulation and broad area assumptions.
4. Save the Space Lab state or export a reference; move to **Unified Model** and recreate the approved geometry as semantic BIM components where needed.
5. Review the plan and 3D view, inspect quantities and archive a `.forge.json` project snapshot.
**Deliverable:** Preliminary massing, spatial diagrams and an annotated feasibility concept. **Limit:** Cross-workspace updates are manual.

### Use case B — Schematic architectural BIM study
1. Open **Unified Model**. Set working dimensions and create walls, slabs, columns and rooms using supported commands.
2. Use the model's snapping and editing tools to refine locations and sizes.
3. Switch between 2D and 3D views to check the same Unified Model objects.
4. Make a measured change, inspect associated geometry and basic quantities; use undo/redo if required.
5. Export or back up the project before handing information to another application.
**Deliverable:** Structured early architectural model and preliminary takeoff. **Limit:** Hosted elements and associative construction documentation are incomplete.

### Use case C — Form exploration and drawing presentation
1. Open **Solid Lab** to create and edit conceptual volumes, Boolean configurations and NURBS curve studies.
2. Save a model transaction; confirm the shared project history can restore the prior state in integrated workspaces.
3. If the architectural model needs the concept, use only supported/manual conversion workflows and verify the resulting element type and dimensions.
4. Open **Drafting** to create explanatory linework, labels, hatches and a presentation sheet.
5. Export the drawing in a supported format and save a complete FORGE project backup.
**Deliverable:** Concept form studies and schematic presentation drawings. **Limit:** Drafting and Solid Lab are not automatically linked.

### First-project tutorial workflow
**Define:** Start in Space Lab with a site/building program and rough area targets. Save the initial design state.

**Iterate:** In Unified Model, create a small test assembly (four walls, a slab, a column), inspect it in plan and 3D, change one dimension, test undo and redo, then make a project backup. Use Solid Lab for alternative forms only when they can remain conceptual.

**Produce:** Draft explanatory diagrams in Drafting, inspect preliminary building assemblies in BIM Studio, and export needed workspace files. Review dimensions manually across legacy workspaces before issuing external information.

### Controls and safe working procedure
- Use workspace-native pan, zoom and orbit tools; keyboard commands may differ between legacy editors.
- In supported CAD views, use snap markers, object selection and numeric dimension controls where provided; verify measured geometry after modifications.
- Treat a session backup as part of the workflow: periodically save a downloadable `.forge.json` file, especially before large edits or importing files.
- After importing a project, check object counts, drawing scale, project integrity and viewport appearance.
- Do not assume changes made in Space Lab, Drafting or BIM Studio appear automatically in Unified Model.

### Engineering risks and improvement priorities
1. Complete adapters connecting Space Lab, Drafting and BIM Studio to the authoritative project store, with deterministic stable IDs and reversible transactions.
2. Consolidate camera controls, snapping and hit-testing using one tested input-handling layer.
3. Adopt robust topology and a genuine B-rep kernel, with geometric tolerance and serialization tests.
4. Complete and verify IFC geometry and property round-trips using representative IFC fixtures.
5. Add browser-based interaction, migration, data-recovery and performance test suites.
6. Improve progressive rendering, lazy geometry loading, Web Worker processing and accessibility.

### Scope and professional limitations
This build is suitable for **concept development and evaluation**. Geometry, quantities, code-related interpretations, technical dimensions, structural/MEP content and external exchange files must be independently checked before any professional or construction use. Shared storage/history currently applies to Unified Model and Solid Lab; the other three workspace engines are preserved but remain independently edited.
