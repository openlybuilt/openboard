# Diagram design

Use this when the brief is complex or includes an image. These rules draw on [Eraser Diagrams' design principles](https://github.com/eraserlabs/eraser-diagrams): express relationships, hierarchy, and containment as data; use a consistent visual grammar; and judge the measured result rather than trusting authored coordinates.

1. **Extract the story.** Record the diagram's purpose and reading order. List every visible entity, its label, its parent group or lane, and each connection with direction and decision label. If a detail in a reference is illegible, do not invent it; use a neutral label or ask if it changes meaning.
2. **Choose the structure.** Use frames for ownership boundaries, departments, or swimlanes. Use repeated shapes and dimensions for repeated roles. Use distinct fills sparingly to distinguish domains, actors, states, or exceptions.
3. **Place groups before details.** Give a primary reading direction. Reserve at least 24 px between peer cards and wider corridors for return paths or multiple arrows. Keep sibling shapes aligned. If the builder cannot find a clear route, widen the gap or canvas instead of forcing an arrow through content.
4. **Route deliberately.** The builder avoids cards, standalone text, and frame titles, then checks the exported arrows again. Use `axis` for a preferred entry side and `via` for a return path or cross-group handoff. A `via` route that crosses content is replaced with a clear automatic route and reported. Put short branch labels near their decision with `labelAt`; the builder moves them if that position is crowded.
5. **Review the preview.** Check for missing entities and edges, reversed directions, text clipping, unnecessary line crossings, indistinguishable roles, and ambiguous branches. Adjust the JSON and regenerate. The preview is for review; the `.openboard` file is the editable result.

For an architecture reference, verify every boundary and cross-boundary path. For an organization chart, verify reporting levels and sibling order. For a swimlane process, verify actor ownership, decision outcomes, exception loops, and handoffs between lanes.
