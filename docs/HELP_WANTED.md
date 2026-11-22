# Focused developer questions

1. What frontend-to-adapter-to-demux registration and TS input path is correct for `M88RS6060` on a GTMedia GTX Combo running the actual OpenATV kernel?
2. At which stage did the recorded SDT failure occur: tuner/TS input, hardware demux routing, Linux DVB section filters, or Enigma2 scan state?
3. Which minimal sanitized `dmesg`, frontend-lock, DVB filter IOCTL and PAT/SDT traces distinguish those candidate failures?
4. What upstream-compatible work is needed for Sony terrestrial demodulator support without assuming a CoreELEC-specific driver architecture?
5. Can reliable source patches be provided and maintained without distributing vendor binary modules or proprietary firmware?

Please include hardware revision, kernel ABI and build provenance, exact test conditions, evidence date, reproducible logs and explicit limitations. A candidate fix should only be marked successful after receiver-side verification.

## OpenBH/XC progress and remaining evidence (22 November 2026)

**Do not retest known-working satellite routing merely to reproduce a historical failure.** OpenBH/XC satellite picture and sound were operator-confirmed after correction of `xc_fe_ts`. The operator also reports working terrestrial reception, but the full post-fix terrestrial test record and precise final driver set remain to be published. See [OpenBH/XC progress](OPENBH_XC_DVB_SUCCESS_2026-11-22.md).

Especially useful now: final **terrestrial** driver provenance, tuner scan/playback or TS evidence, reproducible reboot/cold boot and boot-to-Mars fallback results, and a clear distinction between OpenBH/XC versus OpenATV images. Keep proprietary modules and private backups out of public issues.
