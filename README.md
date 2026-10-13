### 🚀 RedMagic 11 Pro: 16GB ZRAM & RamSlider Mod v1.0

This release provides the necessary components to unlock a true **16 GB ZRAM + 16 GB Writeback** configuration on the RedMagic 11 Pro (REDMAGICOS 11, Android 16).

---

### 📦 Included Files
1. **`zram16_v1.1.zip`** (Magisk / KernelSU Module)
   - Overlays vendor fstab configurations to support 16 GiB `zramsize`.
   - Generates and includes the missing 13–16 GB writeback backing files (`/data/per_boot/zram_swap`).
2. **`RamSlider_v1.1.apk`** (LSPosed Module)
   - Hooks into ZTE's `Settings_MFV_abroad` (`Settings` app).
   - Bypasses the hardcoded `1-12` cap in `MindSyncUtils`.
   - Dynamically scales the slider to 16 steps and auto-positions custom labels.

---

### ⚙️ Installation Instructions

#### Step 1: Flash the ZRAM Module
1. Flash **`zram16_v1.0.zip`** in Magisk or KernelSU.
2. Reboot your device.

#### Step 2: Install and Configure the LSPosed Module
1. Install **`RamSlider_v1.0.apk`** normally.
2. Open your LSPosed manager (Vector), enable the module, and check **`com.android.settings`** as scope.
3. Force stop the **Settings** app (`com.android.settings`).
4. Go to **Settings -> Storage / RAM expansion**, select **16 GB**, and hit **Restart Now**.

---

### 🔍 Verification
Run the following command in Termux (with root) to check your active ZRAM configuration:
```sh
su -c 'getprop persist.zte.mindsync.zram.wb_size; cat /sys/block/zram0/disksize; cat /proc/swaps'
