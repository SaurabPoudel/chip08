# CHIP-8 Emulator (Rust)

A simple CHIP-8 emulator implemented in Rust. The workspace contains a reusable emulator core, a desktop SDL2 frontend, and a WebAssembly build target.

**Crates**
- **`chip8_core`**: core emulator logic and state ([chip8_core/src/lib.rs](chip8_core/src/lib.rs)).
- **`desktop`**: SDL2-based desktop frontend that renders the display and maps keyboard input ([desktop/src/main.rs](desktop/src/main.rs)).
- **`wasm`**: WebAssembly-compatible crate for running in the browser (see `wasm/index.html`).
- **`games/`**: collection of CHIP-8 ROMs used for testing and demos.

**Quick Start (Desktop, Linux)**
Prerequisites: Rust toolchain and SDL2 development libraries.

On Debian/Ubuntu:

```bash
sudo apt-get install libsdl2-dev
```

Build and run the desktop frontend with a ROM (example `15PUZZLE`):

```bash
cd desktop
cargo run ../games/15PUZZLE
```

Controls: the keyboard mapping is in `desktop/src/main.rs` (keys are mapped to CHIP-8 hex keypad).

**WASM (Browser)**
Requires `wasm-pack` and a simple static file server.

```bash
cd wasm
wasm-pack build --target web
# then serve the directory (e.g. python -m http.server) and open index.html
```

**Notes**
- If you encounter SDL-related panics from event decoding, the desktop frontend contains a raw `SDL_PollEvent` loop to avoid enum-construction panics. See [desktop/src/main.rs](desktop/src/main.rs) for details.

**Contributing**
- Bug reports and PRs welcome. Keep changes scoped to a crate and add tests where appropriate.

**License**
- No license file included. Add a license if you intend to publish.
