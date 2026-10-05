# arctide-connect

The wallet-connection page for the Arctide Telegram bot (@Arctide_TheFlock_Bot).

A user taps **🔗 Connect wallet** in the bot, this page opens inside Telegram, their wallet signs a
one-time code, and the bot verifies the signature to learn that they control the wallet. Signing is
free, is not a transaction and cannot move funds. The page never asks for a seed phrase or key.

- `connect/index.html` only signs the bot's own link-code text (a strict pattern): it cannot be used
  to get any other message signed.
- Inside Telegram the result goes straight back to the bot (`Telegram.WebApp.sendData`). Opened in a
  wallet app's browser instead, the page shows a proof (address + signature) to paste into the bot.
- WalletConnect (mobile wallets inside Telegram) turns on when `WALLETCONNECT_PROJECT_ID` is set to a
  project id from cloud.reown.com with this site's domain allowed.

The bot side lives in `community-bot/bot/staking.py` and `ethsig.py`; set the bot's
`WALLET_CONNECT_URL` to this site's `/connect/` address.
