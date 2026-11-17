# GTMedia GTX Combo — OpenATV / Enigma2 community research

**GTMedia GTX Combo (Amlogic S905X3) • Experimental external-drive OpenATV / Enigma2 DVB research**

> **Status: 17 November 2026. Experimental boot and DVB integration only. Successful complete DVB-S/S2 service discovery or DVB-T/T2 reception is NOT claimed.** This repository is not an official OpenATV/GTMedia release.

## Purpose

Invite upstream maintainers and knowledgeable contributors to review and help build reliable Linux DVB support for **GTMedia GTX Combo**. The **GT Combo** and **GTX Combo** must not be assumed identical without board-level verification. This project is independent of the operator's CoreELEC experiments and private engineering repository.

## What we know

- Prior operator work referenced an OpenATV 8.0.1 AArch64 image and Linux `5.15.196`, booting an experiment from external USB/HDD. The exact current image/kernel/driver manifest has **not** been imported into this public repository.
- Candidate module names in experiments: `m88rs6060.ko`, `cxd2878.ko`, `aml_hardware_dmx.ko`, `gt-terrestrial.ko`. Presence of a module or driver attach does not establish full DVB functionality.
- A **16 November 2026** operator-supplied Enigma2 scan excerpt showed:

```text
20:56:06.9958 [eDVBScan] got sdt -1
20:56:06.9959 [eDVBScan] SDT for PAT TSID 001a unavailable
```

These lines establish that expected SDT/service discovery was unavailable in that scan; they **do not** establish the root cause. TS routing, kernel DVB demux/filter behavior, frontend lock and userspace scan state need separate evidence.

- A fully working DVB-S/S2 plus DVB-T/T2 implementation for this experimental OpenATV setup is **not verified by the public evidence here**.

See [SDT symptom report](docs/SDT_DISCOVERY_SYMPTOM.md), [technical status and limits](docs/STATUS_AND_LIMITS.md), and [focused help requests](docs/HELP_WANTED.md).

## Safety and publication boundaries

Experiments are intended for a separate external boot drive; the internal Android Mars installation and boot partitions remain unchanged. Do not force-load incompatible kernel modules or flash speculative bootloader data.

No vendor firmware, binary modules, device-tree images, capture streams, private log archives, credentials, or CoreELEC-only fix kits are distributed. **No project-wide license is selected yet**; do not assume redistribution rights to third-party materials.

This is independent community research. [CoreELEC results are documented separately](https://github.com/brntosaray/GTX-Combo-CoreELEC-Research). Contributions with sanitized logs and upstream-compatible source patches are welcome.
