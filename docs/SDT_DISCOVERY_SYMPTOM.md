# Recorded SDT / service-discovery issue

**Track:** OpenATV / Enigma2 only. **Observed:** 16 November 2026, from an operator-supplied debug excerpt. No full raw debug log or independent test capture is attached.

## Representative excerpt

```text
20:56:06.9958 [eDVBScan] got sdt -1
20:56:06.9959 [eDVBScan] SDT for PAT TSID 001a unavailable
```

## Established by this evidence

The Enigma2 scanning path did not make the expected SDT available for the PAT TSID `001a` during this observed scan. Complete service discovery was not operating correctly at that checkpoint.

## Not established

These two lines cannot distinguish frontend lock failures, transport-stream routing problems, hardware demux issues, section-filter IOCTL behavior, userspace handling, CRC failures, scan timing, or signal quality. In particular, working CoreELEC satellite reception on the same operator device does **not** demonstrate that OpenATV's DVB demux path works.

## Helpful additional evidence

A new **sanitized** log collection could include:

- Dated frontend initialization, adapter numbers, demux registration and kernel/module versions.
- FE status/lock and frequency, symbol rate and delivery-system parameters (avoid identifying user subscriptions).
- PAT and SDT section-reader or DVB filter errors and relevant demux IOCTL results.
- Whether MPEG-TS packets arrive in a controlled capture (metadata only, no copyrighted stream upload).
- Exact external-boot kernel and driver ABI, and what test was run without changing the internal Mars system.

Any future diagnosis or fix needs separate reproducible results; this document makes no unsupported root-cause claim.
