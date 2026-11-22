# Enigma2 image-specific status and boundaries (22 November 2026)

## Evidence and reported context

- Platform: operator-owned GTMedia GTX Combo / Amlogic S905X3.
- Historical OpenATV experiment: external USB/HDD boot, candidate SAT and terrestrial drivers; previous context mentioned AArch64 and Linux 5.15.196. An exact current build/module manifest has **not** been collected for this public publication.
- A 16 November 2026 operator log contains `got sdt -1` and `SDT for PAT TSID 001a unavailable`.
- Complete channel/service discovery and playback remain **unverified in this published evidence**. A module filename or demodulator registration is not enough to declare success.

## New: OpenBH/XC Enigma2 results (separate from historical OpenATV)

- On the operator's GTX Combo, OpenBH/XC DVB-S/S2 playback became functional with **picture and sound** after a mapping correction from `xc_fe_ts=1,0,2,3` to `xc_fe_ts=0,1,2,3`. The captured decoder log contains `VIDEO_START` following the change.
- **22 November operator update:** DVB-T/T2 reception on Enigma Black Hole **also reported working**. The source record's earlier no-signal observation predates that confirmation; the final terrestrial fix and post-fix scan/TS logs are not in the publicly accessible record.
- An **internal U-Boot environment modification** (`saveenv` for USB-first, Mars-fallback boot) was actually recorded; follow-up boot/fallback test results were **not** supplied. Do not claim that the boot environment remained untouched.
- See the [dated OpenBH/XC evidence and limitations](OPENBH_XC_DVB_SUCCESS_2026-11-22.md).
- None of the above is a claim that the **original OpenATV external-HDD image** has received the identical repairs or that either image is ready for public installation.

## Preservation requirements

- Preserve original Android Mars firmware/partitions. The source record already includes a **saved U-Boot environment change**, so document and independently verify any boot fallback rather than claiming the environment is original.
- Keep reproduction on separate external media and obtain consent before any invasive hardware or software experiment.
- Do not confuse CoreELEC results with tested OpenATV behavior.
- Never force-load mismatched `.ko` modules or treat unverified scripts as production drivers.
- Do not redistribute vendor firmware, proprietary driver binaries or private receiver logs.

This repository is a technical collaboration record, **not** a ready-to-flash firmware image.
