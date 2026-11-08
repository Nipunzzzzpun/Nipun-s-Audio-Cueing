<p align="center"><img src="assets/Automation.png" alt="Automation" width="100%"></p>

## About

A single-page cue board for running sound effects, images and text live: for a show, a stream, a class, or a game night. Drop buttons on a dotted-grid stage, press them when you need them, and (optionally) wire them together with a node editor so one press can trigger a whole sequence.

No install, no build, no account. It's one `index.html`.

**Live site:** `https://<your-username>.github.io/Nipun-s-Audio-Cueing/`

## Features

- **Cue board**: place audio cue buttons, images and text on a snap-to-grid stage. Upload your own audio and images, rename, recolour and resize them.
- **Audio controls**: trim start/end, speed, volume and pitch per cue.
- **Copy / paste saving**: *Copy save* puts your whole board on the clipboard; *Paste save* restores it. Your board also autosaves in the browser.
- **Live sharing**: start a session and give friends the code. Everyone sees the same board and each other's cursors (peer-to-peer via PeerJS). Pick your own name and colour.
- **Node editor (automations)**: build logic that runs when a mapped button or key is pressed. Undo/redo (last 200 changes), drag-to-select, groups, wires that snap to pins, and a fullscreen mode.
- **Pan the board**: drag the background of the cue board to move around; the recenter button brings you back.

## Node editor

Open it with the third round button in the top dock. Add **Mapped Buttons** on the right (give them a key if you like), then drag nodes from the palette and wire them together by dragging from an output pin to an input pin. Click a pin to change its colour.

| Node | What it does |
| --- | --- |
| **Button Input** | Starts a chain when its mapped button / key is pressed |
| **Audio** | `play` and `stop` inputs, volume and pitch (typed or driven by a wire), and a `done` output when the sound ends |
| **Wait** | Delays the signal by N seconds (the border burns down as it runs); the time can be driven by a value wire |
| **Counter** | Passes the signal on every Nth press |
| **LOOP** | `start` / `break` inputs, "Loop until N" or "Loop forever", a `count` pin, an `each` output per loop and a `done` output when finished or broken |
| **VALUE** | Add, subtract, multiply or divide a running number; `run` and `clear` inputs; `by` and `start` can be driven by wires |
| **Number** | A fixed number other nodes can read; run it to set a VALUE |
| **IF** | Lets the signal through only if a comparison is true: **Value** mode (`<`, `>`, `=`, `≤`, `≥`, `≠`) or **Text** mode (Is, Isn't, Contains) |
| **AND / OR / NOR / XOR / XAND** | Logic gates over two inputs |
| **RANDOM** | Picks a random number in a range (min / max can be wired) and sends the signal down one randomly chosen wire |
| **Print** | Pops up a message at the bottom of the screen when the signal arrives |
| **Splitter** | A repeater with no delay: any number of inputs and outputs, with a routing menu for which input feeds which output. Hold it to edit the routing, hold a pin and drag it round the border, drag the corner to resize (bigger fits more pins) |
| **Light** | A lamp that lights while it's receiving a signal |

Any pin that holds a changeable value (volume, pitch, `by`, `start`, seconds, count, range, ...) has a blue value pin underneath it, so a wire can drive it.

Shortcuts and gestures in the editor:

- `Ctrl/Cmd + Z` undo, `Ctrl/Cmd + Shift + Z` or `Ctrl + Y` redo
- Mouse wheel to zoom, drag the background to pan
- Hold the background for a moment, then drag to select. Without `Alt` a node must be fully inside the box; hold `Alt` to select anything the box touches. A toolbar then offers Colour, Group, Move and Delete
- Hold `Ctrl` while dragging a wire to turn off pin snapping
- Click a pin to change its colour

## Hosting on GitHub Pages

1. Put `index.html` (and this README) in the repository root.
2. **Settings → Pages →** deploy from the `main` branch, `/ (root)`.
3. Open `https://<your-username>.github.io/<repo-name>/`.

The GitHub button on the page links back to the repository automatically when it's served from GitHub Pages.

## Notes

- Large audio files may not fit in the browser's autosave. Use **Copy save** to keep them.
- Live sharing needs an internet connection (PeerJS's public broker) and works best on modern Chrome, Edge, Firefox or Safari.
- Everything runs in your browser. Files you add are shared only with people in your live session.

## Built with

Plain HTML, CSS and JavaScript, [PeerJS](https://peerjs.com/) for sharing, and the Montserrat / Major Mono Display fonts from Google Fonts.
