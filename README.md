# Bitcoin Curriculum Notes

## Study Group Answers

1. Why did Satoshi put so much stress on the irreversibility of transactions? (Bitcoin Whitepaper)
    * The system of electronic payments made with credit and with the possibility of transaction reversal introduces the need for more trust and creates a system where the trusted third parties that facilitate payment (banks) have to mediate disputes, increasing the cost to transact. Some fraud will always occur in such a system, further increasing costs. Satoshi wanted to build an online system that is the digital equivalent of transacting with cash, where money can't be taken back once it's spent. Thereby eliminating the need for trusted third parties to mediate disputes and the risk of being defrauded.
1. What proposed role do SPV nodes play in the bitcoin ecosystem? (Bitcoin Whitepaper)
    * SPV nodes have the ability to verify that a payment without needing to bear the cost of running a full node. An SPV node and maintain a copy of the blockchain's block headers, and (assuming those headers are correct) verify that a payment was included in a given block use the Merkle branch containing the transaction.
1. How have show-stopping bugs or disruptions to the network been handled in the past? (Incomplete History of Bitcoin Development)
    * At one time, the community was small enough that Satoshi and early maintainers were able to simply make the code changes, entice people to upgrade, and cajole miners to do any reorganizing necessary to remedy major bugs such as the one where a transaction was introduced in a block that caused an overflow.
1. In your opinion, what did Satoshi "invent" that was truly innovative? (Bitcoin's Academic Pedigree)
1. What is a Sybil Attack, and how has it been solved in the past? (Bitcoin's Academic Pedigree)
1. What is the "fair exchange" problem, and how does it apply to the blockchain? (Bitcoin's Academic Pedigree)
1. Why do the authors of Bitcoin's Academic Pedigree believe that bitcoin was ignored by academia for a long time? What reputation/relationship does bitcoin have with academia today? (Bitcoin's Academic Pedigree)
1. How do you judge the merits or value of a good project/experiment? (If I'd Known What We Were Starting)
1. What will happen when the mining reward runs out? (Bitcoin's Security Model: A Deep Dive)
1. Define the differences between a full node, pruned node, and an SPV node? (Security Models)
1. What are the incentives to run a full-node? If I do run a full-node, why accept incoming connections given that they come at a cost? What might those costs be? (Security Models)
1. What is the difference between the block propagation network and the transaction relay network? How does participating in one or the other impact your definition of a full node? (Security Models)
1. Do you believe that bitcoin needs to be competitive with visa/mastercard to succeed? (A trip to the moon)
1. How do you think the bitcoin community might react to a centralized payment processor that does as many transactions per second as visa/mastercard? (A trip to the moon)