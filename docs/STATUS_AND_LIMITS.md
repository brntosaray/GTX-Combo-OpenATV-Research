# OpenATV status and boundaries (17 November 2026)

## Evidence and reported context

- Platform: operator-owned GTMedia GTX Combo / Amlogic S905X3.
- Historical OpenATV experiment: external USB/HDD boot, candidate SAT and terrestrial drivers; previous context mentioned AArch64 and Linux 5.15.196. An exact current build/module manifest has **not** been collected for this public publication.
- A 16 November 2026 operator log contains `got sdt -1` and `SDT for PAT TSID 001a unavailable`.
- Complete channel/service discovery and playback remain **unverified in this published evidence**. A module filename or demodulator registration is not enough to declare success.

## Preservation requirements

- Preserve original Android Mars and internal eMMC/boot/reserved/DTB/DTBO partitions.
- Keep reproduction on separate external media and obtain consent before any invasive hardware or software experiment.
- Do not confuse CoreELEC results with tested OpenATV behavior.
- Never force-load mismatched `.ko` modules or treat unverified scripts as production drivers.
- Do not redistribute vendor firmware, proprietary driver binaries or private receiver logs.

This repository is a technical collaboration record, **not** a ready-to-flash firmware image.
