# Mugetsu (Skua build)

> **This is the Linux Skua build of Mugetsu**, the game player bundled with [BonxieMux](https://github.com/JonasAlv/BonxieMux).
> BonxieMux downloads releases from this repository automatically.

Based on upstream [mugetsu-aqw/mugetsu](https://github.com/mugetsu-aqw/mugetsu) (**2.0.0**), plus [`source/patches/skua.patch`](source/patches/skua.patch) (`desktop/src/skua.rs`):

- `--skua-bridge host:port`: connects to BonxieMux to bridge `ExternalInterface` calls/events and forwarded `SkuaInput` events (mouse, wheel, keyboard, text, focus, visibility, and resize) for both **Wayland** (`Skua.WaylandHost`) and **X11 / XWayland** (`Skua.X11Host`). The player exits when BonxieMux closes the connection.
- `SKUA_EMBEDDED=1`: disables standalone update checks and metadata-driven window resizing while keeping Mugetsu's native right-click menu intact.
- Without those options it behaves like Mugetsu 2.0.0.

## Building

See [`source/README.md`](source/README.md) for local Linux build instructions.
