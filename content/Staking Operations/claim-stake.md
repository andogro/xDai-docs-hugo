---
title: Claim Stake
date: 2019-09-11T20:08:03.000+00:00

---
Stake ordered for withdrawal is available to claim once the staking epoch in which the claim was ordered is complete. See the **important note below** related to actions that can cause a claim delay.

1. Check that your web3 wallet is connected with the correct address and you have enough xDai to process the transaction.
2. Click the Claim icon next to the pool you would like to claim your stake from. The icon will only appear once a claim is available.  
   ![](/uploads/0443bac2580f272b88c41ace451179192d76cffe_2_1380x664.png)
3. The modal will show the amount available to claim. Click the **Claim the Amount** button.  
   ![](/uploads/97b4c3050bce7fcdb6824b2866e5b6bf800f7422_2_1380x664.png)
4. Confirm the transaction with your web3 wallet. The claimed amount will be added to your address balance.

**Important:** If you place a withdrawal order in a staking epoch **before claiming your previously ordered amount**, your initial claim will be carried over and added to the new order, so that **no amount will be available to claim from that pool until the beginning of the next staking epoch**.

**For example:**

* **Staking epoch 100:** 5 $DPOS ordered for withdrawal.
* **Staking epoch 101:**5 $DPOS is available to claim. However, you place another order withdrawal for 7 $DPOS before claiming the available 5 $DPOS. The total ordered for withdrawal from the pool is now 12 $DPOS. This new amount will be available in the next staking epoch.
* **Staking epoch 102:** 12 $DPOS available to claim. This claim will continue to be available in subsequent staking epochs as long as another withdrawal order is not placed, which will delay claiming until the next staking epoch.