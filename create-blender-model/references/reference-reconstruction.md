# Reconstructing from visual references

Use for photographs, sketches, technical drawings, concept art, and multi-view sheets. Photographs contain perspective and lens effects; sketches and generated multi-view sheets may be internally inconsistent.

## Read evidence

Inspect the image itself, not just its filename or caption. Identify:

- Silhouette, major masses, symmetry, and repeated elements.
- Relative dimensions, thickness, overlaps, openings, and occlusions.
- Curvature, bevels, edge profiles, seams, and construction clues.
- Materials and finish; apparent features that may be lighting or reflections.
- Hidden faces, uncertain depth, and obscured connections.

Separate **observed**, **inferred**, and **unknown**. A front photograph may show a handle's width but weakly constrain its depth. Do not invent a detailed back and describe it as observed evidence.

Separate the object from its surroundings. Shadows, camera borders, plinths, and background objects are not automatically part of the requested model.

## Scale and multiple views

Choose a visible reference dimension and express other dimensions as ratios. One photograph without a known measurement cannot uniquely establish physical scale or hidden geometry. Perspective and foreshortening invalidate naive conversion of pixel ratios into world dimensions.

With multiple images, identify shared landmarks and consistent component identities. Check whether they show the same version, pose, or articulation. Use the view best constraining each dimension; do not duplicate conflicting geometry to satisfy incompatible views.

Ask for another view or measurement only when uncertainty materially affects fidelity or function. Otherwise choose a simple, plausible, editable assumption and disclose it. Exact-fit or manufacturing work requires actual dimensions and tolerances.

## Fit a comparison camera

Create a dedicated camera, conventionally `REFERENCE_CAMERA`, for the main reference and additional named cameras for other relevant views.

Estimate projection type, azimuth, elevation, roll, perspective strength, focal length, distance, framing, and relevant lens distortion. Distance and focal length can trade off; single-photo estimates are approximate. Orthographic projection suits true orthographic drawings, not every reference.

Use silhouette landmarks, visible face ratios, and vanishing lines to fit the camera against the blockout. Check geometry from independent views. Do not distort the asset to compensate for a camera mismatch or reproduce lens distortion in its mesh.

## Compare fairly

Use reference-matched views for alignment and neutral diagnostic views for construction. Approximate source lighting when needed to assess appearance, without baking reflections or cast shadows into base color.

Use side-by-side views, aligned overlays, or silhouette comparisons where practical. Match framing and aspect ratio. Raw pixel differences are usually not meaningful across different backgrounds, exposure, or lighting.

For signs, text, mirrored parts, or repeated motifs, inspect each relevant instance, including the back. Symmetric placement does not imply mirrored lettering. Preserve readable orientation and specified differences between sides.

State which faces are grounded in evidence and which remain designed approximations. Additional detail cannot remove uncertainty absent from the source.
