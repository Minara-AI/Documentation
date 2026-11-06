# Withdrawal issues

**My on-chain withdrawal was rejected.** Common reasons:

* Insufficient balance — leave enough to cover gas fees.
* Invalid withdrawal address format.
* Network mismatch between selected token and destination address.

If the issue persists after checking these, contact us on Discord.

**I'm not receiving the email verification code for my withdrawal.** Check your spam folder and make sure you're looking at the inbox linked to your Minara account. If you signed up with Apple and chose Hide My Email, Apple's private relay may have stopped forwarding Minara emails. See [I'm not receiving email verification codes from Minara](../account-and-access/login-and-access.md) for how to fix it and what to do if codes still don't arrive.

**Why can I trade on Solana but not withdraw when my wallet has no SOL?**

Withdrawals on Solana require a small SOL balance in your Minara Solana wallet to cover network transaction fees (gas) and any applicable account balance requirements. If your wallet has no SOL, especially if it has never been funded with SOL, your withdrawal may fail even if you have enough USDC or other tokens.

Deposit at least 0.003 SOL into the same Minara Solana wallet you are withdrawing from. Once the deposit arrives, try the withdrawal again.

Trading on Solana is not affected: Minara pays the SOL transaction fees on your behalf and recovers the cost from your balance. This fee-advance mechanism does not apply to withdrawals.

The SOL deposit is not a fee charged by Minara. Any remaining available SOL can be withdrawn later, subject to network fees and account requirements. Network transaction fees are non-refundable.

**My withdrawal hasn't arrived in my external wallet.** Most withdrawals complete within a few minutes. Check the transaction status on a blockchain explorer using your transaction hash. If the transaction is confirmed on-chain but hasn't appeared in your wallet, the issue is with the receiving wallet — contact that wallet's support.

**I accidentally withdrew to the wrong address.** On-chain transactions are irreversible. Minara cannot reverse a completed withdrawal. If the address belongs to a known exchange, contact that exchange's support with your transaction hash.
