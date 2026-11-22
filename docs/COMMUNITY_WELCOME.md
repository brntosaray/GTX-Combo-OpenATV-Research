<!-- Discussion topic title: Welcome — GTMedia GTX Combo OpenATV/Enigma2 development and DVB collaboration -->

# Welcome to GTX Combo OpenATV / Enigma2 research

Hello, I'm **EMO**. This repository documents experimental **OpenATV/Enigma2** work for the **GTMedia GTX Combo (Amlogic S905X3)**. The intended approach uses an **external USB/HDD boot medium**, preserving the internal Android Mars installation.

## Update — 22 November 2026 (OpenBH/XC track)

**OpenBH/XC Enigma2 on the GTX Combo:** the operator confirmed DVB-S/S2 satellite **picture and sound** after an XC frontend/TS mapping correction and now reports **terrestrial reception working**. Satellite video is supported by a captured `VIDEO_START` log; the full post-fix terrestrial test logs are still not available in the public record. This result is **specific to OpenBH/XC**, not proof that the earlier OpenATV image is identically fixed.

See [OpenBH/XC progress report](OPENBH_XC_DVB_SUCCESS_2026-11-22.md). Note: this source file is a repository reference; a previously published GitHub Discussion must be updated separately in the GitHub UI.

## Progress and limitations
- Experimental external-media boot and investigation of Amlogic **DVB-S/S2, DVB-T/T2**, TS routing and demux integration.
- Historical notes reference an AArch64 image and Linux kernel `5.15.196`; the exact current image/driver manifest is not yet fully published.
- A recorded Enigma2 scanning symptom was:

```text
[eDVBScan] got sdt -1
[eDVBScan] SDT for PAT TSID 001a unavailable
```

This shows **unavailable SDT/service discovery in that scan**, **not** a proven root cause. Full working channel scanning and live DVB reception for OpenATV **are not claimed**.

## We welcome contributors

Developers familiar with **Linux DVB frontend drivers, Amlogic demux/TS, DVB section filtering, Enigma2 scans and source-level integration** can help identify the next high-value evidence or propose maintainable patches.

Please share exact GTX hardware, image/kernel ABI, adapter registration, frontend-lock information, timestamped sanitized logs and reproduction details. GTX Combo and GT Combo should not be treated as identical.

See [research overview](../README.md), [SDT symptom](SDT_DISCOVERY_SYMPTOM.md), [project boundaries](STATUS_AND_LIMITS.md), and [help wanted](HELP_WANTED.md).

Existing coordination thread: **[Issue #1](https://github.com/brntosaray/GTX-Combo-OpenATV-Research/issues/1)**. Use Discussions for broader engineering questions and brainstorming.

Please preserve Android Mars and avoid flashing internal partitions or force-loading incompatible modules. **No proprietary firmware or binaries are offered here.**

— **EMO**
