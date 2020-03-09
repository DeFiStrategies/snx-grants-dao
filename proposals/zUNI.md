## Title of proposal: zUNI - An ERC20 token that lets you accrue additional sETH LP tokens from automatic SNX rewards rebalancing.

## Description: 
We at [DeFiZap](https://defizap.com) are big fans of Synthetix project and are always looking for ways to improve the experience for this community. 
For example, our sETH Unipool Zap helps users add liquidity to the sETH<>ETH Pool on Uniswap in one-transaction, using just one asset (ETH or sETH or other ERC20s). Inputs are split into appropriate proportions to enter the pool with to mint sETH LP tokens which represent your claim on liquidity provided + accrued exchange fees. Over 8,000 ETH has been added to the sETH pool using this Zap alone since it’s deployment less than 3 months ago.
As soon as the new Unipool contract for SNX rewards was announced, we added a visual interface to help users easily stake their sETH LPs in Unipool contract, but we knew we had to do more. Today we are proud to propose something we already have available for testing - zUnipool tokens or simply zUNI. 

zUNI tokens represent a claim on sETH LP stake in Unipool + accrued SNX incentives from sETH Unipool Staking Reward system, which are auto-rebalanced into additional sETH LPs and re-staked in Unipool contract.

zUNI users can convert their sETH LPs into zUNI tokens at any point, by calling stakeMyShare. 

Likewise, they can redeem their zUNI for their original sETH LPs + additional sETH LPs (accrued from rebalancing SNX rewards into additional sETH LPs), by calling getMyStakeOut. 


## Motivation: 
Up until recent deployment of Unipool contract, SNX rewards for sETH LPs on Uniswap were essentially distributed manually.
- Before: Take snapshots of LP addresses and airdrop SNX rewards proportionally.
- Now: Stake LP tokens in Unipool which proportionally accrue SNX rewards every second, are redeemable anytime to:
    - sETH LP tokens + accrued SNX rewards.
    - JUST SNX rewards.
    - JUST some sETH LP tokens.
*Why zUNI?*
- Once staked in Unipool, sETH LP tokens cannot be moved - zUNI is an ERC20 which can be transferred freely and is always proportionally redeemable for an ever growing amount of sETH LPs.
- Accrued SNX rewards are not being utilized - anytime zUNI is minted or redeemed, accrued SNX rewards for all zUNI holders will rebalance into sETH LPs which are re-staked to accrue SNX rewards at a faster rate.
- Improve sETH<>ETH peg with every SNX rebalance as SNX is used to buy sETH from Uniswap in order to obtain necessary proportions to obtain LPs from adding sETH+ETH liquidity to the pool.

## Additional information: 
Contracts:
- [zUnipool.sol](https://github.com/amateur-dev/Unipool/blob/master/contracts/zUniPool.sol)
- [Unipool.sol](https://github.com/k06a/Unipool/blob/master/contracts/Unipool.sol) {original UniPool}
- Review code, submit PRs with your feedback here: [https://github.com/amateur-dev/Unipool](https://github.com/amateur-dev/Unipool)

Testing on forked mainnet instructions.

Why testing on Forked Mainnet:
The Contract that we have developed and in the process of testing requires to interact with (a) the Unipool contract that is giving out the rewards and (b) Uniswap, to be able to convert the underlying SNX into sETH LP tokens.  We wanted to test these functionalities in “as close to as real mainnet” situations considering the quantum of SNX required for distribution {yes, that can be gamed on a test net} and (most importantly) the deep volume that exists on Uniswap {which is only on the mainnet (creating that on a testnet would be very cumbersome)}.  Hence, our entire testing has been on a forked version of the mainnet.

Instructions:

- Video Tutorial: [https://www.loom.com/share/53ead589fa584db49c228d6c0352b5f6](https://www.loom.com/share/53ead589fa584db49c228d6c0352b5f6)
- https://medium.com/ethereum-grid/forking-ethereum-mainnet-mint-your-own-dai-d8b62a82b3f7
- [WIP] Once Geth is running on port 8545, open a new terminal window
    - Type: “ganache-cli --fork http://localhost:8545 -e 30000”
      - This creates a network that simulates mainnet running on port 8546 with each address starting with 30,000 ETH
- Pending for final push on repo. [In a new terminal window, navigate to the Unipool folder
    - Type : “truffle test”
      - Contracts will be compiled and tests will be run. The status of each test is indicated by a checkmark or cross.]

Front-end:
To help us design and develop a worthy UI/UX, we partnered with one of our fellow MetaCartel members - [RaidGuild](https://raidguild.org/). This page will be launched as soon as the community approves, tests and audits zUNI smart contract.
[View WIP drafts in detailed tutorial post.](https://defitutorials.substack.com/p/zuni-programmable-pooling-incentives)

## Previous work: 
[sETH Unipool Zap.](https://defizap.com/zaps/unipoolseth)

## Estimated hours: 

- 50 hours planning/designing
- 150 hours building

Total: 200 hours

## Price (SNX): 
- ~20,000 SNX of which 6,500 will be used acquire sETH LPs and minting initial zUNI tokens.

## Ethereum Address: 
- 0xf79Cabc4cacA5ECa8eE6A36651A0Ad5A2190F04E
