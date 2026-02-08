# Experimental ImmortalWrt Builds for mt798x

This repository provides **experimental builds** based on [**padavanonly/immortalwrt-mt798x-6.6**](https://github.com/padavanonly/immortalwrt-mt798x-6.6).

Current targets:

- **Zyxel EX5601-T0 (ubootmod)**
- **GL.iNet GL-MT3000 / Beryl AX**

## Key Differences from padavanonly/immortalwrt-mt798x-6.6

- Retains all essential **MediaTek Wi-Fi features** from the upstream build, but excluded many VPN-related packages.
- Default language set to **English**, with Wi-Fi region defaulting to **Sweden (SE)**.
- Enabled **DFS** on the 5G band with vendor-specific **DFS Zero-Wait** support for countries with a valid regulatory domain mapping.

## Installation

Compiled builds are published via **GitHub Actions**:

- Download and unzip the release artifacts (ignore the `packages` folder).
- Flash the `*squashfs-sysupgrade.itb` file to a supported device already running **OpenWrt/ImmortalWrt ubootmod**.

## DFS with zero/wait usage notes

When channel width is set to 80 Hz on the 5G band (default), the driver will end up with a 160 Hz 👍