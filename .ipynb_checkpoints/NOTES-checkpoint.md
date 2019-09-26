**Uniswap notes:**

Uniswap mechanism for liquidity provider / delegators brokerage:
* Uniswap liquidity pools are autonomous and use the Constant Product Market Maker (x * y = k)
* A small liquidity provider fee (0.3%) is taken out of each trade and added to the reserves
* Formal verification: https://github.com/runtimeverification/verified-smart-contracts/blob/uniswap/uniswap/x-y-k.pdf
* The invariant is that the ratio of e:t:l is preserved and k = e * t increases (e is ether, t is exchange tokens, and l is total liquidity / supply of uni tokens)
* By supplying and burning liquidity (uni tokens), the investor can exchange for their share of ether and tokens

Uni-token === IXO staking token
If you stake you're delegating, and delegators receive a proportion of the networks fees, block rewards/inflation, service fees from oracles

**Terminology:**

* c_ - IXO-Cosmos equivalent of Ethereum tokens
* native - native to IXO-Cosmos network
* cIXOS - staking tokens 
* cIXO - utility tokens

**Actor flow:**

1. Participant buys into market maker with Dai, and is given Ethereum based IXO tokens.
2. Participant stakes IXO into the brokerage mechanism in exchange for IXOS. The IXO stake is backed by a proportion of the DAI collateral pool.
3. The IXO and IXOS pools are mirrored on the IXO-Cosmos network, and backed by DAI - post IBC these assets can be made native to the IXO-Cosmos network.
4. cIXO become utility tokens that can be spent in IXO-Cosmos network, and minted through block rewards to be rewarded to actors in the system. The utility comes from the asset backing of the cIXO tokens in the brokerage.

**Working example:**

1. Participant purchases 100 IXO tokens @ 0.1 DAI per IXO for a total of 10 DAI.
2. Participant provides liquidity in brokerage contract by depositing 50 IXO, retaining 50 IXO for the time being. The asset backing is provided by the bonding curve Dai collateral pool.
3. Participant is rewarded with 50 IXOS tokens to represent the proportion of the liquidity provided.
4. These IXOS tokens are mirrored and can be used within the IXO-Cosmos network as equivalent cIXOS tokens, these are low velocity and are essentially staked for IXO-Cosmos incentive rewards.
5. Participants within the IXO-Cosmos network, who are incentivized/rewarded with cIXO tokens for supporting the network roles, may atomic swap/mirror their cIXO tokens for IXO tokens and in effect DAI via the bonding curve.

**Observations:**

* Based on last two actions - what is the best way to couple the cIXO token value to the DAI reserve to maintain the cross blockchain peg?
* Objective - make the cIXO utility token stable.
* cIXOS staked on IXO-Cosmos side for various incentive rewards.

**To reduce invariance:**
* Introduce arbitrage rebalancing
* Introduce algorithmic binding
* Introduce capacitor like smoothing of binding - treat the pool like a capacitor and the variance as AC electricity, determine the RC ratio necessary to filter out noise. The smoothing capacitor acts smooths the ripple current, to an appropriate level of stability. It does this by storing charge (perhaps tax), and discharging when necessary.
