---
name: openboard
description: Create a new editable OpenBoard diagram from a written brief or reference image, with a visual preview and an importable .openboard file. Use for architecture diagrams, flowcharts, organization charts, swimlanes, and other whiteboards; not for account access or editing an existing board.
---

# Create an OpenBoard diagram

1. Read the brief and any attached reference images. Identify the message, audience, entities, hierarchy or lanes, connections, and labels. Ask only about a missing decision that would change the diagram's meaning.
2. Draft a compact JSON diagram using [the specification](references/diagram-spec.md). Keep containers and connections explicit. Use consistent shapes and colors for the same roles; reserve variation for meaningful distinctions. Place related items together, leave room for labels, and route lines away from text and other shapes.
3. Run `python3 scripts/build_board.py diagram.json --out output/board.openboard --preview output/board.svg` from this skill's directory. The builder needs only Python's standard library and does not connect to an OpenBoard server.
4. Inspect the SVG preview. Revise the JSON until labels, hierarchy, spacing, and routes are readable. Check that the `.openboard` file exists and the builder reports no errors. Give the user both files; they can import the board through OpenBoard's **Open** menu.

The image is a reference for structure and content, not a mandate to trace pixels. Preserve the relationships and layout logic when recreating an image. An SVG preview is only a review artifact; the `.openboard` file contains editable elements. This skill creates new boards only and does not access accounts.
