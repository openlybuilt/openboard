# Diagram specification

The builder accepts JSON with `title`, optional `canvas`, `elements`, and `connections`. Coordinates are absolute pixels. IDs are unique strings. Put large containers before their contents so they render behind them. An optional `container` names a `frame` element and is saved as its OpenBoard `frameId`.

```json
{
  "title": "Service request",
  "canvas": { "width": 900, "height": 540, "background": "plain", "color": "#ffffff" },
  "elements": [
    { "id": "team", "type": "frame", "x": 40, "y": 90, "width": 820, "height": 390, "label": "Service team", "fill": "#f4f7fb", "stroke": "#8094b0" },
    { "id": "request", "type": "rectangle", "container": "team", "x": 90, "y": 230, "width": 210, "height": 90, "label": "Request received", "fill": "#e8f2ff" },
    { "id": "review", "type": "rectangle", "container": "team", "x": 570, "y": 230, "width": 210, "height": 90, "label": "Review request", "fill": "#e8f2ff" }
  ],
  "connections": [{ "from": "request", "to": "review", "label": "assign" }]
}
```

## Elements

| Type | Key fields | OpenBoard use |
| --- | --- | --- |
| `rectangle`, `ellipse`, `diamond` | `x`, `y`, `width`, `height`, `label` | Editable shape with a bound text label. |
| `frame` | Shape fields; `label` names the frame | Native editable frame; use for groups, lanes, or page regions. |
| `text` | `x`, `y`, `text`, `fontSize` | Standalone text. |
| `code` | `x`, `y`, `width`, `height`, `code`, `language`, `filename` | OpenBoard code block. |
| `line`, `arrow`, `freehand` | `x`, `y`, `points` | Points are `[x,y]` offsets from the element origin. |

Shape fields: `fill`, `stroke`, `strokeWidth`, `dashed`, `fontSize`, `textColor`, and `container`. Colors must be six-digit hex codes or `transparent`. The default canvas is white and plain; `background` may be `plain`, `dots`, or `grid`.

Connections use `from` and `to` shape IDs, optional `label`, `labelAt`, `stroke`, `dashed`, `axis`, and `via`. `axis` is `auto`, `vertical`, or `horizontal` and controls which sides connect. `via` is a list of absolute `[x,y]` waypoints; the builder inserts elbows between diagonal waypoints. Without it, the builder makes an orthogonal route between the selected sides. `labelAt` positions a connection label at an absolute `[x,y]`. Add waypoints when a route must avoid a container, shape, or label. A connection is saved as an editable, bound OpenBoard arrow.

## Designing from references

- **Architecture:** Establish containers first, then services within each boundary. Use one color family per domain and keep cross-boundary arrows visibly distinct.
- **Organization chart:** Place leaders above reports, align siblings, and use repeated card dimensions. Route each branch through a shared horizontal level when it helps reveal hierarchy.
- **Swimlane process:** Give each actor a horizontal frame, put tasks within its lane, and reserve clear corridors between lanes for transitions and return loops.
- **All diagrams:** Keep labels short, use font sizes that remain readable in the preview, and inspect every arrow endpoint. If an image's content is unclear, preserve its visible relationships and avoid inventing missing labels.
