---
layout: post
title: Puul Protocol
subtitle: Puul Protocol Details
gh-repo: PuulFinance/puulfinance.github.io
gh-badge: [follow]
tags: [puul,protocol,defi]
comments: false
---

![Fees](/assets/img/fees.png)

The Puul protocol can perhaps be described as a reward distribution mechanism, which uses concepts from tokens, vaults, and farming to generalize and simplify
many commonly used protocols.

Puul has characteristics of normal ERC20 tokens, vaults, and farms, but goes much further in simplicity and flexibility.

Perhaps the main contribution of the Puul protocol is that it introduces the abstract concept of tokenizing any asset in a pool that generates rewards. 
The rewards are returned based on the proportion of the pool tokens owned. It doesn't matter how the rewards are generated or how many rewards there
are - Puul will track the correct values in all cases.

#### Protocol Safety

Puul uses some now familiar concepts from farming and vaults, but generalizes them to allow much more flexible systems to be constructed. These systems are
much safer than current systems due to the following reasons:

1. Abstraction to Simplify
2. Encapsulation 
2. Separation of Concerns

##### Abstraction

Puul has abstracted key farming and vault concepts to simplify many use cases. Due to the abstractions, very flexible and robust systems can easily be 
construted with just a few operations.

##### Encapsulation

All Puul operations are encapsulated. One operation does one thing in the right place and at the right time.

##### Separation of Concerns

All protocol operations are separated such that each does it's own specific task. This leaves little or no room for exploits. A failure of one 
operation will be isolated and most likely recoverable.

#### Example

A good example of using the Puul protocol is our fee system. Puul collects withdrawal and reward fees from pools. Distributing those fees is problematic
in most other protocols. There is usually some ad hoc, inflexible distribution mechanism that is hard or impossible to modify and change. 

Puul makes it simple to create a very flexible fee distribution system. Here is how we did it:

1. Rewards fees go the a FarmEndpoint. A FarmEndpoint can be attached to any pool. Anything flowing into the FarmEndpoint is harvested 
as rewards for the pool tokens holders the endpoint is attached to.
2. In the same way, withdrawal fees go to another FarmEndpoint.
3. The reward FarmEndpoint is attached to a new token called PUULREW.
4. The withdrawal FarmEndpoint is attached to new token called PUULWTH.
5. To distribute the fees, we now only have to distribute PUULREW and PUULWTH tokens.

Some of those fees go to the developer fund, and some is meant for the Puul Staking Pool. How do we get them in the Puul Staking Pool as rewards?
By having another FarmEndpoint own the PUULREW and PUULWTH tokens!

That FarmEndpoint is attached to the Puul Staking Pool (PUULSTK). The PUULREW and PUULWTH rewards (the fees) are claimed into this 
FarmEndpoint. They are then harvested as rewards into PUULSTK. Owners of PUULSTK can claim these rewards.

This process can go on ad infinitum to create elagant reward systems safely and easily.

#### Puul is Transaction Efficient

The harvesting and claiming abstractions are very transaction efficient. These transactions are done at the global protocol level, and aren't dependent on
user interactions. So they scale endlessly. Usually, you'll be performing these operations at most a few times a day.

#### Puul Performs Operations at the Right Time and Place

Perhaps the main cause of defi exploits is not so much flaws in the operations (although those exist too), but rather design decisions 
that try to do too many things, or do things at the wrong time or in the wrong place. The recent Pickle exploit is a good example of
this. There were myriad issues with the flawed function that allowed the exploit, but it can be summed up in one work - encapsulation.
The function in question was using data and operations outside of their respective contexts. If all of the operations were performed 
in the right place (inside the jars), the exploit could not have happened. In this case there were many data validation errors also, but
the main error was just the design itself.

#### Access Control

The Puul protocol has specific roles for performing each operation. Most of those roles are controlled by a timelock contract and are
controlled by governance.

The only role with immediate access to the protocol is the Harvester.

#### The Harvester

There is one special priviliged user in the Puul protocol called the Harvester. The Harvester performs all the operations mentioned above,
plus a few others. None of the operations the Harvester performs can cause a loss of funds. They mostly involve claiming and harvesting rewards,
which convert and move tokens in a very controlled way. 

The Harvester can also change some settings, like limits on pools. None of the settings the Harvester can changes can cause you to lose funds or prevent
you from withdrawing from the protocol.

#### Entering and Exiting the Puul Protocol

Puul also greatly simplifies getting assets into and out of pools. Puul let's you use common tokens, like the stable coins USDT, USDC, and DAI. Puul will convert
to the required staking token and stake the token to start collecting the rewards. The number of transactions needed to start farming go from
3-4 to one.

It's the same when exiting the protocol. With one transaction you can withdraw and liquidate you stake back to USDT, USDC, DAI, or WETH.

Practically speaking, this makes farming so easy and painless that it opens up oppportunities that wouldn't exist for most investors.


