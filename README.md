# GTMedia GTX Combo — OpenATV / Enigma2 community research

**Community:** [Discussions](https://github.com/brntosaray/GTX-Combo-OpenATV-Research/discussions) · [Welcome topic (ready to publish)](docs/COMMUNITY_WELCOME.md) · [Issues](https://github.com/brntosaray/GTX-Combo-OpenATV-Research/issues)


**GTMedia GTX Combo (Amlogic S905X3) • Experimental external-drive OpenATV / Enigma2 DVB research**

> **Updated 22 November 2026:** **OpenBH/XC Enigma2 on one GTX Combo has operator-confirmed working satellite picture and sound; the operator also reports terrestrial reception working.** These are **OpenBH/XC findings**, not proof that an unmodified OpenATV image works in the same way. Terrestrial post-fix logs and complete build manifest have not yet been published. This is not an official GTMedia/OpenATV release or a downloadable working image.

## Official openATV GTX Combo port — November 2026

**Credit:** Captain and the openATV team developed the native GTX Combo port, including the Linux 5.15.196 integration, DVB/media support, multiboot and Open Recovery Manager (ORM). This independent repository contributed device testing, diagnostic observations and feedback; it is not the author or distributor of their official image. Thanks to Munir for comparative receiver testing.

- [Official openATV image downloads](https://images.mynonpublic.com/openatv/index.php?open=gtxcombo&v=8.0)
- [Original development discussion on LinuxSat](https://www.linuxsat-support.com/thread/164261-first-full-open-source-box-coming/)
- [Independent r4 test results and backup guidance](docs/CAPTAIN_OPENATV_R4_2026-11-28.md)

The operator tested r4 from external USB HDD and chose to archive this independent OpenATV investigation after reporting the official release. Earlier OpenBH/XC experiments below remain historical, separate from Captain's port.

## Purpose

Invite upstream maintainers and knowledgeable contributors to review and help build reliable Linux DVB support for **GTMedia GTX Combo**. The **GT Combo** and **GTX Combo** must not be assumed identical without board-level verification. This project is independent of the operator's CoreELEC experiments and private engineering repository.

## Latest GTX Combo OpenBH/XC progress (22 November 2026)

- **DVB-S/S2 picture and audio confirmed in the operator's OpenBH/XC test:** an XC transport-route mismatch was traced to the frontend-to-TS mapping; switching the hardware demux parameter from `xc_fe_ts=1,0,2,3` to `xc_fe_ts=0,1,2,3` produced satellite video (`VIDEO_START` in the recorded kernel trace) and the operator confirmed picture on-screen. Related local CIMaX, TS routing and Enigma2 frontend setup were documented.
- **DVB-T/T2 terrestrial:** the operator **now reports working reception in Enigma Black Hole**. The available dated troubleshooting document shows earlier successful Sony/ASCOT3 detection but still lacked signal at that *earlier checkpoint*. Exact final terrestrial fix, post-fix scan/playback logs and module hashes remain **awaiting publication**.
- **Boot qualification:** the documented OpenBH/XC external-media work involved a **persistent internal U-Boot environment change** (`saveenv`, USB-first then Mars fallback). The record confirms the environment write, **not** successful results for both requested follow-up boot tests. It is incorrect to claim the boot environment was untouched.

**Detailed report:** [OpenBH/XC satellite recovery and terrestrial status (22 Nov 2026)](docs/OPENBH_XC_DVB_SUCCESS_2026-11-22.md). The older **OpenATV** investigation below remains a separate research track.

## What we know

- Prior operator work referenced an OpenATV 8.0.1 AArch64 image and Linux `5.15.196`, booting an experiment from external USB/HDD. The exact current image/kernel/driver manifest has **not** been imported into this public repository.
- Candidate module names in experiments: `m88rs6060.ko`, `cxd2878.ko`, `aml_hardware_dmx.ko`, `gt-terrestrial.ko`. Presence of a module or driver attach does not establish full DVB functionality.
- A **16 November 2026** operator-supplied Enigma2 scan excerpt showed:

```text
20:56:06.9958 [eDVBScan] got sdt -1
20:56:06.9959 [eDVBScan] SDT for PAT TSID 001a unavailable
```

These lines establish that expected SDT/service discovery was unavailable in that scan; they **do not** establish the root cause. TS routing, kernel DVB demux/filter behavior, frontend lock and userspace scan state need separate evidence.

- A complete DVB-S/S2 + DVB-T/T2 result for the **historical OpenATV image** remains **separate and not independently reproduced in the public evidence**. The **new OpenBH/XC status** is documented above.

See [SDT symptom report](docs/SDT_DISCOVERY_SYMPTOM.md), [technical status and limits](docs/STATUS_AND_LIMITS.md), and [focused help requests](docs/HELP_WANTED.md).

## Safety and publication boundaries

Experiments use a separate external boot drive. The supplied OpenBH/XC record **does document a saved internal U-Boot environment change** for USB-first boot with Mars fallback; no change to Android Mars firmware partitions is claimed. **Do not represent this exact setup as zero-write to internal storage**, force-load mismatched kernel modules or change boot environment/firmware on another device from these notes.

No vendor firmware, binary modules, device-tree images, capture streams, private log archives, credentials, or CoreELEC-only fix kits are distributed. **No project-wide license is selected yet**; do not assume redistribution rights to third-party materials.

This is independent community research. [CoreELEC results are documented separately](https://github.com/brntosaray/GTX-Combo-CoreELEC-Research). Contributions with sanitized logs and upstream-compatible source patches are welcome.
