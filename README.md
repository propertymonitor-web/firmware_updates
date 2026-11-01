# firmware_updates

Firmware files for LODESTAR / ORION / OTR radios, and the list the dashboard's **Updates** screen reads.

- `latest.json` - the newest version of each product, with the files, flash address, size and SHA-256 of each.
- `cairn/mph/` - CAIRN (Bluetooth build, mph) for the Heltec V4, release cairn-beta3. Same file layout as OTR.
- `otr/mph/`, `otr/metric/` - OTR for the Heltec V4. `*-update.bin` keeps settings and is flashed at 0x10000 (the dashboard does this for you; it also blanks the 8 KB boot-selection record at 0xE000 so the radio starts the copy just written). `*-merged.bin` is the full image for a fresh flash at 0x0 with https://flasher.meshcore.io.

Adding a release: put the new files here, bump `version` and the `size` / `sha256` values in `latest.json` (tools: `sha256sum`), commit to `main`. Radios and dashboards compare the version their radio reports against `latest.json`.

Not yet tested on a real radio at the time of writing.
