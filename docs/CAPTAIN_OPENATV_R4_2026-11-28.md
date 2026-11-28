# Captain / openATV GTX Combo — independent r4 field report (28 November 2026)

## Attribution

Full credit for the native GTX Combo openATV port, kernel and driver integration, multiboot and Open Recovery Manager goes to Captain and the openATV team. Our contribution is independent testing, diagnostics and feedback. Thanks to Munir for comparative testing. This is not an official release note.

[Official downloads](https://images.mynonpublic.com/openatv/index.php?open=gtxcombo&v=8.0) · [Development discussion](https://www.linuxsat-support.com/thread/164261-first-full-open-source-box-coming/)

## Operator-reported results

- Linux 5.15.196, external USB HDD on blue port, root on USB partition confirmed by console. Factory Android fallback without drive and standby reported working. USB helper changes persistent boot settings; it is not a zero-write process.
- Remote, 4K, AC3 and playback of channels previously breaking up on Mars worked. Earlier eMMC build also had terrestrial and SAT+TERR Quad PiP reported working; do not treat those as independently repeated r4 tests.
- Eutelsat 3E: 23 services with a revised satellite list. Badr: 118 database services on 13 low-band transponders with V1; 587 with a dish-specific alternative table (changed polarity and transponder list). Android blind scan reference: 730 total services. Strong evidence of reversed polarization on the operator's reception path, not proof of physical LNB rotation or a universal image defect. The remaining difference is unresolved. No universal modified satellite table is recommended.
- Wi-Fi/BT initialization intermittent: SDIO CMD53 CRC error -84 during WCN firmware transfer, variable failure points. Reported 2 successes in 9 boots including one unlogged success; mixed warm/cold boots, not a controlled cold-boot series. No immediate retry in the traced write path; BT initialization can start a full re-download. Requested clock 50 MHz; actual 24 MHz in a debugfs snapshot, not measured during failed transfers. Root cause remains unproven.
- LAN random MAC on r4, missing RTL8153 firmware, duplicate kernelpolicy argument. Captain announced a test image with 12 MHz fallback and one failed-block retry, factory MAC fallback, Realtek firmware and command-line cleanup. These changes were not validated by this operator.

## Backup and USB guidance

Use the matching official recovery package and its instructions, on supported factory Android. Make a full eMMC backup before enabling USB boot or installing anything. A separate 64 GB USB stick is recommended: the tested device's raw eMMC user area alone was 31,264,342,016 bytes, with additional boot areas, recovery and metadata. A nominal 32 GB drive may be insufficient. Keep every backup part, both boot areas, manifest and factory snapshot files. Verify the backup with ORM where supported, then copy to safe storage and compare hashes before reusing the stick. Do not choose install or restore when merely creating a backup. Exact menus and supported ports may vary by recovery version; follow the bundled official guide. Mars compatibility is not established.

The operator's relocated backup passed 40/40 source/destination SHA256 checks and 32/32 original manifest checks; actual restore from the relocated copy was not tested. No private backup, binary modules, device identifiers or logs are published here.

## Status

Independent Captain track archived by operator decision. Official development continues with its maintainers. Mars and CoreELEC remain separate research tracks.
