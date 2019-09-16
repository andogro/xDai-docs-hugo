+++
date = "2019-09-16T06:00:00+00:00"
title = "Staking Terminology & Glossary"

+++
# Active Pool

Active pools consist of all candidate and validator pools eligible to join the next staking epoch as members of the validator set. At the end of a staking epoch, the new validator set is constructed from this list. Active pools with higher stake have a higher likelihood of selection to the next epoch, but all active pools have a chance to be selected (randomness introduces variation in selection).

To be considered active, a pool must contain at least the minimum stake amount (see the whitepaper) and be in good standing (not banned).

All active pools are listed in the active pools tab, arranged from highest stakes ratio to lowest stakes ratio. Delegators may add or move stake to and from active pools during a staking window. However, if the active pool is a current validator, the change in stake amounts will not take effect until the next staking epoch. A withdrawal from a validator’s pool is limited to the amount staked during the current staking epoch. However, any delegator in the validator’s pool (including the validator themselves) can order a withdrawal and remove their stake during the next staking epochs.

# Active Stake

Stake currently in use by the validator set is called active stake. The amount of active stake is snapshot at the beginning of each staking epoch and used as the basis for reward distribution among validator pools at the end of the epoch.

Additional stake can be placed on validator pools during a staking epoch, however, this is pending stake and does not impact the pool until the next staking epoch. Active stake cannot be withdrawn or moved during a staking epoch, but it can be ordered for withdrawal (the withdrawal amount can be claimed beginning with the next staking epoch).

# AuRa Algorithm

AuRa stands for Authority Round. It is the underlying algorithm currently used by the xDai chain to ensure validators produce blocks in an honest and timely fashion. In AuRa, validators take turns proposing blocks, and a majority of validators in the current active set must agree a block is valid before it is finalized. For more information, see [https://wiki.parity.io/Aura](https://wiki.parity.io/Aura "https://wiki.parity.io/Aura")

There are plans to update the AuRa algorithm to Honey Badger BFT in future iterations of the xDai Stable Chain. More information on Honey Badger is available here [https://forum.poa.network/c/posdao/hbbft](https://forum.poa.network/c/posdao/hbbft "https://forum.poa.network/c/posdao/hbbft")

# Balance

The balance is the amount of $DPOS available on a participant’s address connected by a web3 browser extension (like MetaMask or NiftyWallet). The available balance, along with the current staked amount, is displayed below the connected address in the UI. If $DPOS is acquired on the Ethereum mainnet through an exchange, crowdsale, or other means, it must be converted to xDai $DPOS using the bridge before it can be used for staking on the xDai Stable Chain.

<screenshot - waiting for next iteration>

# Ban

A ban occurs due to validator misbehavior. This can include:

* not revealing a secret number more than 20 times in a staking epoch
* not revealing a secret number on the last reveal round of a staking epoch
* Reported malicious behavior (ie releasing 2 blocks at the same step or releasing a block out of order) by other validators
* Too many calls to the reportMalicious function (spam calls)

When a validator is banned, they are immediately removed from the current staking epoch and moved to the inactive pool list. They do not receive any rewards from the staking epoch. Rewards are distributed among the remaining validators in the set at the end of the staking epoch.

Any funds in the pool (validator and delegator stakes) are frozen for a period of 90 days. During that time, the mining address of the banned validator is prevented from participating in an active pool. At the end of 90 days, the funds are released and can be withdrawn or moved to another pool, and the ban is lifted.

To reactivate a banned pool after the 90 day ban is complete, a candidate must increase their stake by any amount, as long as the total amount is equal to the minimum candidate stake requirements. Adding stake calls the `stake` function and reinstates the pool.

# Block number

Each block in the chain is numbered sequentially starting from the genesis block. The block number displayed in the BlockScout interface corresponds to block height; it is the most current block in the chain.

# Block/Bridge rewards

Validators and their delegators receive rewards in exchange for securing the chain. Rewards are divided equally among each validator pool participating in the current staking epoch. At the end of each staking epoch, reward funds collected by validator pools are distributed amongst the validator and the delegators according to the reward distribution rules.

Within each pool, these rewards are further divided based on the reward

Rewards take two forms; block and bridge rewards.

* Block rewards are allocated in $DPOS, and sent to the validator pool (validators & delegators) responsible for creating and signing a block. Transaction fees in xDai are given to validators only (not the validator pool).
* Bridge rewards are collected whenever funds (either xDai or $DPOS) are moved into or out of the chain. An entrance or exit fee is charged, and this fee is equally distributed to all validator pools in the validator set in place when the funds are bridged.

Reward funds collected by validator pools are distributed amongst the validator and the delegators according to the reward distribution rules at the end of each staking epoch.

![](/uploads/Block_Bridge_rewards.png)

$DPOS is the staking token, and xDai is the Native Coin. The 70/30 Split rules are detailed in the fees section.

# Bridge

A bridge uses the TokenBridge technology to connect two chains to one another, allowing for asset conversion from 1 chain to the other. The basic mechanism involves bridge smart contracts which locks assets on one side and mint them on the other. When the assets are moved back across the bridge, they are burned and unlocked. Bridges have their own set of validators which monitor token transfers.

![](/uploads/Bridge_1.png)

The xDai Stable Chain operates with two bridges:

1. An ERC20-to-Native Bridge converts DAI to xDai and vice versa. When Dai is “bridged”, the specified amount of DAI is locked in a contract and a corresponding amount of xDai is minted on the xDai Stable chain. During this minting process, a 1% fee is collected for validators (ie. if 100 DAI are “bridged”, 99 xDai are transferred to the user’s wallet and 1 xDai is equally distributed amongst the current validator pools). When converted back, a 1% exit fee is collected in the same manner. These fees are distributed at the end of a staking epoch.
2. An ERC20-to-ERC20 bridge converts $DPOS ERC20 tokens on the Ethereum mainnet to $DPOS on the xDai chain and vice versa. A 1% fee is also collected on entrance/exit and distributed to current validator pools.

**BRIDGE HOW TO NEEDED……**

Future bridge implementations will extend the multi-staking capability of the $DPOS token, allowing additional sidechains to use $DPOS as a staking token via bridge connections.

![](/uploads/Bridge_2.png)

# Candidate

To become a validator and produce blocks on the chain, a participant must first declare themselves as a candidate. Candidates meet all the requirements of a validator, and are available for selection as validators for subsequent staking epochs.

To become a candidate, a participant must:

1. Acquire both bridged $DPOS and xDai tokens. This includes at least the minimum required candidate stake in $DPOS and a small amount of xDai to process transactions. Recommended amounts: ??
2. Configure and run a node that meets the technical requirements for the protocol. Once the node is functional, a participant can become a candidate by enabling a web3 wallet with their staking address, providing the mining address associated with their node, and staking the minimum required candidate stake.

<screenshot of become a candidate modal - need lorem ipsum eliminated>

Once added, candidates may attract delegators to stake into their pools, increasing the chances of the candidate’s selection to the next validator set.

When the next staking epoch begins, candidates are selected as validators based on the total amount of stake in their pool as well as a random number which provides some variation in the selection process (if there are greater than 19 candidates).

Candidates who are not selected remain in active pool list, and can attempt to attract more stake to increase their selection chances in the next epoch if they choose to do so.

Every current validator can also be thought of as a potential candidate for the next validator set. Delegators can place stake on currently active validators, and this pending delegation stake (along with the previous placed stake) will be considered during selection for the next staking epoch.

# Candidate Pool

The candidate pool is the total amount of $DPOS stake currently placed on a candidate. This includes their stake amount as well as any additional delegator’s stake. The larger the size of a candidate’s pool, the greater their odds of selection to the next validator set.

# Claim Ordered Withdrawal

Stake ordered for withdrawal is available to claim once the staking epoch in which the claim was ordered is complete. To claim an ordered withdrawal, simply click on the Withdraw/Claim button and claim the ordered amount from the popup window. The claim will be processed through a web3 connected wallet, and will require a minimal amount of xDai to complete the transaction.

# Delegator

Delegators are participants who provide additional stake to protect the chain, but are not validators themselves. They do not need to run a node, and do not assume responsibility for consensus. To delegate, a participant must have both bridged $DPOS and xDai, and place at least the minimum amount of delegator stake (see the whitepaper) on a candidate pool. Delegators can place stake on multiple candidates, move stake from one candidate to another, or withdraw stake from candidates at any time.

Delegators place stake on candidates they believe will make good validators. Once a candidate becomes a validator, the delegator’s stake is activated and may not be withdrawn or removed during the current staking epoch. However, active stake can be ordered for withdrawal, and additional stake can be placed on an active validator (within the staking window) in anticipation of the next staking epoch.

Stake delegated to a validator accrues rewards for the delegator. While all validator pools within a validator set receive the same share of rewards, rewards within each pool are shared proportionally based on the amount of stake provided by the validator and the delegators. This may influence delegation strategies (ie delegating to a smaller pool can increase the reward amounts if that candidate is chosen as a validator).

Pool rewards are proportionally distributed between a validator and the staking delegators, as long as the total delegators’ percentage of stake is below 70%. If the total delegators’ stake exceeds 70%, the delegators’ rewards are adjusted accordingly and the validator receives 30%.

If a validator is banned, any stake within the banned pool (including delegated stake) is frozen for a period of 90 days and can be withdrawn only when the ban is over. Delegators should perform due diligence when selecting candidates to stake on, and should think of their stake as a “vote” for that candidate to become a validator for the next staking epoch.

# $DPOS token

$DPOS is the staking token for the xDai Stable Chain. It is an ERC20 equivalent (ERC677) on the Ethereum mainnet, and an ERC20 equivalent (ERC677) when bridged to the xDai chain. $DPOS is available in limited, hard-capped amounts in an initial public and private offering. It can be obtained through exchange listings… more info here on where it is available, how to obtain.

The majority of $DPOS is generated as rewards for validators and delegators on the chain. Details regarding the emission rate and distribution is available here. [$DPOS Staking Token Rewards and Emission Model](https://forum.poa.network/t/dpos-staking-token-rewards-and-emission-model/2469)

# DPOS (Delegated Proof of Stake)

Delegated Proof of Stake (DPOS) is an extension of Proof of Stake - a consensus model that provides rewards to validators in exchange for providing an amount of tokens as stake. This staking process incentivizes validators to act in the best interests of the network, as their stake will be impacted if malicious behavior is detected.

To increase the decentralization of this model and allow for wider community participation, the DPOS model allows any token holders to deposit stake. Delegators do this by placing stake on potential validators (either current validators who may be elected to the next validator set, or candidates who are not currently validators).

Delegators do not participate in block production themselves, but provide leverage to candidates they feel will make good validators. If these candidates are selected, rewards are divided amongst the validator and their delegators.

DPOS provides the opportunity for delegators to “vote” on potential validators by staking tokens on them. Candidates are incentivized to maintain a good reputation in order to attract more delegators and increase their chances of becoming validators. The POSDAO algorithm supports a DPOS model.

For more information on DPOS, see: [https://steemit.com/dpos/@dantheman/dpos-consensus-algorithm-this-missing-white-paper](https://steemit.com/dpos/@dantheman/dpos-consensus-algorithm-this-missing-white-paper "https://steemit.com/dpos/@dantheman/dpos-consensus-algorithm-this-missing-white-paper")

# Emission Curve, Emission Schedule

The emission curve or schedule refers to the total amount of tokens that will be generated by a platform.

The $DPOS staking token will be released according to a unique emission schedule. A majority of tokens are released by the protocol as rewards (73 million). Rewards will be generated at a higher rate at the beginning of the protocol, and will gradually taper to an annual APR of 4%. In total, 100 million $DPOS will be released. For more information see: [$DPOS Staking Token Rewards and Emission Model](https://forum.poa.network/t/dpos-staking-token-rewards-and-emission-model/2469)

xDai emission rates will not be determined by the protocol, as xDai is peggged directly to DAI, and the amount of xDai is always equal to the amount of DAI locked in the bridge smart contract.

# Epoch (Staking Epoch)

The time duration (in blocks) for which the validator set is selected. On the xDai Stable Chain AuRa implementation, each staking epoch lasts for 120954 blocks, which corresponds to a one-week timeframe with 5 second blocks. This value is configurable for other chains adopting the protocol.

# Epoch number

The number of the current staking epoch. The staking epoch increments every 120954 blocks on the xDai chain. A new validator set is chosen for each epoch.

# Fees

Fees are collected from users of the xDai chain and divided amongst validator pools. Fees are charged for bridge events and transactions.

* Bridge fees: A 1% fee is charged whenever tokens are locked or unlocked in a bridge contract. This entrance and exit fee is collected for both Dai <-> xDai transfers (collected in xDai) as well as DPOS (mainnet) <-> DPOS (xDai chain) transfers (collected in $DPOS). Assessed bridge fees are split equally between validator pools active at the time of transfer.
* Transaction Fees (Gas fees): Transaction fees are assessed for any xDai transactions such as sending xDai to another wallet or interacting with a smart contract. These fees are sent to the validator who seals the block in which the transactions take place (transaction fees are not split among pool participants, they are only received by the validator). Transaction fees on the xDai chain are extremely low. As an example, during EthDenver over 38,000.00 of transactions were cumulatively charged less than .20 in transaction fees.

# Hard Cap

The $DPOS token is subject to limited distribution, and the hard cap describes the maximum amount that will be released to various entities. During the initial offering, the public hard cap is 1,000,000 $DPOS tokens, and the private hard cap is 8,500,000 tokens. For additional information related to the release schedule, see [$DPOS Staking Token Rewards and Emission Model](https://forum.poa.network/t/dpos-staking-token-rewards-and-emission-model/2469)

# Inactive Pool

Inactive pools are candidate pools which do not meet the ‘active pool’ criteria. This includes banned validator pools and previous candidates/validators who do not meet the minimum stake requirements (this can occur if funds are withdrawn or if a validator chooses to remove their pool).

Underfunded pools are reactivated and moved to the active pools section once the minimum stake requirements are met (their status is updated in the following block).

To reactivate a banned pool after the 90 day ban is complete, a candidate must increase their stake by any amount as long as the amount is at least equal to the minimum stake requirements. Adding stake calls the `stake` function and reinstates the pool.

# Initial Validators

The protocol is designed to begin with a set of predefined validators. After the first staking epoch, this validator set can change depending on the presence of additional candidates. The initial validator set for the xDai Stable Chain is comprised of the same group of validators responsible for securing the chain prior to the POSDAO upgrade. See this post for more information regarding this select group.

# Mining Address

The mining address is used by a validator’s node to sign blocks, participate in the randomness beacon, and report on any malicious validators. Mining addresses have the ability to call certain functions using a zero gas price. This address must be configured on the node and provided to the interface when becoming a candidate.

To start, generate a new Ethereum address and corresponding private key using tools such as MyCrypto, Metamask etc. Create a new account and export and save the private key.

Next, follow the instructions for setting up a new xDai node. You will provide the mining address and JSON keystore password during node setup.

Once your node is ready, you can become a candidate through the web UI. You will enter in the node’s mining address during this process.

# Minimum Stake

A pool must contain at least the minimum amount of stake from a candidate in order to become active. Minimum stake requirements exist for validator candidates as well as for delegators. The minimum stake amount for delegators is much lower.

* For validator candidates, the minimum stake is…# here
* For delegators, the minimum stake is ….# here per candidate . Stake may be placed on multiple candidates, but at least … must be placed on each candidate/validator.

If a candidate tries to place an amount of stake that does not meet the minimum stake requirements, their pool is not created.

# Move Stake

Delegators and candidates can move stake between different candidate pools. Stake can be moved from active or inactive candidate pools at any time. If stake was placed on a current validator during the current staking epoch, it is pending stake and may be moved. However, stake placed on a current validator during a previous epoch is currently in use (active stake), and cannot be moved. To reallocate active stake, follow the order a withdrawal process.

To move, click on the move stake icon associated with the pool where the stake is placed. A pop-up will present information about the current amount staked in the pool and a dropdown list of pools where the stake may be moved. Select the amount to move and the pool you would like to move the stake to. That pool’s information will populate in the modal. Click the move stake button to confirm the move. A transaction will be registered in your web3 wallet (metamask etc.) and stake will be moved to the new pool.

# Node

Candidates and validators are responsible for maintaining a node capable of verifying transactions and storing the entirety of the chain. A node must meet the technical requirements of the protocol. Instructions for setting up a node are available here .

# Order Withdrawal

Active stake cannot be immediately withdrawn by a delegator or validator from a validator pool, however, an order may be placed to withdraw this stake. Once the epoch is complete, the ordered amount is available to be claimed.

To order a withdrawal, click on the withdraw icon associated with the validator pool you would like to withdraw from. The withdraw popup will appear. Enter the withdrawal order amount.

If this is an active validator, the Withdraw Now button will be inactive, and the Order Withdrawal button will be active. Click the Order Withdrawal button to complete the order.

If an order for withdrawal has already been placed during the current staking epoch, it is possible to update this order using the same interface. Entering an additional positive amount will increase the order withdrawal, and entering a negative amount will decrease the order accordingly.Withdrawal orders can be claimed once the current staking epoch is complete and a new staking epoch begins.

# Pending Stake

Pending stake is stake placed during the current staking epoch which is not yet activated. It does not impact the current staking epoch. Pending stake can be moved, increased, or withdrawn during the staking window. Once the window is closed, any placed stake is frozen until the next staking epoch begins.

# POSDAO

POSDAO stands for Proof of Stake Decentralized Autonomous Organization, and describes the overall protocol design underlying the xDai Stable Chain. POSDAO is designed to provide a decentralized, fair, and energy efficient consensus for public chains. The algorithm works as a set of smart contracts written in Solidity. Details are available in the POSDAO whitepaper [POSDAO white paper](https://forum.poa.network/t/posdao-white-paper/2208)

# Remove My Pool

The Remove My Pool function removes a pool from selection consideration for the next staking epoch. It moves any active pool to the inactive pools list, and ensures that a current validator pool completes the current staking epoch but does not participate in new validator set selection at the end of the epoch.

The Remove My Pool link appears in the header (instead of the become a candidate button) when the application is accessed using an associated staking address. Clicking on this link will initiate the transaction to move the pool to the inactives list. All staked funds will remain in the pool during this process.

# Reward distribution rules

Block rewards are shared by all validator pools participating in consensus. Rewards are distributed to validator pools according to the following rules:

1. Each pool in the validator set receives an equal share of the block reward on block creation.
2. Pool rewards are distributed proportionally, as long as the total delegator’s stake is below 70%.
3. The validator is guaranteed to receive at least 30% of the pool reward. If the total delegator’s stake exceeds 70%, the delegators’ rewards are adjusted accordingly.

Rewards are tallied and stored in a smart contract as each block is closed, and are distributed at the end of each staking epoch.

Detailed examples are available in the POSDAO whitepaper. [POSDAO white paper](https://forum.poa.network/t/posdao-white-paper/2208)

# Secret number, Randomness Beacon

The protocol implements a random number generator similar to ​RANDAO​, which is used to select a set of validators from the group of candidates at the start of each staking epoch. This number is used to add random variation to validator selection, although candidates with larger pools have a higher likelihood of selection to a validator set for each staking epoch (candidates with higher stakes are probabilistically selected as validators for more staking epochs).

This random number is generated by the current validator set during the staking epoch. Generation consists of several commits and reveal rounds, resulting in a cumulative process where entropy increases over the course of the epoch. If a validator skips revealing their secret number too often, or fails to reveal it in the last collection round (which can influence selection for the next validator set), they are treated as malicious and banned.

# Stake, Staked

Stake is an amount of $DPOS tokens deposited into the protocol by validators, candidates, and delegators. Stake protects the protocol and promotes honest behavior; users who provide stake do not want to lose this stake or potential rewards due to malicious behavior (See banning for details and consequences related to malicious behavior). The total stake amount in a pool influences the likelihood of that pool’s selection to a validator set. The more stake contained in a candidate’s pool, the higher their probability of selection to a validator set.

Contrary to many Proof of Stake implementations, total pool stake amounts do not correspond to higher validator rewards in the POSDAO protocol. Each validator pool within a validator set receives the same reward for participating in consensus and securing the chain. However, staking percentages do impact distribution within each pool, as the amount of stake provided by delegators determines the amount of reward the validator and each of their delegators receive.

Stake is managed according to the following rules:

* Stake can be placed, moved, or withdrawn (or ordered for withdrawal) during the staking window, which begins immediately after the previous stakes snapshotting process finishes when a staking epoch begins, and ends 6 hours prior to the end of a staking epoch. No staking actions can take place outside of the staking window.
* Stake can be freely placed, moved, or withdrawn from candidate pools during a staking epoch.
* Stake may be placed on a current validator pool, however it will not impact current pool rewards or staking percentages until the following staking epoch. In this case, it is referred to as pending stake.
* Pending stake may be moved or withdrawn during the staking window.
* Active stake placed in a validator pool may be ordered for withdrawal. When the staking epoch is complete, this ordered amount may be claimed.

# Staking Address

The Ethereum address related to a candidate or validator and used to place stakes and collect rewards. The staking address is tied to the mining address when completing the Become a Candidate process.

A staking address is generated just like any other arbitrary Ethereum address. Ecosystem tools such as MetaMask or MyCrypto provide easy interfaces for address and private key creation. Staking addresses must be funded with enough $DPOS to provide at least the minimum staking amount, and a small amount of xDai to cover transaction fees.

# Staking Window

The period of time when stake may be placed on or withdrawn from a candidate or validator pool. The staking window begins shortly after a staking epoch starts, and ends during the final 6 hours of a staking epoch. During the disallow period (when the window is closed), stake may not be withdrawn or placed, preventing manipulation of the incoming validator set at the end of an epoch.

# Stakes Ratio

The Stakes Ratio shows the amount of stake deposited in a validator’s pool relative to the total stake committed to all validator pools. For example, if the total staked amount for all validator pools is 30000, and the staked amount in a specified validator’s pool is 5000, the Stakes Ratio for this pool is 16.67%. A higher stakes ratio corresponds to a greater likelihood of selection to the next validator set.

# Technical Requirements

In order to run a node, certain technical requirements should be met. More details are available here: <link to xDai DPOS validator requirements/node setup post when created>

Minimal system requirements:

* OS: Ubuntu Linux 16.04 LTS with root or sudo-user access over ssh
* CPU: minimum 2 cores
* RAM: minimum 4GB
* Disk: SSD
* Open network ports: SSH port (default 22 TCP), 30303 UDP. For security purposes, close other ports

Running 2 nodes simultaneously:

In addition, we recommend that each validator run two separate nodes simultaneously with different internet connections. This mitigates risk in the event a node goes down during the final reveal phase of a staking epoch. If this occurs, and there is no redundancy, the node is considered malicious and banned from the protocol.

To setup, the first node must have the ​engine_signer​ option in a configuration toml file, the second node should not have that option but should have the ​watchguard​ script which​ detects if the first node goes offline and sets the ​engine_signer​ option for the second node (see [https://github.com/poanetwork/posdao-test-setup/issues/39](https://github.com/poanetwork/posdao-test-setup/issues/39 "https://github.com/poanetwork/posdao-test-setup/issues/39")[​](https://github.com/poanetwork/posdao-test-setup/issues/39%E2%80%8B)).

# Validator

A validator is responsible for running a node that verifies transactions and finalizes blocks on the xDai chain. Validators are entities in the ecosystem that have the technical acumen and desire to participate in the consensus process, and can provide the minimum amount of stake into their pool to participate. The initial group of validators for the first staking epoch is hard coded in the protocol. During the first staking epoch, additional entities may declare themselves as candidates and vie for additional validator slots (see becoming a candidate for more information on this process).

A validator serves the chain for one-week staking epochs as a member of the validator set. During this time, they participate in the consensus process (including transaction verification, committing/revealing random numbers, and detecting/reporting malicious behavior) and take turns proposing and sealing blocks. They receive block rewards as well as transaction and bridge fees in exchange for hosting a node, securing the chain and providing consensus on all transactions. Rewards are distributed according to the distribution rules of the protocol.

Validators may increase their stake amounts at any time by selecting their own pool in the list of pools and adding stake to that pool. This pending stake does not influence current rewards, but is used during the validator selection process for the next staking epoch.

Validators can also remove their pool from selection consideration to the next epoch with the Remove My Pool functionality.

# Validator Pool

The validator pool contains the total amount of $DPOS stake placed on a validator (including active and pending stake). The total amount of active stake is snapshot at the beginning of a staking epoch and used for reward distribution between the validator and its delegators at the end of the epoch. Additional pending stake may be placed on the validator pool during a staking epoch. This pending stake does not accumulate any rewards, but does influence the chances of the pool becoming a validator for the next staking epoch.

# Validator Set

The Validator set is the current group of validators participating in consensus. The maximum number of validators in a set is 19, and a new validator set is chosen for each staking epoch. Members are selected based on the total amount of stake in their pool relative to the total deposited stake (stake ratio), along with a random number that adds variation to the process. A higher stake ratio results in a higher likelihood of selection, but it does not guarantee selection, as every active candidate has a chance to be selected to the next set.

If a validator in the set is removed for malicious behavior, a new validator set (containing the current set minus the malicious validator) is queued and installed into the protocol. This modified set completes the current staking epoch, and rewards are distributed equally among the modified set.

# Withdrawal Rules

Withdrawals are allowed during the open staking window.

* Any amount of stake including the entire stake amount (minus any stake currently ordered for withdrawal and not yet claimed) can be withdrawn from an active candidate during the staking window.
* Only stake placed in the current staking epoch may be withdrawn from a validator’s pool. An order for withdrawal can be placed on a validator’s pool; the ordered amount can be claimed during the next staking epochs.
* If an order for withdrawal has been placed, the amount can be changed during a staking epoch. To add an additional amount to withdraw, simply enter the additional amount. To withdraw a lower amount, enter a negative number to reduce the ordered amount. A transaction is created for each adjustment.
* Stake may be withdrawn during the staking window from an inactive validator, as long as that validator is not banned. If banned, the banned until date will show the date when stake may be withdrawn from the pool.

Ordered withdrawals can be claimed once the current staking epoch is complete (within the staking window of any following staking epochs).

# xDai Stable Chain

The xDai stable Chain is a new network created by POA Network that uses XDai, a representation of Dai, as its native currency. All transactions are performed using xDai, and all gas costs are paid using xDai.

The xDai stable chain provides 5 second blocktimes and extremely low, stable gas fees. This predictability allows users to plan for exact transaction costs, and applications can leverage micro-transactions. xDai is primarily used as a peer-to-peer payment network, where individuals and businesses can relay assets quickly, cheaply and with low volatility.

The xDai Stable chain utilizes the Ethereum 1.0 EVM, meaning any smart contract deployed to the mainnet can also be deployed to the xDai stable chain.

More information is available here: [xDai Chain Frequently Asked Questions](https://forum.poa.network/t/xdai-chain-frequently-asked-questions/1780)

# xDai Coin

The xDai native coin is the transactional token used on the xDai stable chain. xDai is created using bridge technology, and is a 1-to-1 representation of the ERC20 DAI token on the Ethereum mainnet. To mint xDai, a user can lock an amount of DAI into the bridge smart contract using the Bridge UI . Once locked, the corresponding amount of xDai is minted into the users wallet. xDai can then be viewed and sent to other users or vendors by connecting to the xDai RPC in a web3 compatible wallet. To convert xDai back to DAI, the same Bridge UI is used, the selected amount of xDai is burned, and the corresponding amount of DAI is unlocked in the contract.

![](/uploads/xDai Coin.png)