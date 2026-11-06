# Reset your 2FA

**I can't get a verification code from my authenticator app. How do I reset 2FA?** This happens when you turned on two-factor authentication in Minara (for example, the first time you exported a private key) but never added the setup key to Google Authenticator or another authenticator app. Without the setup key, no app can generate codes for your account, and Minara can't show the setup key again. Minara can remove 2FA from your account once you prove the account is yours. You can then set up 2FA again.

{% hint style="warning" %}
Minara support will never ask for your private key, seed phrase, or a verification code. If someone asks for any of these, it's a scam.
{% endhint %}

**What do I need to do?**

Open a ticket on [Discord](https://discord.com/invite/minaraai) and include the email address linked to your Minara account and your Minara UID. Minara verifies account ownership through your deposit wallet or your payment details, so the next step depends on how you have used your account:

_**If you have deposited to Minara before**_

1. Support gives you a verification amount with two decimal places, for example **10.28** or **10.19**. The amount is different for each request.
2. Deposit **exactly** that amount into your Minara wallet, **from the same external wallet you used for your earlier deposits**. A different amount, or a deposit from another wallet, cannot be used for verification.
3. Reply in your ticket with the transaction hash.

_**If you have never deposited, but have paid for a subscription**_

No deposit is needed. Tell support in your ticket that you have a paid plan. The team verifies your identity using the payment information from your subscription.

_**If you have never deposited and never paid for a subscription**_

Minara cannot verify that the account is yours, because identity is verified only through a deposit wallet or payment information. In this case, create a new Minara account instead.

After your identity is confirmed, support passes your request to the engineering team, who remove 2FA from your account. You'll get a reply in your ticket when it's done.

**Can I verify by sending an email from my account's email address instead?** No. 2FA is an extra layer of protection on top of your email login. If an email from your account address were enough to remove it, anyone who gained access to your email could also take over your Minara account, and 2FA would no longer protect you. That's why Minara only accepts verification through your deposit wallet or payment information.

**How do I avoid this next time?** The next time Minara asks you to set up 2FA, scan the QR code with your authenticator app before you click **Next**. Also save the manual setup key in a password manager or another secure place. If you lose your phone, you can restore your codes in a new app with that setup key.
