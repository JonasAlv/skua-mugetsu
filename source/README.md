# Mugetsu source (Skua Linux build)

This folder holds the upstream [Mugetsu](https://github.com/mugetsu-aqw/mugetsu) **2.0.0** patches on top of [Ruffle](https://github.com/ruffle-rs/ruffle), plus [`patches/skua.patch`](patches/skua.patch) for [BonxieMux](https://github.com/JonasAlv/BonxieMux).

Every release is built from this folder by GitHub Actions ([`.github/workflows/build.yml`](../.github/workflows/build.yml)).

## What's here

| File | What it is |
|---|---|
| `RUFFLE_COMMIT` | The pinned Ruffle commit (`f22d29d9cb8483af85fe1f97056ac2d78c32cefe`) |
| `RUST_VERSION` | The Rust toolchain version (`1.99.0`) |
| `patches/ruffle.patch` | Upstream Mugetsu 2.0.0 changes to Ruffle |
| `patches/skua.patch` | Skua-specific changes applied after `ruffle.patch` (`desktop/src/skua.rs`, `--skua-bridge`, `SkuaInput`) |
| `patches/wgpu-core.patch`, `wgpu-hal.patch`, `gc-arena.patch`, `lyon_path.patch`, `lyon_algorithms.patch` | Upstream patches to the five crates from crates.io |
| `pgo/aqw.profdata.zip` | Upstream PGO profile for AQW |
| `build-linux.sh` | Fetches Ruffle and the five crates, applies all patches, and builds `build/out/Mugetsu` |
| `release-linux/`, `release/LICENSES/` | Readme, notices, and license texts packaged into the Linux archives |
| `notes/` | Release notes used for GitHub draft releases |

## Building it yourself (Linux)

You need [Rust](https://rustup.rs) (`rustup toolchain install 1.99.0`), Java 17 or newer, `git`, and system development libraries (on Debian/Ubuntu: `sudo apt install build-essential pkg-config libasound2-dev libudev-dev libfontconfig-dev libfreetype6-dev libssl-dev`).

```bash
bash build-linux.sh
```

The output binary is `build/out/Mugetsu` (pass `--no-pgo` to skip PGO or `--prepare-only` to only apply patches).
