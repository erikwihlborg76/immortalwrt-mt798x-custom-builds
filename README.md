# Experimental ImmortalWrt Builds for Zyxel EX5601

## About the Build

This build targets **zyxel_ex5601-t0-ubootmod**, based on **padavanonly/immortalwrt-mt798x-6.6**.  

Key changes include:

- **Zero-Wait DFS** support added
- **SQM** support added  
- **WARP** acceleration kept (debug features removed)  
- **Toolchain optimizations** applied  

All essential **MediaTek Wi-Fi features** from the padavanonly build are retained.

## Using It

To enable DFS:  

- Set the Wi-Fi channel to **"auto"** on the 5 GHz band.  
- DFS is only enabled when the selected Wi-Fi country has a valid regulatory domain mapping.

## Changes Compared to padavanonly immortalwrt-mt798x-6.6

- Switched language to **English**, with default Wi-Fi country set to **Sweden (SE)**  
- Reduced from **multi-profile builds** to a **single target: zyxel_ex5601-t0-ubootmod**  
- Added **SQM stack**: `sqm-scripts`, `luci-app-sqm`, `kmod-sched-cake`, `kmod-sched-core`  
- Removed debug options: `WARP_DBG_SUPPORT`, `WARP_MEMORY_LEAK_DBG` (additional debugging features can be toggled at the end of the `.config`)  
- Enabled **DFS** and vendor-specific feature **DFS Zero-Wait**  
- Applied **target-specific optimizations**  
- Removed **BusyBox customizations**

## How It’s Built

The build is automated using **GitHub Actions**:  

- Sources are fetched from [padavanonly/immortalwrt-mt798x-24.10](https://github.com/padavanonly/immortalwrt-mt798x-24.10)  
- Patches from this repository and the device-specific `.config` in the `/configs` folder are applied before compilation.  
- Compiled builds are available under the **GitHub Actions** section. Direct archive unzipping may fail for unknown reasons, but extracting the file `immortalwrt-mediatek-filogic-zyxel_ex5601-t0-ubootmod-squashfs-sysupgrade.itb` works reliably and can be flashed onto a **zyxel_ex5601-t0-ubootmod** device already running ImmortalWrt.  

---

## Usage notes

- **Configs**  
  - If both `immortalwrt.config` and `openwrt.config` exist, the workflows will prefer them over the generic `.config`.  
  - Use `.config` if the same settings apply to both builds.

- **Patches**  
  - Place global patches (kernel/DTS/build system) under `patches-core/`.  
  - Place package-specific patches under `package-patches/package/.../patches/`.

- **Overlays**  
  - Place modified package files directly under `package-patches/package/.../`.  
  - Place rootfs overlay files under `files/` (they will be copied into the firmware image).
