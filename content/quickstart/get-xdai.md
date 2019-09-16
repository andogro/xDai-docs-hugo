---
title: Get Xdai
date: 2019-09-11T20:08:03.000+00:00

---
To start staking on the xDai Stable Chain, you will need the Minimum required stake in $DPOS, as well as a small amount of xDai in order to pay for staking transactions. (Note: 500 transactions will cost slightly over .01xDAI, so $1.00 in xDai will allow for lots of staking!!) xDai is also used for any other on-chain transactions.

Steps to get xDai:

1. **Acquire DAI**  
   There are several methods to acquire DAI on the Ethereum Mainnet.
   1. Directly through an exchange or other service with USD:  
      Bibox, Coinbase, Changelly, Wyre
   2. Convert other ERC20 assets to DAI (like ETH -> DAI)
      1. Uniswap
      2. Bangor
      3. Kyberswap
      4. [https://eth2dai.com/market/WETH/DAI](https://eth2dai.com/market/WETH/DAI "https://eth2dai.com/market/WETH/DAI")
   3. Generate DAI with a CDP: [https://cdp.makerdao.com/](https://cdp.makerdao.com/ "https://cdp.makerdao.com/")
2. **Transfer DAI to xDai**   
   You can transfer directly from the bridge, or use a bridge enabled wallet to complete the conversion.
   1. **Directly from Bridge:**
      1. Go to: [https://dai-bridge.poa.network/](https://dai-bridge.poa.network/ "https://dai-bridge.poa.network/")
      2. Connect your web3 wallet (Metamask/Nifty) to the Ethereum Mainnet.
      3. You will see your DAI balance on the left hand side of the bridge, and your xDai balance on the right. Enter the amount of DAI you would like to convert to xDai and click Transfer.
      4. Confirm your Request by pressing the Continue button
      5. Submit the transaction in the wallet popup
      6. Wait for the necessary block confirmations
      7. Once complete, you will see a success message. The requested amount of xDAI (minus a 1% fee*) will be minted to your wallet account on the xDai network.
      8. To check the amount of xDai, Change the RPC in Metamask to point to [https://dai.poa.network](https://dai.poa.network "https://dai.poa.network"). If you have not added previously:
         1. Click the network dropdown at the top
         2. Select Custom RPC
         3. Enter in xDai for the Network name, [https://dai.poa.network](https://dai.poa.network "https://dai.poa.network") for the New RPC URL, XDAI for the symbol, and click SAVE.
         4. Change the network to xDai to view your xDai balance.
      9. To convert from xDai back to DAI, follow the process above, but in step #2 connect your web3 wallet to the xDai network instead of the Ethereum Mainnet. You will now see your xDai amount on the left hand side of the bridge, and DAI on the right. Follow the same processes to transform your xDai back to DAI*.
   2. **DEX Wallet:**
      1. [https://forum.poa.network/t/dexwallet-guide/1787](https://forum.poa.network/t/dexwallet-guide/1787 "https://forum.poa.network/t/dexwallet-guide/1787")
      2. To acquire xDai, use the ‘Buy’ menu item and follow the prompts. [https://medium.com/dexlab-io/dexwallet-welcomes-poas-xdai-chain-17d4a45a3453](https://medium.com/dexlab-io/dexwallet-welcomes-poas-xdai-chain-17d4a45a3453 "https://medium.com/dexlab-io/dexwallet-welcomes-poas-xdai-chain-17d4a45a3453")
   3. **Burner Wallet:** 
      1. [https://forum.poa.network/t/burner-wallet-guide/1873](https://forum.poa.network/t/burner-wallet-guide/1873 "https://forum.poa.network/t/burner-wallet-guide/1873")
         1. Press **exchange button** and follow prompts.
         2. Process is shown in more detail here: [https://medium.com/@jaredstauffer/how-to-get-xdai-how-to-convert-dai-to-xdai-eth-dai-xdai-30a60e4b6641](https://medium.com/@jaredstauffer/how-to-get-xdai-how-to-convert-dai-to-xdai-eth-dai-xdai-30a60e4b6641 "https://medium.com/@jaredstauffer/how-to-get-xdai-how-to-convert-dai-to-xdai-eth-dai-xdai-30a60e4b6641")

_*A 1% fee will be extracted during any bridge conversion (DAI -> xDAI or xDai -> DAI). This fee supports the on-chain DPOS consensus, and is split equally amongst the active validator pools when the bridge transaction is executed._