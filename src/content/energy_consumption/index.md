---
title: Ethereum Energy Consumption
description: The basic information you need to understand Ethereum's energy consumption.
lang: en
sidebar: true
---

Ethereum's current energy expenditure is too high and unsustainable. Resolving energy expenditure concerns without sacrificing security and decentralization has been a significant technical challenge for Ethereum's development. Let's explore why building Ethereum has had a high environmental impact and how upcoming network upgrades will dramatically change this.

## Energy secures the network {energy-secures-the-network}

Transactions on the Ethereum blockchain are validated by [miners](/developers/docs/consensus-mechanisms/pow/mining). Miners bundle together transactions into ordered blocks and add them to the Ethereum blockchain. The new blocks get broadcast to all the other node operators who run the transactions independently and verify that they are valid. Any dishonesty shows up as an inconsistency between different nodes. Honest blocks are added to the blockchain and become an immutable part of history.

Reliance on miner honesty only works if there is a cost associated with mining and unpredictability about which specific node submits the next block. These conditions are met by imposing proof-of-work (PoW). To be eligible to submit a block of transactions, a miner must solve an arbitrary computational puzzle faster than any other miner. Solving this puzzle creates competition between miners and costs in the form of energy expenditure. To successfully defraud the blockchain, a dishonest miner would have to consistently win the proof-of-work race, which is very unlikely and prohibitively expensive.

Ethereum has used proof-of-work since genesis. Migrating off of proof-of-work has always been a fundamental goal of Ethereum. Still, it has been philosophically and technologically challenging because the viable alternatives all required to compromise Ethereum's core principles.

## Proof-of-work energy expenditure {#proof-of-work}

Proof-of-work is a robust way to secure against dishonest changes to the blockchain, but it is problematic for several reasons. Since the right to mine a block requires solving a computational puzzle, miners can increase their odds of success by investing in more powerful hardware. These incentives cause an arms race with miners acquiring increasingly power-hungry mining equipment. Ethereum's proof-of-work protocol currently consumes as much energy as a medium-sized country.

## Proof-of-stake {#proof-of-stake}

A greener future for Ethereum is already being built in the form of a **proof-of-stake (PoS)** chain. Under proof-of-stake, arbitrary puzzle-solving is unnecessary. Removing puzzle-solving drastically reduces the energy expenditure required to secure the network. Miners get replaced by validators who perform the same function except that instead of expending their assets up-front in the form of computational work, they stake ETH as collateral against dishonest behavior. If the validator's node is non-responsive or a fraudulent block gets submitted to the chain, the staked assets can be "slashed", strongly incentivizing honesty and securing the network.

Similarly to proof-of-work, to maintain a fraudulent blockchain, a validator would require 51% of the total ETH staked in the network. However, unlike proof-of-work, consensus is not based on the longest chain, but a mechanism known as ["Casper"](https://arxiv.org/abs/1710.09437). Migrating from proof-of-work to proof-of-stake eliminates the need to expend energy on arbitrary computations.

## The merge {#the-merge}

There is a functional proof-of-stake chain called the [Beacon Chain](/eth2/beacon-chain/) that has been running since December 2020 that is demonstrating the viability of the proof-of-stake protocol. The merge refers to the point in time when Ethereum leaves proof-of-work behind and fully adopts proof-of-stake. The merge is expected to happen ~Q2 2022. [More on the merge](/eth2/merge/).

## Proof-of-stake energy expenditure {#proof-of-stake-energy}

As well as building confidence in the proof-of-stake mechanism, the Beacon Chain also enables estimates of Ethereum's post-merge energy usage. A recent [blog post on the ethereum.org blog](https://blog.ethereum.org/2021/05/18/country-power-no-more/) suggested that the merge to proof-of-stake could result in a 99.95% reduction in total energy use, with proof-of-stake being ~2000x more efficient than proof-of-work. The energy expenditure of Ethereum will be roughly equal to the cost of running a home computer for each node on the network.

![image](energy_use_per_transaction.png)

We can use this data to compare Ethereum to a global service like Visa. 100,000 Visa transactions uses 149kWh of energy<sup>[^2]</sup>. Assuming sharding has been implemented, Ethereum's current transaction rate (15 transactions per second) will be increased by at least 64x (the number of shards), not accounting for additional optimization from rollups. A realistic estimate for post-merge, sharded Ethereum with rollups is [25000 - 100000](https://twitter.com/VitalikButerin/status/1312905884549300224?s=20) transactions per second. We can use this information to estimate a maximum and minimum energy expenditure per 100,000 transactions.

- 25000 transactions per second.
- `100,000 / 25000 = 4` seconds to process 100,000 transactions.

We can also estimate Ethereum's energy expenditure per second, making a conservative estimate that 10,000 active validators are securing the network (there are over 180,000 validators on the Beacon Chain at the moment, but many validators can operate on a single node. Currently, there are 3000-4000 individual nodes, so 10,000 is a conservative estimate for post-merge):

`1.44kWh daily usage * 10,000 network nodes = 14,400kWh` per day.
There are 86,400 seconds in a day, so `14,400 / 86,400 = 0.1667 kWh` per second.

If we multiply that by the amount of time it takes to process 100,000 transaction: `0.1667 * 4 = 0.667 kWh`.

This is ~0.4% of the energy used by Visa for the same number of transactions, or a reduction in energy expenditure by a factor of ~225.

Repeating the calculation with the maximum transactions-per-second yields 0.1667 kWh per second which is about 0.1% of the energy expenditure of Visa, or a reduction of ~894x.

_We’ve provided the basic comparison to Visa to baseline your understanding of post-merge Ethereum energy consumption against a familiar name. However, in practice, it’s not really correct to compare based on number of transactions. Ethereum’s energy output is time-based. If Ethereum did more or less transactions from one minute to the next, the energy output would stay the same._

_It’s also important to remember that Ethereum does more than just financial transactions, it’s a platform for applications, so a fairer comparison might be to many companies/industries including Visa, AWS and more!_

## A greener Ethereum {#green-ethereum}

While Ethereum's energy consumption has historically been substantial, there has been a major investment of developer time and intellect into transitioning from energy-hungry to energy-efficient block validation. To quote [Bankless](http://podcast.banklesshq.com/), the best way to conserve the energy consumed by proof-of-work is simply to "turn it off", which is the approach Ethereum has committed to take.

<InfoBanner emoji=":evergreen_tree:">
  If you think these stats are incorrect or can be made more accurate, please raise an issue or PR. These are estimates by the ethereum.org team made using publicly accessible information and the current Ethereum roadmap. This doesn't represent an official promise from the Ethereum Foundation. 
</InfoBanner>

## Further reading {#further-reading}

- [A country's worth of power, no more](https://blog.ethereum.org/2021/05/18/country-power-no-more/) – _Carl Beekhuizen, May 18 2021_
- [Ethereum Energy Consumption Index](https://digiconomist.net/ethereum-energy-consumption/) – _Digiconomist_

## Related Topics {#related-topics}

- [Ethereum's vision](/eth2/vision/)
- [The Beacon Chain](/eth2/beacon-chain)
- [The merge](/eth2/merge/)
- [Sharding](/eth2/beacon-chain/)