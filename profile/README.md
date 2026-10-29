# Zainium OS — independent, immutable, enterprise-grade Linux

<p align="center">
  <img src="https://raw.githubusercontent.com/Zainium-Dynamics/.github/main/profile/zainium-os.png" alt="Zainium OS">
</p>

<p align="center">
  <a href="https://zainiumdynamics.tech">Website</a> ·
  <a href="https://zainiumdynamics.tech/docs">Docs</a> ·
  <a href="https://zainiumdynamics.tech/principles">Principles</a> ·
  <a href="https://zainiumdynamics.tech/dhs">Dualayer Hierarchy Standard</a> ·
  <a href="https://zainiumdynamics.tech/news">News</a> ·
  <a href="https://x.com/zainiumdynamics">X</a>
</p>

Zainium Dynamics builds **Zainium OS**, an independent, enterprise-grade Linux operating system — built from scratch and immutable by design. Its core stays intact whatever you install, upgrades apply atomically, and software for musl and glibc runs side by side. It is not derived from any other distribution, and it is a rolling release.

- **A base that never breaks.** The base (`syshub`) and the software you install (`zexlib`) live in separate layers under `/overlayer` and are joined at boot with OverlayFS. Nothing you install is written into the base, and the base always boots on its own.
- **Even root cannot change a single byte of the base.** On an installed system every base file is sealed with fs-verity, so the kernel refuses to rewrite it. Kernel lockdown, AppArmor, Landlock, Yama and IPE are on from the first boot, every kernel module is signed, and `elevate` replaces sudo.
- **Atomic upgrades.** Base upgrades are staged while you work and applied by the initramfs at the next boot, journaled and reversible.
- **musl at the core, glibc when you need it.** Each C library has a directory of its own, so prebuilt glibc software runs next to the musl base.
- **No dependency hell.** The zex package manager resolves every package and shared library before it installs anything.
- **An open standard.** The filesystem layout is published as the [Dualayer Hierarchy Standard](https://github.com/Zainium-Dynamics/dualayer-hierarchy-standard), for any distribution to implement.

The repositories here are the system itself — [ZainiumOS](https://github.com/Zainium-Dynamics/ZainiumOS), the initramfs [quantra_ramfs](https://github.com/Zainium-Dynamics/quantra_ramfs), the [installer](https://github.com/Zainium-Dynamics/zainium_installer), [sys_resolver](https://github.com/Zainium-Dynamics/sys_resolver), the kernel in [linux_patches](https://github.com/Zainium-Dynamics/linux_patches) and the recipes in [syshub-recipes](https://github.com/Zainium-Dynamics/syshub-recipes), [userland-recipes](https://github.com/Zainium-Dynamics/userland-recipes) and [cosmic-zainium](https://github.com/Zainium-Dynamics/cosmic-zainium) — and memory-safe Rust replacements for classic system software: [elevate](https://github.com/Zainium-Dynamics/elevate) in place of sudo and doas, [userutiles](https://github.com/Zainium-Dynamics/userutiles), [oxidized-environment](https://github.com/Zainium-Dynamics/oxidized-environment), [oxiread](https://github.com/Zainium-Dynamics/oxiread) and [oxidized-yacc](https://github.com/Zainium-Dynamics/oxidized-yacc).

Zainium OS is free software under the GPL-3.0 and in active development.

Created by Ali Zain — [zainiumdynamics.tech](https://zainiumdynamics.tech)
