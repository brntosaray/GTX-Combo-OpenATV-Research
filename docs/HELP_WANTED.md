# Focused developer questions

1. What frontend-to-adapter-to-demux registration and TS input path is correct for `M88RS6060` on a GTMedia GTX Combo running the actual OpenATV kernel?
2. At which stage did the recorded SDT failure occur: tuner/TS input, hardware demux routing, Linux DVB section filters, or Enigma2 scan state?
3. Which minimal sanitized `dmesg`, frontend-lock, DVB filter IOCTL and PAT/SDT traces distinguish those candidate failures?
4. What upstream-compatible work is needed for Sony terrestrial demodulator support without assuming a CoreELEC-specific driver architecture?
5. Can reliable source patches be provided and maintained without distributing vendor binary modules or proprietary firmware?

Please include hardware revision, kernel ABI and build provenance, exact test conditions, evidence date, reproducible logs and explicit limitations. A candidate fix should only be marked successful after receiver-side verification.
