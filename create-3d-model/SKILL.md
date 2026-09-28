---
name: create-3d-model
description: Create or refine editable 3D assets from text descriptions, photographs, sketches, concept art, or multiple views. Use for modeling objects, props, characters, or environment assets with proportion planning and rendered validation; not for image-only depictions of 3D objects.
---

# Create 3D Model

Act as a 3D artist and technical artist. Turn the user's brief into an editable asset. Match silhouette and major proportions before adding detail. Use Blender by default when no application is specified; respect another requested application and adapt this workflow to its capabilities.

## 1. Understand the brief before creating geometry

Read supplied files and relevant project instructions. Establish the subject, required features, style, explicit exclusions, intended use, known dimensions, units, and output formats. Honor supplied polygon, texture, rigging, collision, or fabrication constraints.

Use reasonable stated defaults when information is missing. For a simple request, proceed with an editable static asset and preview. Do not require a questionnaire, concept generation, rig, multiple LODs, or approval between every pass. Ask only when missing information materially affects the result, such as a functional fit dimension or conflicting designs. Honor explicit user/project approval gates and reuse approval already given.

Choose the input path:

- **Images:** inspect the actual photographs, drawings, or concept art and read [reference-reconstruction.md](references/reference-reconstruction.md). Separate visible evidence, inferred construction, and unknown geometry.
- **Description only:** derive a compact design specification: primary masses, relative dimensions, component placement, shape language, materials, and distinguishing features. Label unspecified choices as design decisions, not observations. Preserve requested stylization or fantastical forms instead of imposing realism. Generated concept art is optional and does not replace the 3D deliverable.
- **Mixed inputs:** combine explicit requirements with reference evidence. Resolve consequential contradictions instead of averaging incompatible designs. Previously approved concepts constrain the model to the extent specified by the user.

Record enough of the brief and assumptions to guide modeling and correction. Keep this lightweight for simple assets.

## 2. Plan geometry and proportions

Decompose the asset into primary masses, secondary forms, repeated elements, and surface details. Identify symmetry, joints, curves, edge profiles, and plausible construction where relevant.

Declare coordinates and front direction. A useful Blender default is X = width, Y = depth, Z = up, front = -Y; use project conventions if different. Use a known dimension when available. Otherwise choose a normalized reference, such as width = 1, and label any assigned physical size as assumed.

Store major dimensions and placements as named parameters with units or ratios. Derive dependent dimensions rather than scattering unexplained constants. Keep ambiguous parts easy to change.

Choose modeling methods per component:

| Need | Suitable starting point |
| --- | --- |
| Mechanical or architectural forms | Primitives, extrusion, bevels, mirror, controlled booleans |
| Repeated parts | Linked instances, arrays, reusable generators |
| Tubes, cables, trim | Curves, sweeps, profile extrusion |
| Rounded or organic forms | Subdivision cages, sculpting, remeshing, deliberate topology |
| Rule-based distributions | Geometry Nodes or equivalent procedural systems |
| Animation or fabrication | Construction appropriate to deformation or a solid physical object |

Prefer editable, economical construction. Do not force organic forms into piles of primitives or prohibit custom meshes when appropriate. Dense arbitrary vertex lists are a poor substitute for a coherent shape model.

## 3. Establish a reproducible working scene

Verify the available application and execution path. For an existing Blender session, perform a read-only scene inspection before editing; registered tools alone do not prove a live connection. If unavailable, use a verified local Blender executable when suitable. If no modeling runtime is available, a script may be supplied as an explicitly unexecuted partial deliverable; do not claim a model was built or validated.

Preserve source files and unrelated scene contents. Work in a dedicated asset collection or new scene. Rebuild only clearly owned generated content; do not clear the user's entire scene. Separate asset geometry from cameras, lighting, and validation helpers.

For procedural work, deliver a deterministic build script with named parameters, component functions, meaningful object/material names, fixed random seeds where used, and documented input dependencies. A clean scene plus those inputs should reproduce the asset. Re-running should replace its own output without duplicating it. Include geometry, materials, relevant UV setup, modifiers, and validation cameras/lighting.

For sculpted or manually authored assets, the editable native file is authoritative. Preserve useful layers/modifiers and record procedural stages; do not promise scripted reconstruction of unrecorded manual work.

Use APIs supported by the installed application. Consult current official documentation through available documentation tools for version-sensitive syntax or behavior instead of guessing shader sockets or modifier settings.

## 4. Build in passes

### A. Blockout

Create the silhouette, primary masses, and major proportions. Render a neutral clay preview before fine detail. Check a useful three-quarter view and an independent view revealing depth or the back. For reconstruction, also use a reference-matched camera.

Correct silhouette, dimensions, negative spaces, and component placement first. A pleasing camera angle is not proof of correct geometry.

### B. Structure

Add secondary forms, openings, joints, panels, handles, folds, or anatomical transitions as appropriate. Add meaningful edge treatment. Verify booleans and subdivision do not distort primary forms.

### C. Materials and detail

Choose detail according to viewing distance and intended use. Model features affecting silhouette, parallax, deformation, or fabrication; use textures, normals, or bump for appropriate surface-only detail.

For physically based rendering, define coherent base color, metalness, roughness, and relevant transmission/IOR. Use Principled BSDF in Blender where appropriate. Match stylized shading when requested. Add microstructure and wear only when supported by the brief, at a plausible scale and intensity. Do not use procedural noise to disguise incorrect geometry.

Create UVs when the material or target pipeline needs them. Procedural shaders may need baking for export; modifiers and instances may need conversion on an export copy.

## 5. Render, critique, and correct

Read [validation-and-delivery.md](references/validation-and-delivery.md) for checks relevant to the intended use.

Render under neutral lighting and inspect the actual resulting images. Keep camera, lighting, framing, and color management consistent between comparison iterations. Separate presentation renders from diagnostic views when needed.

Evaluate in order:

1. Silhouette and overall proportions.
2. Component placement, depth, angles, and negative spaces.
3. Curvature, transitions, and edge profiles.
4. Material response and color relationships.
5. Missing or excessive details.

For image-based work, compare against the source and check camera fit before compensating with geometry. For description-based work, compare against the brief, dimensions, required features, and consistency across views. Do not claim a photographic match where no photo exists.

Identify up to five concrete discrepancies with the greatest visual impact. Change the relevant parameters or components, render again, and inspect whether those discrepancies improved. Prefer measured differences; label visual estimates as estimates. Keep a short correction record for substantial work.

Continue while meaningful defects remain and evidence supports a correction. Stop when the brief is met and remaining changes are minor, or missing evidence, unavailable tools, or an agreed resource limit prevents progress. Report unresolved defects. Do not loop indefinitely on uncertain hidden details or treat successful script execution as visual approval.

## 6. Deliver the asset and evidence

Save the editable native asset, requested exports, actual preview renders, and any build script with necessary inputs. Reopen the saved asset and inspect requested exports where target tools are available. Keep assumptions and external dependencies discoverable without unnecessary paperwork.

Link the native asset and a real preview in the handoff. Include scripts and exports when present. Summarize what was checked and distinguish observed success from untested compatibility. Do not claim game readiness, printability, deformation quality, or reference accuracy without corresponding checks.
