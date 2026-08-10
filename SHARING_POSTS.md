# Ready-to-post announcements

## Reddit / r/OpenCoreLegacyPatcher

**Title:** Mid-2011 iMac (iMac12,1) High Sierra → Monterey: internal installer workaround + Magic Mouse duplicate-entry fix

I documented a full real-world upgrade of a 21.5-inch Mid-2011 iMac (iMac12,1) from High Sierra to Monterey with OCLP.

The machine has a 2.5 GHz Core i5, 24 GB RAM, and a 1 TB SSD. The final result is surprisingly good—Monterey is running smoothly enough that the upgrade was well worth the effort.

A few things made this installation unusual:

- OCLP would not list a 32 GB SD card in the built-in SD reader.
- I created the Monterey installer on a temporary internal HFS+ partition instead.
- Wi-Fi/Bluetooth needed post-install patching and troubleshooting.
- The Magic Mouse kept showing connection failures even though macOS could see it.
- The final mouse fix was deleting **two entries for the same Magic Mouse**—one under the friendly name and another under its hardware address—then rediscovering it.
- Wi-Fi works reliably but currently requires a manual connect after startup.
- The temporary installer partition was removed afterward and the APFS container expanded back to the full 1 TB.

I turned the full process into a redacted, chapter-by-chapter field guide with checkpoints so readers can tell when to stop rather than rushing ahead.

**Important:** it is an independent case study, not official OCLP documentation, and disk identifiers in the guide are machine-specific.

[ADD GUIDE LINK]

If anyone has the same iMac12,1 hardware and runs into similar SD-reader, Bluetooth, or legacy Wi-Fi behavior, I hope this saves you some time.

---

## MacRumors / forum version

**Subject:** Field guide: Mid-2011 iMac12,1 High Sierra to Monterey with OCLP

I recently completed an OCLP Monterey upgrade on a 21.5-inch Mid-2011 iMac (iMac12,1, 2.5 GHz i5, 24 GB RAM, 1 TB SSD) and documented the entire process as a step-by-step field guide.

The main complications were:

1. Built-in SD reader showed the card as internal, so OCLP would not use it as installer media.
2. Monterey installer was created on a temporary internal HFS+ partition using `createinstallmedia`.
3. OCLP root patching was required before the older wireless stack behaved properly.
4. Magic Mouse pairing failed repeatedly until duplicate Bluetooth records were removed.
5. Wi-Fi now works reliably, although this machine still requires a manual join after startup.
6. The installer partition was safely deleted and the APFS container restored to the full SSD size.

The guide includes redacted screenshots, terminal commands, checkpoints, and warnings around destructive disk operations.

[ADD GUIDE LINK]

This is an independent case study, not official Dortania/OCLP documentation. Anyone following it should verify current OCLP documentation and their own disk identifiers before using any erase/resize commands.

---

## Short Facebook / WhatsApp tech-group post

I successfully upgraded a Mid-2011 21.5-inch iMac from High Sierra to Monterey using OpenCore Legacy Patcher. The machine has 24 GB RAM and a 1 TB SSD, and the improvement was well worth the effort.

I documented the whole process—including an internal installer-partition workaround, Wi-Fi recovery, a Magic Mouse duplicate-entry fix, and final disk cleanup—in a redacted step-by-step guide.

[ADD GUIDE LINK]

Important: this is a real-world case study, not official OCLP documentation. Always verify your own Mac model and disk layout first.
