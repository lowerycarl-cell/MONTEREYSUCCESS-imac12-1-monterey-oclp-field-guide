# Mid-2011 iMac (iMac12,1) → macOS Monterey with OpenCore Legacy Patcher

An independent, real-world field guide documenting a successful upgrade of a **21.5-inch Mid-2011 iMac (iMac12,1)** from **macOS High Sierra** to **macOS Monterey** using **OpenCore Legacy Patcher (OCLP)**.

This is **not official OCLP documentation**. It is a practical case study built from a live troubleshooting session, including the workarounds, mistakes, recovery steps, checkpoints, and final successful configuration.

## What makes this guide useful

This case included several problems that are easy to encounter on older hardware:

- OCLP would not recognize a 32 GB SD card in the iMac's built-in SD reader as installer media.
- The Monterey installer was instead created on a temporary internal HFS+ partition.
- OpenCore was installed to the internal EFI partition.
- Monterey installed successfully as an in-place upgrade.
- Wi-Fi and Bluetooth required OCLP post-install patching and additional troubleshooting.
- The Magic Mouse repeatedly showed connection failures until **duplicate Bluetooth device records** were removed.
- Wi-Fi ultimately worked reliably, though the saved network required a manual connect after startup.
- The temporary installer partition was safely removed and the APFS container expanded back to the full 1 TB SSD.

## Tested machine

- **Model:** 21.5-inch iMac, Mid 2011
- **Model Identifier:** iMac12,1
- **CPU:** 2.5 GHz Intel Core i5
- **RAM:** 24 GB DDR3
- **Storage:** 1 TB SSD
- **Starting OS:** macOS High Sierra
- **Target OS:** macOS Monterey
- **OCLP:** 2.4.1
- **OpenCore:** REL-104 / 1.0.4

## Download the guide

- **PDF:** `Mid-2011_iMac_Monterey_OCLP_Field_Guide_Redacted_v2.pdf`
- **Editable DOCX:** `Mid-2011_iMac_Monterey_OCLP_Field_Guide_Redacted_v2.docx`

The PDF is the recommended version for sharing. The DOCX is included as an editable master.

## Read this before following the commands

**Disk identifiers in the guide belong to one specific iMac. Do not copy destructive `diskutil` commands blindly.**

Before any erase, resize, or EFI operation:

1. Run `diskutil list`.
2. Verify the exact target disk and partition.
3. Make a backup of anything important.
4. Stop if your disk layout differs from the guide.

A wrong disk identifier in an erase or resize command can destroy data.

## Key lessons

### 1. Built-in SD readers may not behave like removable USB media
The 32 GB SD card was visible to macOS but appeared as an internal physical disk. OCLP therefore did not list it as installer media.

### 2. A secondary internal installer partition can work
The APFS container was safely shrunk after verification, a temporary HFS+ partition was created, and Apple's `createinstallmedia` tool was used to build the Monterey installer there.

### 3. Post-install root patching is essential
The iMac booted Monterey before all legacy hardware behaved properly. OCLP root patches were required for older graphics/wireless support.

### 4. "Detected" does not mean "paired"
The Magic Mouse was visible with a strong signal but repeatedly failed to connect. The final fix was to remove **both Bluetooth records** for the same mouse—one under its friendly name and one under its hardware address—then power-cycle and rediscover it.

### 5. Wi-Fi may work without auto-joining
The legacy Atheros Wi-Fi card detects and joins the network successfully, but on this installation the saved network does not auto-connect after startup. Manual selection connects quickly and reliably.

### 6. Keep a wired mouse nearby
A basic wired USB mouse dramatically simplified recovery and final configuration.

## Suggested publication title

**Field guide: Mid-2011 iMac (iMac12,1) High Sierra → Monterey with OCLP — internal installer workaround, Wi-Fi recovery, Magic Mouse duplicate-entry fix, and disk cleanup**

## Attribution / licensing

This package does not assign a public license yet. Before publishing widely, choose the license you prefer for the written guide (for example, **Creative Commons Attribution 4.0 (CC BY 4.0)** if you want others to freely share and adapt it with attribution).

## Official project

OpenCore Legacy Patcher is maintained by the Dortania/OCLP community. Readers should always compare this field guide with the current official OCLP documentation before beginning an upgrade because OCLP behavior and supported macOS versions change over time.
