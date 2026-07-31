# Changelog

## 0.1.1 (2026-07-30)

- Fix install/build failure: switch from Alpine to Debian bookworm base and install Fluent Bit from the official apt repository (glibc). Alpine 3.20 has no `fluent-bit` package in main/community ([#3](https://github.com/Shaffer-Softworks/home-assistant-openobserve-addon/issues/3)).
- Drop unsupported arches (`armhf`, `armv7`, `i386`); Fluent Bit Debian packages are amd64/aarch64 only.

## 0.1.0 (2026-05-20)

- Initial add-on split from home-assistant-openobserve monorepo
- Fluent Bit shipper for `home-assistant.log` → OpenObserve `/_multi`
