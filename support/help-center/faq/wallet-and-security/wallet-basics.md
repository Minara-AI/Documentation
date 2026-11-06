# Wallet and balance

**My balance shows $0 or won't refresh. Are my funds missing?** A $0 balance is often a temporary data-loading issue, not proof that your funds have moved. Check your network connection and API rate limits first.

Hyperliquid rate-limits API requests. Keeping several Minara Perps windows open alongside Hyperliquid windows can send too many concurrent requests. When this happens, the Minara front end may be unable to fetch the latest account data and can temporarily show $0 or a stale balance.

1. Close extra Minara Perps and Hyperliquid windows.
2. Wait a few minutes, then refresh a single Minara window.
3. Confirm that you're viewing the correct wallet: EVM Spot Wallet, Solana Spot Wallet, or Perps wallet.
4. If the balance still does not load, open a [Discord](https://discord.com/invite/minaraai) ticket with your wallet address, a screenshot, and the approximate time the issue started.

If the balance changed after a deposit or withdrawal, also check Asset → Activity and include the transaction hash in your support ticket.

**Will Minara execute trades without my authorization?** No. Every trade requires your explicit confirmation. Large transactions trigger a secondary confirmation step. Automated strategies (Autopilot, Workflow) only execute after you have explicitly activated them.

**What kind of wallet does Minara use?** Minara creates a non-custodial smart contract wallet for each user, built on the ERC-4337 standard (powered by [Privy](https://www.privy.io/)). It is an on-chain wallet — not stored in Minara's internal database. Minara can manage funds in the wallet but cannot hide, delete, or blacklist it. Every transaction is publicly verifiable on-chain.

**I sent assets to the wrong chain. Can I get them back?** If you sent to a supported chain you didn't intend (for example, USDC on Ethereum instead of USDC on Base), contact support on [Discord](https://discord.com/invite/minaraai) immediately with your transaction hash. Recovery options depend on the specific situation, but assets sent to a supported chain can often be accessed.

If you sent to an unsupported chain entirely, see below.

**I deposited from an unsupported chain. Can I recover my funds?** Contact us on Discord immediately with your transaction hash. Recovery is not guaranteed — common reasons for unrecoverable deposits are unsupported blockchains or incorrect recipient addresses.

**How do I export my private key?** See [Export your private key](export-private-key.md).
