# Validation and delivery

Select checks by intended use. Do not impose every production discipline on every small asset.

## Shared checks

- **Shape:** inspect silhouette, depth, component placement, and negative spaces from complementary views. Include the back when construction or duplicated features matter.
- **Geometry:** inspect normals, shading, unintended holes/intersections, loose geometry, z-fighting, boolean artifacts, and excessive density. Open surfaces or intersecting parts may be intentional in render assets; manifoldness is not universal.
- **Transforms:** verify dimensions, units, orientation, origin/pivot, and transform behavior. Apply transforms when needed for the target while preserving modifier behavior and an editable source.
- **Materials:** check missing textures, relevant UV seams/stretching, assignments, and response under neutral light.
- **Saved artifact:** save and reopen the native file, verify the asset is present, and check external resources resolve. An unsaved scene or render alone is not an editable model deliverable.
- **Evidence:** inspect actual render files for correct framing and visible content. A completed render process can still produce a blank or irrelevant image.

## Destination-specific checks

| Destination | Relevant validation |
| --- | --- |
| Still render | Intended camera/resolution, silhouette, material response, visible surfaces |
| Game / real-time | Requested triangle/texture budgets, units/axes, pivot, material support, exported geometry; LODs/collision only if in scope |
| Animation | Deformation topology, articulated parts/pivots; representative pose checks when a rig is in scope |
| Printing / fabrication | Closed intended solids, wall thickness, self-intersections, real dimensions/tolerances, separate-part fit; slicer checks when available |
| Editable concept | Clear components, editable construction, key dimensions, stated assumptions, useful previews |

Do not infer target compatibility from a valid file extension. If the destination application or device cannot be tested, state which checks were performed and which remain unverified.

## Reproducibility and export

For scripted assets, run the build in a clean scene and verify its output. If reuse in a populated scene is promised, also verify a repeated build does not duplicate owned objects or modify unrelated contents. Include seeds and necessary input dependencies.

Preserve the editable source before destructive export conversions. Export only intended objects, excluding diagnostic cameras, lights, and helpers unless requested. Bake/adapt unsupported materials when required. Reimport exports into a separate scene or inspect them in the destination application to catch missing components, orientation changes, or material loss.

Use portable relative paths or pack dependencies where appropriate. Include textures and inputs that cannot be embedded. Do not report a standalone package if it depends on unprovided absolute paths.

## Handoff

Follow the project's organization. Otherwise a native asset with optional `scripts/`, `textures/`, `renders/`, and `exports/` folders is sufficient; create only folders used.

Show a real preview and link the native file and requested exports. For substantial reconstructions, include a concise note with dimensions, inferred geometry, build instructions, validation results, and unresolved discrepancies. Keep simple-asset handoffs brief.
