---
layout: post
title: Introducing Puul
subtitle: Defi Made Easy
gh-repo: PuulFinance/puulfinance.github.io
gh-badge: [follow]
tags: [puul,defi]
comments: false
---

Welcome to Puul. Puul is the most versatile defi protocol available today.

With Puul, you can farm existing farms and vaults in a much simpler way, and start collecting rewards immediately.

Puul also makes it easy to create new vaults, farms, and other defi investment opportunites.

Puul is the only defi platform with the ability to farm **any** farm or vault. Many defi platforms have promised this, but Puul is the only one to deliver.

## Puul Generalizes Defi

Puul generalizes defi into simple concepts.

### Pools with Rewards

Perhaps the key innovation in Puul is the concept of tokenizing any asset in a pool that provides reward tokens.

Puul calculates the correct proportional rewards, no matter how those rewards are generated or how many rewards there are.

Suprisingly, this concept generalizes many defi protocols, such as farms and vaults.

You can claim the rewards at any time without unstaking or withdrawing, and the rewards can be returned in any coin, like USDC, USDT, DAI, WETH, or WBTC.

### Everything is Tokenized

Most farms require that you stake some LP tokens, but do not send an ERC20 token back to you that represents your investment. Your LP tokens disappear into the staking contract and are stuck there until withdrawn. This is a grave oversight.

With Puul, you get a new ERC20 token that you can transfer or sell just like any other token.

This means that your stake now has a measureable value.

Instead of withdrawing the tokens and liquidating them, you can simply sell or tranfer them.

This is a huge advance for defi.

### Everything is Farmable

Pools in the Puul protocol collect rewards from farms. Puul adds the concept of a FarmEndpoint to the protocol. A FarmEndpoint
can be attached to any pool. FarmEndpoints generalize the concept of farming, but also 
provide other benefits. 

A FarmEndpoint can produce it's own rewards (like a typical farm), but it can also
collect rewards from one or more other pools. The way it does this is through token ownership - the FarmEndpoint
owns tokens in another pool and can claim those rewards into itself. Those rewards then flow to the token
holders of the pool that is attached to the FarmEndpoint.

This concept has powerful implications and makes it very easy to set up endlessly flexible reward and token
distribution networks simply through normal ERC20 token ownership.

### How We Use Puul

Here is a good example of how we use Puul to distribute our fees.

#### Puul Fees

Puul collects two types of fees - reward and withdrawal fees. We could have just used a typical contract which extracts the fees and directs them to an address. But then any change to the fee distribution would be hard coded and very rigid.

So here is what we did instead (and what you can do).

We direct the reward fees to a FarmEndpoint and the withdrawal fees to another FarmEndpoint. Each FarmEndpoint is attached to a pool, which farms the rewards (the fees in this case) into the pool.

But remember, pools are just ERC20 tokens. So to distribute the fees, we only have to distribute the pool tokens. This gives us endless flexibility in distributing the fees for the Puul platform - we merely distribute ERC20 pool tokens.

The Puul network now has two other tokens, one for the reward fees (PUULREW) and another for the withdrawal fees (PUULWTH).

#### Chaining Pools and Rewards

But it doesn't end there. We want some of those fees to go to the Puul Staking Pool (PUULSTK). How do we do this? In the same way!

We create another FarmEndpoint that owns the PUULREW and PUULWTH tokens. This FarmEndpoint is attached to PUULSTK. The rewards from PUULREW and PUULWTH (the fees) are owned by the FarmEndpoint attached to PUULSTK. 

When those fee tokens are claimed, they wind up in the PUULSTK FarmEndpoint. When that FarmEndpoint is harvested into PUULSTK, the proportional rewards from the fees go to the PUULSTK token holders.

#### Pool, Tokenize, and Claim Recursively

Any pool can harvest rewards from a FarmEndpoint. Since a pool is an ERC20 token, distributing the farmed rewards is the same as distributing the pool tokens.

But pool tokens themselves can be owned by another FarmEndpoint and harvested into another completely different pool.

This can go on ad infinitum.

### Puul is Gas and Transaction Efficient

Puul is very gas efficient, but is also **transaction efficient**. By this we mean that the number of transactions necessary to maintain pools and farms is greatly reduced.

The harvesting transaction can be done at any time, and only needs to be done once, no matter how many users are using a pool.

Since pool tokens can be transferred like any other token, you don't have to liquidate your farming stake to exit a farm, you just sell the tokens. This saves
an enormous number of transactions that are required to enter and exit farms.

### Simple Token Conversion
We go one step further. When you claim rewards or withdraw, you can optionally convert the rewards or withdrawal into another token with **one** transaction.

It's the same when you deposit - from a single token and one transaction you can start farming.

### Real World Example
Imagine entering and exiting a typical farm. Let's say it's a farm that requires staking of a Uniswap LP Token, like PICKLE/WETH. Here is what you would
have to do to start farming:

1. Buy some PICKLE.
2. Buy some WETH.
3. Create the LP Token.
4. Deposit the LP Token.

With Puul, this is reduce to **one** transaction. The same operations you see above are encapsulated into one transaction with Puul. 

To exit the farm, you reverse the process above. Again, with Puul this is reduced to one transaction.

But remember, Puul returns you an ERC20 token representing your stake, so in most cases you don't have to withdraw and liquidate, you can simply sell your tokens.

### Puul Reduces Complexity

The Puul protocol consists of a few simple operations, with no dependencies between the operations.

Complicated processes can be designed with much less chance of an exploit.

Due to the clean separation of concerns, any problems encountered will most likely be recoverable.

Puul has also reduced the complexity of distributing fees and rewards from even thousands of farms and vaults into a few familiar concepts.

### What's Coming

We have some pools that are available now. Go the the [Puul Finanace App](https://puul.finance) and check them out. 

And please, keep checking back. You will see new pools appearing almost daily.

