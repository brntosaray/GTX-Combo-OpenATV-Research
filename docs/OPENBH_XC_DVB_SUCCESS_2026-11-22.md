# GTMedia GTX Combo — OpenBH/XC Enigma2 DVB progress (22 November 2026)

> **Scope:** GTMedia **GTX Combo** (Amlogic S905X3), **OpenBH/XC-derived Enigma2** experiment. This is **not** evidence that an unmodified OpenATV image has the same fixes. Source is an operator-supplied 34-page troubleshooting record titled *Black Hole Fix.docx* and the operator's **22 November 2026** confirmation that both satellite and terrestrial reception now work.

## Status / evidence levels

| Feature | Status | Supporting evidence or limitation |
| --- | --- | --- |
| DVB-S/S2 satellite picture **and** sound on OpenBH/XC | **Confirmed by operator during troubleshooting; log excerpt retained in supplied record** | Enigma2 picture appeared after correcting the XC frontend-to-TS mapping. Kernel log includes `VIDEO_START-tsync_mode:1(S)`. |
| DVB-T/T2 terrestrial on OpenBH/XC | **Operator reports success on 22 Nov 2026** | The earlier troubleshooting document, taken at a previous checkpoint, still showed **no terrestrial signal** with the then-loaded XC `cxd2878.ko`. No post-fix tuner/scan/playback log or complete current module manifest was provided for this public update. Do not treat the earlier failure as the final state. |
| OpenATV-specific external-HDD experiment | **Separate track; historical** | Earlier notes documented a terrestrial configuration and an SDT/service-discovery failure. Success on OpenBH/XC does not automatically prove success on the OpenATV image. |
| Automatic USB boot with Mars fallback | **U-Boot environment change observed; end-to-end reboot/fallback test not documented in the supplied record** | The record ends after `saveenv` succeeded. Do not claim that both follow-up boot tests passed. |
| Cold-boot consistency / other units / installation package | **Not independently verified** | No general-release image or validated installer published here. |

## Satellite root-cause finding: XC TS frontend mapping

In the captured OpenBH/XC test, the frontend-to-TS mapping parameter was originally:

```text
xc_fe_ts=1,0,2,3
```

The investigation identified a **GT Combo-style frontend ordering** not matching the tested **GTX Combo** frontend order. While satellite audio could be heard, the decoder received zero video data before the routing correction. A live change to:

```text
xc_fe_ts=0,1,2,3
```

was followed by the operator reporting satellite picture, and the log showing:

```text
tsdemux_init ... To use device 1,pcr_num=0
xc-dvb: play demux0 vpid 0xbff pcr 0xbff vformat 2
[tsync_avevent_locked 830]VIDEO_START-tsync_mode:1(S)
```

The changed parameter was subsequently included in the `aml_hardware_dmx.ko` insertion line of the experimental `/etc/init.d/xc-gui-startup`; the report showed a successful shell syntax check. This **does not replace** reboot/cold-boot verification.

Other steps documented in the same satellite repair investigation were **local CIMaX initialization**, `gtx-tsfix v2` routing adjustments, and Enigma2 frontend/DiSEqC configuration (including an eight-input switch with the relevant satellite on input 1). These are context-specific findings, **not universal installation instructions**.

## Terrestrial tuner evidence and the difference between discovery and reception

Earlier OpenBH/XC kernel logs from the operator's record included:

```text
[dvb]: Demod: client cxd2878 0x6c ... Meson I2C adapter
i2c i2c-2: Detect CXD2878/CXD6802(SiP) chip.
DVB: registering adapter 0 frontend 0 (sony cxd2878 familly)...
i2c i2c-2: Deceted the Tuner chip ASCOT3 ,ID 2878A
```

The same earlier checkpoint reported **no terrestrial signal**; the observed XC `cxd2878.ko` differed from a customized `GTX_v2_Tonly` driver previously used in a separate OpenATV setup. These facts demonstrate frontend discovery only, **not** that the earlier XC driver configuration could receive channels.

**Current update:** The project operator subsequently confirmed that terrestrial reception is working on Enigma Black Hole. The exact terrestrial fix, full post-fix logs, channel scan/playback evidence and new hashes are **not included in the available technical report**. They should be added when explicitly collected, rather than guessed from the satellite repair or from an older OpenATV module.

## Boot and Mars preservation: important qualification

Work was performed on **external USB/HDD Enigma2 media**, and Android Mars firmware itself was not presented as reflashed by this report. However, the record explicitly documents a **persistent U-Boot environment modification on internal storage**, after an 8 MiB environment backup:

- `bootcmd` was changed to try `run usbboot` before `run storeboot`.
- `usbboot` tries external `cfgload` before falling back.
- `saveenv` output was **`Writing to MMC(1)... done`**, with `mmc env offset: 0x27400000`.
- The document requests two subsequent verification boots (with and without HDD); **their results are not present**.

Therefore **do not describe this exact boot setup as leaving the bootloader environment untouched**. No partition image, bootloader code, full backup, private IP, host fingerprint or rollback binary is published. Do not copy these boot environment settings to another unit without an independently tested safety/recovery plan.

## Follow-up documentation wanted

- Post-fix **terrestrial** frontend status (delivery system, frequency/lock), successful scan and picture/sound or TS evidence, without copyrighted recordings.
- Exact **OpenBH/XC** image build, kernel ABI, final loaded module hashes and final frontend-to-TS assignments.
- Cold-boot and reboot results with the external drive; controlled fallback-to-Mars result when no external drive is present.
- Clarify which results, if any, also reproduce on the separate **OpenATV** external boot experiment.

For dated historical OpenATV failures, see [SDT discovery symptom](SDT_DISCOVERY_SYMPTOM.md). This document **does not merge** the two image histories or the separate [CoreELEC research](https://github.com/brntosaray/GTX-Combo-CoreELEC-Research).

**No proprietary firmware, binary drivers, private diagnostic dumps or flashing tools are distributed.**
