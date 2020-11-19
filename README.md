# Bitcoin Curriculum Notes

## Study Group Answers

1. Why did Satoshi put so much stress on the irreversibility of transactions? (Bitcoin Whitepaper)
    * The system of electronic payments made with credit and with the possibility of transaction reversal introduces the need for more trust and creates a system where the trusted third parties that facilitate payment (banks) have to mediate disputes, increasing the cost to transact. Some fraud will always occur in such a system, further increasing costs. Satoshi wanted to build an online system that is the digital equivalent of transacting with cash, where money can't be taken back once it's spent. Thereby eliminating the need for trusted third parties to mediate disputes and the risk of being defrauded.
1. What proposed role do SPV nodes play in the bitcoin ecosystem? (Bitcoin Whitepaper)
    * SPV nodes have the ability to verify that a payment without needing to bear the cost of running a full node. An SPV node and maintain a copy of the blockchain's block headers, and (assuming those headers are correct) verify that a payment was included in a given block use the Merkle branch containing the transaction.
1. How have show-stopping bugs or disruptions to the network been handled in the past? (Incomplete History of Bitcoin Development)
    * At one time, the community was small enough that Satoshi and early maintainers were able to simply make the code changes, entice people to upgrade, and cajole miners to do any reorganizing necessary to remedy major bugs such as the one where a transaction was introduced in a block that caused an overflow.
1. In your opinion, what did Satoshi "invent" that was truly innovative? (Bitcoin's Academic Pedigree)
    * Satoshi's key invention was the minting and transferring of money in a non-reversible way by using Proof of Work.
1. What is a Sybil Attack, and how has it been solved in the past? (Bitcoin's Academic Pedigree)
    * A Sybil attack is one where a nefarious actor creates enough fake nodes (IE one node pretending to be many) to take over a network's consensus mechanism. In the past, two possible ways of solving the problem were 1) to have a gatekeeper allowing entry into a network (not ideal as it creates the need for trust and a single point of failure), or 2) to require each node in a network to solve a proof-of-work puzzle, which would be no problem for honest nodes, but difficult for Sybil nodes. This latter strategy creates a scenario where honest nodes end up needing to run as many nodes as they can computationally afford, so that attackers don't gain a moderate advantage by have >1 identities while honest actors only claim 1.
1. What is the "fair exchange" problem, and how does it apply to the blockchain? (Bitcoin's Academic Pedigree)
    * The fair exchange problem is how to ensure that money is transferred if (and only if) an asset is transferred or a service is rendered in return. Smart contracts enable this kind of functionality in Bitcoin without the need for an arbitrator.
1. Why do the authors of Bitcoin's Academic Pedigree believe that bitcoin was ignored by academia for a long time? What reputation/relationship does bitcoin have with academia today? (Bitcoin's Academic Pedigree)
    * The authors believe that academia has a resistance to radical ideas, which Bitcoin was, being that it was not formally peer reviewed and didn't have much of a tie to previous work. The authors assert that academics have spent time in recent years ignoring Bitcoin or arguing why it can't work despite the fact that it already does work (I somewhat disagree with this as we've seen increasing academic mindshare going to improve Bitcoin itself). Today, Bitcoin remains somewhat unconnected from the disciplines that that it's based on. For instance the ongoing Proof of Work academic work today continues without referencing Bitcoin.
1. How do you judge the merits or value of a good project/experiment? (If I'd Known What We Were Starting)
   * If the main goal of a project is to market its coin so that a lot of people buy it, it's not a good project (analogy being to that of a company whose only business plan is market its stock)
   * Where are the principals of the project/business located? Are they named Can you validate that they are who they say the are? What regulatory authorities oversee them?
   * What legal recourse do you have in case of fraud?
   * Is the company running the project incorporated? Do they have the appropriate licenses? Do they have a legal authority to issue stock?
   * Basically, do diligence on these things as you would with a company.
1. What will happen when the mining reward runs out? (Bitcoin's Security Model: A Deep Dive)
   * Blocks will presumably continue to be mined in order to claim Bitcoin transaction fees. Although there's some debate in the community as to whether or not the network will continue to function due to some attacks that may have more incentives in the absence of a block reward.
1. Define the differences between a full node, pruned node, and an SPV node? (Security Models)
   * Full node: Downloads the entire blockchain (headers and blocks), validates and relays transactions in the most-work chain. May validate and relay unconfirmed transactions but doesn't have to.
   * Pruned node: Downloads the entire blockchain, validates all blocks, and discards blocks beyond a certain size limit (defaults to 550mb). Is still a full node in the sense that it can validate and relay transactions in the most-work chain. But is in theory susceptible to large reorgs where the reorg extends far enough back to weird the pruned node is no longer storing the blocks being reorged.
   * SPV node: Doesn't download and validate the entire block chain. Downloads the most-work headers and can query other nodes to determine whether a transaction is included in the blockchain.
1. What are the incentives to run a full-node? If I do run a full-node, why accept incoming connections given that they come at a cost? What might those costs be? (Security Models)
1. What is the difference between the block propagation network and the transaction relay network? How does participating in one or the other impact your definition of a full node? (Security Models)
1. Do you believe that bitcoin needs to be competitive with visa/mastercard to succeed? (A trip to the moon)
1. How do you think the bitcoin community might react to a centralized payment processor that does as many transactions per second as visa/mastercard? (A trip to the moon)