---
description: Find answers to common issues.
---

# Troubleshooting

## I cannot connect to the platform

* Make sure to select the correct network (Ethereum Mainnet or Gnosis Chain). Normally on the wallet provider you can switch the network in the settings option.
* On a non-custodial wallet app (e.g. Rabby):
  * Make sure to unlock and select Ethereum app.
  * Make sure contract data is allowed on the Ethereum app settings.
* On custodial wallet app (e.g. Coinbase):
  * Use the scan QR option to connect.
  * If you want to access directly from the wallet browser, just go to app.spark.fi.
* Using Wallet Connect:
  * Use the scan QR code to connect

## Why is my Wallet Blocked?

Spark receives blockchain intelligence provided by [TRM Labs](https://www.trmlabs.com/). TRM combines on-chain data and real-world investigations to identify financial crime and other prohibited activities. This data blocks wallets from app.spark.fi that are associated with certain legally prohibited conduct.If you believe your address has been incorrectly flagged, please contact [contact@marsfoundation.xyz](mailto:contact@marsfoundation.xyz).

**What information is shared with TRM Labs?** Your address is shared with TRM, but no metadata is tracked or shared. The request from the UI is routed to the SparkLend hosted API, which is used as a proxy endpoint, and the address is passed directly through to the TRM service. Users' IP addresses are not shared with TRM.

## I cannot send transactions

Make sure you have enough ETH in your wallet to pay the transaction fees. Depending on the network status, the cost of the transactions may vary. At least 0.05 ETH is required to interact properly.

### Enable contract data on Ledger

If you are using a Ledger hardware wallet, make sure to select the Ethereum app and enable contract data.

To enable contract data:

* Connect and unlock your Ledger device.
* Open the Ethereum application.
* Press the right button to navigate to Settings.
* Then press both buttons to validate.
* In the Contract data settings, press both buttons to allow contract data in transactions.
* The device displays Allowed.

[Here is a visual guide.](https://teckers.co/uniswap-ledger/)

## The site does not load

The following steps may solve your problems:

* If you are using Brave browser, switch to another browser to see if the issues are related to Brave. If it is related to Brave browser some helpful actions are:
  * Clearing cache data and cookies for the site
  * Hard refresh with control + F5 (or cmd + r)
  * Disable brave wallet (or the wallet not being used as default, e.g. metamask) or other extensions that might be interfering with proper connection with the wallet
  * If the site still won't load after taking the steps above, you will have to use the platform in another browser.
* Make sure your internet connection is working and stable
* Restart the browser and try to connect again
* Try to hard refresh the site with control + F5
* Check if there are any updates for your browser or wallet provider. If so, update it to the latest version.

### IPFS Troubleshooting

If the Cloudflare gateway is not working and you are unable to connect to [app.spark.fi](https://app.spark.fi), you can use any public or private IPFS gateway supporting origin isolation to access the Spark interface:

* Go to `<your favorite public ipfs gateway>/ipns/app.spark.fi`
* Make sure the gateway supports origin isolation to avoid possible security issues
* You should be redirected to a URL that looks like `https://app-spark.fi.<your gateway>`

## My transaction is stuck pending confirmation

In this situation make sure to not keep sending transactions, as every new transaction will be stuck pending the oldest transaction to be confirmed. You can get rid of the stuck transaction by speeding it up or cancelling it. Depending on the wallet you are using, you may have that option natively.

For example, Metamask or Trust Wallet both have the options to cancel or speed up transactions.

Alternatively, if your wallet provider doesn't have this option, you can still drop the stuck transaction by sending a 0 ETH transaction, to your address (yourself) using the same nonce (number id) as the stuck transaction. You can inspect the nonce in your stuck transaction in [Etherscan](https://etherscan.io) and use interfaces such as [MyCrypto ](https://mycrypto.com/)to send a 0 ETH transaction with a higher gas cost to replace the one that is stuck.

Here is a guide about the topic for [MyCrypto](https://support.mycrypto.com/how-to/sending/checking-or-replacing-a-transaction-after-it-has-been-sent).

:::info
If you still have any questions or issues, feel free to reach out to the Spark team on the official [Discord](https://discord.com/sparkdao).
:::
