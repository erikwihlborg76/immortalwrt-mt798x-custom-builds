# Experimental ImmortalWrt Builds for mt798x

This repository provides **experimental builds** based on [**padavanonly/immortalwrt-mt798x-6.6**](https://github.com/padavanonly/immortalwrt-mt798x-6.6).

Current targets:

- **Zyxel EX5601-T0 (ubootmod)**
- **GL.iNet GL-MT3000 / Beryl AX**

## Key Differences from padavanonly/immortalwrt-mt798x-6.6

- Retains all essential **MediaTek Wi-Fi features** from the upstream build.
- Default language set to **English**, with Wi-Fi region defaulting to **Sweden (SE)**.
- Added the full **SQM stack** (usable only when vendor WAN/LAN acceleration is disabled --- enabled by default).
- Enabled **DFS** and vendor-specific **DFS Zero-Wait** support for countries with a valid regulatory domain mapping.

## Installation

Compiled builds are published via **GitHub Actions**:

- Download and unzip the release artifacts (ignore the `packages` folder).
- Flash `immortalwrt-mediatek-filogic-zyxel_ex5601-t0-ubootmod-squashfs-sysupgrade.itb` onto a **Zyxel EX5601-T0** already running **OpenWrt/ImmortalWrt ubootmod**.

## DFS Usage

To enable DFS:

1. Ensure the selected Wi-Fi country has a valid regulatory domain mapping (see `patches/0001-Added-regdomain-field-and-corrected-serveral-allowed.patch`).
2. Set the 5 GHz Wi-Fi channel to **"auto"**.
3. x
