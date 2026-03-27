# Mesh Canvas

Collaborative real-time drawing across the Macula federated relay mesh.

Each node has a cursor. Strokes flow cross-relay — draw on a node connected to relay00 in Nuremberg and it appears instantly on a node connected to relay01 in Helsinki.

## Mesh Topics

| Topic | Purpose |
|-------|---------|
| `{realm}.hecate.canvas.strokes` | Drawing strokes (sender, points, color, width) |
| `{realm}.hecate.canvas.cursors` | Cursor positions (sender, x, y) |
| `{realm}.hecate.canvas.clear` | Canvas clear events |

## Architecture

- Canvas state is ephemeral (no persistence)
- Each stroke is a list of points with color and width
- Cursor positions broadcast at ~10Hz for live presence
- Each sender gets a unique color (derived from node name hash)

## Demo Value

- Most visually striking demo
- Real-time collaboration across geographic relays
- Kill relay01 in Helsinki, strokes from Nuremberg still reach Linode
- Shows latency characteristics of relay mesh
