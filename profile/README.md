<div align="center">

# Zainium Dynamics

**A deterministic, musl-native operating system, built from scratch.**

[![Website](https://img.shields.io/badge/Website-zainiumdynamics.tech-0052cc?style=flat-square&logo=globe&logoColor=white)](https://zainiumdynamics.tech)
[![Built with Rust](https://img.shields.io/badge/Built%20with-Rust-f74c00?style=flat-square&logo=rust&logoColor=white)](https://www.rust-lang.org)
[![musl libc](https://img.shields.io/badge/libc-musl-2e7d32?style=flat-square&logoColor=white)](https://musl.libc.org)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=flat-square&logo=gnu&logoColor=white)](https://www.gnu.org/licenses/gpl-3.0)

</div>

---

## What we're building

**[ZainiumOS](https://github.com/Zainium-Dynamics/ZainiumOS)** is a from-scratch Linux operating system targeting **musl libc**, not glibc. It is not derived from or repackaged from any existing distribution — the cross-compilation toolchain, the base system, and the package manager are all original work, built from upstream source.

The filesystem is split into layers that never share physical storage:

- **`syshub`** — the immutable base system, read-only at runtime
- **`zaisys`** — the immutable bootloader, kernel image, and ramfs
- **`zexlib`** — the writable userland, where all installed packages live

These merge at runtime through a real Linux OverlayFS union — never a symlink farm, never shared storage. `syshub`/`zaisys` can never be modified by anything that happens in userland, and every privileged action that touches the system is mediated by **Elevate**, our own replacement for `sudo`.

Packages are resolved by **Zex** through a strict, priority-ordered tier system — Zainium's own native archive first, then Void Linux musl ports, then Alpine, then Chimera as a last resort — plus a source-build engine for Rust crates via crates.io.

**Determinism is the first rule, and it is not negotiable.** Every build, every install, every upgrade produces the same result from the same inputs, every time. ZainiumOS does not favor any upstream and is not built to compete with any other distribution — it exists to be deterministic.

Read the full architecture in the [ZainiumOS README](https://github.com/Zainium-Dynamics/ZainiumOS#readme).

---

## The ecosystem

Most Linux distributions lean on decades-old C tooling. ZainiumOS rebuilds the userland it depends on in Rust, from scratch, rather than inheriting it as-is.

| Project | What it is |
|---|---|
| [**ZainiumOS**](https://github.com/Zainium-Dynamics/ZainiumOS) | The operating system itself |
| [**Quantra-System**](https://github.com/Zainium-Dynamics/Quantra-System) | PID 1 init system, initramfs, and network stack — memory-safe, static, Rust |
| [**Recoil**](https://github.com/Zainium-Dynamics/Recoil) | Immutable system safety net and chronology engine — rollback for the whole system |
| [**Evorix-browser**](https://github.com/Zainium-Dynamics/Evorix-browser) | A native, track-free, musl-based web browser |
| [**oxidized-environment**](https://github.com/Zainium-Dynamics/oxidized-environment) | Native TOML-based environment resolver — replaces `/etc/profile.d` |
| [**oxideutils**](https://github.com/Zainium-Dynamics/oxideutils) | A memory-safe, high-performance rewrite of GNU binutils |
| [**oxibus**](https://github.com/Zainium-Dynamics/oxibus) | A from-scratch Rust implementation of D-Bus |
| [**oxicurses**](https://github.com/Zainium-Dynamics/oxicurses) | A Rust rewrite path for classic ncurses |
| [**oxiread**](https://github.com/Zainium-Dynamics/oxiread) | A memory-safe library for interactive command-line editing |
| [**oxipd**](https://github.com/Zainium-Dynamics/oxipd) | A from-scratch Rust rewrite of dhcpcd |
| [**oxidized-yacc**](https://github.com/Zainium-Dynamics/oxidized-yacc) | A pure Rust LALR(1) parser generator |
| [**syshub-recipes**](https://github.com/Zainium-Dynamics/syshub-recipes) | Package recipes for `syshub`, the base OS |
| [**userland-recipes**](https://github.com/Zainium-Dynamics/userland-recipes) | Community package recipes for `zexlib`, the userland |

---

<div align="center">

Developer and System Architect: **Ali Zain**

</div>
