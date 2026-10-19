# A deterministic, musl-native operating system

![Zainium OS](https://raw.githubusercontent.com/Zainium-Dynamics/.github/main/profile/zainium-os.png)

Zainium Dynamics builds ZainiumOS, an independent Linux operating system made from scratch on musl libc and not derived from any other distribution. The base system and the software you install live in separate layers under `/overlayer` and are joined at boot with OverlayFS, so nothing you install can change the base. Around it we make the tools the system runs on, such as the initramfs quantra-ramfs, sys_resolver for programs that expect the usual Linux paths, and the package recipes in syshub-recipes, userland-recipes and cosmic-zainium.

We also write memory-safe Rust replacements for classic system software: elevate in place of sudo and doas, oxidized-environment, a TOML-based replacement for `/etc/profile.d`, oxiread for interactive line editing, and oxidized-yacc for parser generation.

Our first rule is determinism: the same inputs should give the same build, install and upgrade, every time. ZainiumOS is free software under the GPL-3.0 and in active development.

Created by Ali Zain — zainiumdynamics.tech
