<p align="center">
  <img src="https://raw.githubusercontent.com/Zainium-Dynamics/.github/main/profile/zainium-os.png" alt="Zainium OS" width="160">
</p>

Zainium OS
==========

Zainium Dynamics builds Zainium OS, an independent, enterprise-grade Linux
operating system, built from scratch and immutable by design. It is not
based on any other distribution, and it is a rolling release: install it
once and keep it current.

  - The base and the software you install live in separate layers under
    /overlayer and are joined at boot. Nothing you install is written into
    the base, and the base always boots on its own.
  - Even root cannot change a single byte of the base: on an installed
    system every base file is sealed with fs-verity. Kernel lockdown,
    AppArmor, Landlock, Yama and IPE are on from the first boot.
  - Base upgrades are staged while you work and applied at the next boot,
    journaled and reversible. The kernel rolls the same way.
  - musl is the core C library; glibc can be installed next to it for
    prebuilt software.
  - zex resolves every package and library before it installs anything.

The Dualayer Hierarchy Standard
-------------------------------

The filesystem layout of Zainium OS is published as an open specification,
the Dualayer Hierarchy Standard (DHS): one layer per owner under
/overlayer, and a directory of its own for each C library, so musl and
glibc run side by side. Any distribution can implement it.

    /overlayer/
    ├── syshub/      the base, changed only by atomic upgrades
    ├── userland/    software the user installs, on top with OverlayFS
    ├── ignition/    kernels, initramfs and boot loader
    └── agents/      instructions for AI agents

Zainium OS is the reference implementation; its layers are called syshub,
zexlib and zaisys.

Repositories
------------

    ZainiumOS                 the system's documentation and layout
    kernel-recipes            the kernel, its modules and headers
    quantra_ramfs             the initramfs: joins the layers, applies upgrades
    zainium_installer         the installer
    syshub-recipes            recipes for the base
    userland-recipes          recipes for installable software
    cosmic-zainium            the COSMIC desktop for Zainium
    sys_resolver              runs software that expects /usr, /etc and /bin
    elevate, elevate-pam      sudo and PAM, rewritten in Rust
    userutiles                core utilities in Rust
    dualayer-hierarchy-standard   the DHS specification

Links
-----

    Website    https://zainiumdynamics.tech
    Docs       https://zainiumdynamics.tech/docs
    DHS        https://zainiumdynamics.tech/dhs
    News       https://zainiumdynamics.tech/news
    X          https://x.com/zainiumdynamics

Zainium OS is free software under the GPL-3.0. Created by Ali Zain.
