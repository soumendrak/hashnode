## Understanding Layer 2 of Blockchain

## Background

- As we know it today, the Internet was a cumulation of decades of research in computing technologies. To finally end up with a platform that connects billions of people and machines worldwide, we had to solve problems we didn’t even know existed. Eventually, with a mechanism that included 7 different Layers called the [OSI Model](https://en.wikipedia.org/wiki/OSI_model), the [Internet](https://en.wikipedia.org/wiki/Internet) was born.
- Just like the internet, Blockchain, too, is a platform that had to be constructed in Layers. The layer-based model allowed developers and infrastructure architects to focus on their agendas and nothing else.

![source: [https://en.wikipedia.org/wiki/OSI_model](https://en.wikipedia.org/wiki/OSI_model)](https://cdn.hashnode.com/res/hashnode/image/upload/v1641535662782/uVjzX_PcZ.png)


source: [https://en.wikipedia.org/wiki/OSI_model](https://en.wikipedia.org/wiki/OSI_model)

- Put into perspective, for an application builder, it is more than enough to focus on the last Layer, the Application Layer. While for a platform developer, knowing the initial Layers is of utmost importance as they form the base for applications to be built on. As we move up, Layer to Layer, the complexity increase while the generality goes down.

## Introduction

- If you follow DeFi closely, you’ve probably come across the term “Layer 2”. Crypto natives often talk about blockchains in terms of “Layer 0”, “Layer 1”  and “Layer 2”, but to understand what they mean, it’s worth explaining from the base point.
- Layer 0 can be considered a bridge between the Internet, the physical world, and the blockchain. Remember that blockchain technology is not all software. It involves
physical network infrastructure (like the mining component of PoW platforms, data storage, etc.) that allow a complex technology like Blockchain function. Layer 0 is the basement that is never seen but is as important as the building itself.
- Blockchains like Bitcoin and Ethereum is often described as “Layer 1” chains because they settle every transaction on their network.
- Layer 2, meanwhile, is the framework that gets built on top of the blockchain. Layer 2 solutions have an important role to play in improving scaling.
- We’ve spent a lot of time researching them in regards to our own offering, and we’re closely linked with Layer 2 projects like Polygon (formerly known as *Matic*). For our latest Understanding DeFi guide, we wanted to detail how they work for the community, along with some examples of the solutions that are being developed today.

## **What is Layer 2?**

- Ethereum has created a financial system unlike anything the world has seen before, but it suffers from some well-documented problems.
- Ethereum in its current iteration processes around 15 transactions per second. This has caused a number of issues: the network often gets congested, sometimes pushing gas fees to extreme highs.
- Blockchains should be scalable, secure and decentralised. While there are ways of improving transaction speeds by using more powerful nodes, this approach [compromises on decentralisation](https://twitter.com/SBF_Alameda/status/1343436567847739392).
- It’s hoped that Ethereum 2.0 will improve scalability, but it will still be some time before the upgrade is complete. And with Etheruem usage peaking at around 1 million transactions daily, it needs other solutions today.
- That’s what Layer 2 is for. Layer 2 is what gets built on top of the base chain in order to improve scalability.
- Like Bitcoin, Ethereum can be thought of as a Layer 1 protocol. It’s the settlement layer for all transactions on the network.
- Layer 2 solutions offer a way of increasing transaction speeds and scaling while benefiting from the security of the main chain. In some cases, they can process thousands of transactions per second, which will be needed if Ethereum is to achieve wider adoption.

## **Examples of Layer 2 solutions**

- Ethereum’s Layer 2 solutions fall under several categories, and each one differs in its approach to making the network more scalable.

### **Channels**

- Channels offer users a way of making multiple transactions off-chain while submitting only two transactions to the settlement layer, i.e. Ethereum. This allows for high throughput at a low cost, however, there are limitations. Participants need to be known in advance, and they’re also required to deposit funds into a multisig contract. That means the network needs to be regularly monitored to ensure that the funds are safe. It also takes time to set up channels between users, so doesn’t allow for much open participation.
- Channels come in two forms: state channels and payment channels.
- Examples of channels include Connext and Raiden.

### **Plasma**

- Plasma solutions use [Merkle tree](https://en.wikipedia.org/wiki/Merkle_tree) to create an additional chain to the main blockchain. This facilitates fast transactions at a lower cost, as the blocks aren’t settled on the main chain, and there’s no need to store data on the ledger.

- However, there are limits to what you can do using Plasma. The framework only supports certain transactions, so more complex DeFi activity, for example, isn’t possible. Withdrawals are subject to potential challenges and longer waiting times, and it also requires someone to monitor the network to check funds are safe, as well as operators to store data.
- Examples of Plasma solutions include OMG and Polygon (the Polygon SDK is also set to support ZK rollups, optimistic rollups and standalone chains).

### **Sidechains**

- Sidechains run separately from the main blockchain and operate independently using their own consensus algorithm. They connect to Ethereum via a two-way bridge. They’re compatible with the Ethereum Virtual Machine, but they’re also limited: they’re less decentralised than the main network, the consensus algorithm isn’t settled by Layer 1, and sidechain validators could coordinate to act maliciously.
- Examples of sidechains include xDAI and Skale.

### **Rollups**

- Rollups work by executing transactions on Layer 2, while submitting data to the base chain. This means that they benefit from the security of Ethereum, but can perform transactions outside of Layer 1.

- There are two types of rollups:
    - ZK (zero-knowledge) rollups, which bundle many transfers into one transaction, and optimistic rollups, which operate in parallel to Ethereum.
        - ZK rollups group transactions together by creating what’s known as a SNARK — a succinct non-interactive argument of knowledge. This is a cryptographic proof that gets submitted to the base layer, so only one transaction is sent to Ethereum. ZK rollups allow for fast transactions, but the scope of these transactions is limited.
        - Examples of ZK rollup solutions include Loopring and StarkWare.
    - Optimistic rollups, meanwhile, sit alongside the base chain, with transactions sent to Ethereum as calldata. Optimistic rollups provide composability, a fundamental requirement of DeFi, though they are subject to longer wait times and potential attacks.
        - Optimistic rollups are currently being developed by Optimism.

### **Validium**

- Validium is not unlike ZK rollup technology in that it uses zero-knowledge proofs, but the data is stored off-chain. That means up to 10,000 transactions per second with no withdrawal delays and a lower risk of attacks, but it’s not possible to run every kind of smart contract, generating ZK proofs requires high computational power, and finality times can be slower.
- Examples of Validium solutions include StarkWare and DeversiFi.

## **Final thoughts**

- In summary, there are currently several Layer 2 solutions that aim to resolve Ethereum’s scaling issues. There are also some hybrid solutions that seek to improve the network’s scalability by combining the technologies.
- If Ethereum achieves its full potential, becoming a global trust layer, it’s likely that these solutions and more will be required to scale the network in combination with Ethereum 2.0.
- In the future, the Ethereum ecosystem could see significant change, as new projects assess the benefits and drawbacks of running on Layer 2.
- Now that you understand Ethereum’s various Layer 2 solutions, are there any you’ve used before? If not, why not try a transaction using Plasma or ZK roll-ups? Let us know how you get on.
- There is Layer 3 as well, built on top of layer 2 for a specific narrow use case.

Thank you for reading to the end.

## References:

- [Understanding DeFi: Layer 2 explained](https://medium.com/monolith/understanding-defi-layer-2-explained-6981ef6c8990#:~:text=Layer%202%20is%20what%20gets%20built%20on%20top,benefiting%20from%20the%20security%20of%20the%20main%20chain)
- [Beginner’s guide to Blockchain layers](https://cryptoadventure.com/beginners-guide-to-blockchain-layers/)
