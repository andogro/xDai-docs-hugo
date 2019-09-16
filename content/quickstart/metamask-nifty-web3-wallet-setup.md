+++
date = ""
draft = true
title = "Metamask / Nifty:  Web3 Wallet Setup "

+++
Use a web 3 wallet to connect your address to the staking interface and interact with your xDai and DPOS balances. These instructions cover chrome application features, but are similar for all browsers that support Web3 wallets.

1. Download Nifty Wallet or Metamask  
   {{% notice info %}}**Do not enable both wallets at the same time** as there can be conflicts between the two. Apps can be enabled/disabled in the chrome extensions interface.{{% /notice %}}
2. Once installed, go to [blockscout.com](http://blockscout.com/).
3. Change the BlockScout Network to xDai Chain and select an item from Stakes in top menu.
   1. `<xDai chain select screenshot>`
   2. `<stakes screenshot>`

### Nifty Wallet

1. Open Nifty Wallet by clicking on the icon, and check that you are connected to your correct address. Point the network to xDai Chain (preconfigured with Nifty)
2. Add the $DPOS token:
   1. Open TokensTab and click Add Token button `<screenshot>`
   2. Enter the following `(will change)`:
      1. Token Address: 0x6f7a73c96bd56f8b0debc795511eda135e105ea3
      2. Token Symbol: DPOS
      3. Decimals of Precision: 18
      4. Click Add
3. Nifty should be ready for staking. Make sure you have $DPOS on the xDai chain and enough xDai to cover basic transaction costs (1 xDai will cover @ 500 transactions). Instructions on acquiring $DPOS and/or xDai.

### Metamask

1. Open MetaMask by clicking on the icon, and check you are connected to the correct address in your wallet, then point network to custom URL:  
   `<screenshots>`
2. Fill in xDai network details:
   1. Network Name: XDAI
   2. New RPC URL: [https://dai.poa.network](https://dai.poa.network "https://dai.poa.network")
   3. Symbol: xDai
   4. Block Explorer URL: [https://blockscout.com/poa/dai](https://blockscout.com/poa/dai "https://blockscout.com/poa/dai")
   5. Click Save Button
3. Add the $DPOS token:
   1. Open Token Menu
   2. Select Add Token
   3. Select Custom Token and add the following:
      1. **Token Contract Address:** 0x...TBD...
      2. **Token Symbol:** DPOS
      3. **Decimals of Precision:** 18
      4. Click **Next**
   4. Click **Add Tokens**
4. MetaMask should be ready for staking. Make sure you have $DPOS on the xDai chain and enough xDai to cover basic transaction costs (1 xDai will cover @ 500 transactions).