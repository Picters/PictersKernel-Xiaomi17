<p align="center"><img src="assets/logo.jpg" width="280" alt="Picters Kernel"></p>

# Picters Kernel · Xiaomi 17 series

Custom kernel for **Xiaomi 17, 17 Pro, 17 Pro Max and 17 Ultra** on **SM8850**.
Built on [Kokuban's kernel](https://github.com/YuzakiKokuban/android_kernel_xiaomi_sm8850), with BakaSU and additional USB drivers.

- External Wi-Fi: Realtek RTL8812AU, RTL8812BU, RTL8814AU and RTL8188EUS; monitor mode and packet injection.
- Extra drivers: USB Ethernet, USB serial, CAN and DVB / SDR.
- **Picters Modules Manager:** Stock / Inject switching, adapter controls and CPU / GPU profiles.

## Downloads

[**Latest release**](https://github.com/Picters/PictersKernel-Xiaomi17/releases/latest)

| Vendor channel | Kernel | KMI |
| --- | --- | --- |
| A17 | 6.12.69 | 6 |
| A16 | 6.12.23 | 5 |

Choose by your **vendor KMI**, even if your ROM runs a newer Android version. Use the kernel and PictersKernelPack from the same build.

Using a Pro, Pro Max or Ultra? [Let me know in Issues](https://github.com/Picters/PictersKernel-Xiaomi17/issues/new) if it works. Include your model, ROM and vendor KMI.

## Install

1. Flash the matching **Kernel ZIP** with an AnyKernel3-compatible installer, then boot Android.
2. Install the matching **PictersKernelPack ZIP** through your root manager and reboot.
3. Open **Picters Modules Manager** and grant root. Enable **Show system apps** in your root manager if needed.

The pack includes the app and extra modules. The app opens GitHub Releases for manual updates.

## Credits

[YuzakiKokuban](https://github.com/YuzakiKokuban) · BakaSU / KernelSU · AnyKernel3 · [aircrack-ng](https://github.com/aircrack-ng) · [morrownr](https://github.com/morrownr)
