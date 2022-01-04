# DPoS

## Overview
Stabila blockchain is a distributed accounting system. There can be thousands of nodes in a blockchain system, each of which independently stores the same ledger. If new transaction data is to be written into the ledger,  approvals from these nodes are needed. Achieving this goal in an untrusted distributed environment is a complicated systematic quest. The blockchain system operates means typically, each node in the blockchain can always keep the same ledger, provided that most nodes in the system are honest and reliable. To ensure that honest and reliable nodes can jointly supervise the transaction data written into the ledgers, each blockchain system needs to build its consensus, which is equivalent to the constitution of the blockchain. As long as the vast majority of nodes comply with the consensus requirements, it can guarantee that the results will undoubtedly be credible, even in an untrusted distributed environment. Therefore, the significance of the consensus is that the honest nodes in the blockchain can ultimately achieve the agreement of the ledgers as long as they strictly abide by this consensus.

There are several types of consensus, and the most commonly used are POW, POS, and DPoS. Different blockchain systems will have a unique way of implementation. This article will mainly introduce the DPoS consensus on which STABILA is based. We will also explain the essential components and mechanisms of DPoS.

## Block Producing Process
The executives of the blockchain network collect the newly generated transactions in the blockchain network and verify the legality of these transactions, then package the transactions in a block, record them as a new page on the ledger, and broadcast the page to the entire blockchain network. Other nodes will receive the new page, verify the legality of the page's transaction data, and add it to their ledger. The executives will repeat this process to record all new transaction data in the blockchain system in the ledger.

## DPoS overview
The role of consensus is to select the executives in the blockchain system. The executives verify the transaction data and keep the account in order. They broadcast new accounts to other nodes in the network and obtain the new accounts' approval from other nodes. As a specific implementation of consensus, DPoS works in the following way:

The DPoS consensus selects some nodes as executives in the blockchain system based on the number of votes they receive. First, when the blockchain system starts to operate, a certain number of coins/tokens will be issued, and then the coin/tokens will be given to nodes in the blockchain system. A node can apply to be an executive candidate in the blockchain system with a portion of the coins/tokens. Any token-holding node in the blockchain system can vote for these executives. Every t period, the votes for all the executives will be counted. Top N candidate nodes with the most votes will become executives for the following t period. After t period, the votes will be counted again to elect the new executives, continuing the cycle.

Let's see how it's realized in the context of STABILA:

## Definition
- STABILA: refers to the STABILA network. The document does not distinguish between STABILA, STABILA blockchain, STABILA blockchain system, etc.

- STABILA coin: refers to the equity token issued by and circulating in STABILA, known as STB.

- Executives candidates: nodes eligible for becoming executives in STABILA.

- Executives: nodes in STABILA qualified for bookkeeping. They are usually called executives in DPoS consensus. In STABILA, there will be initially 21 executives, which are also called Governor nodes (or GOV). Here, we will not distinguish between a bookkeeper, Executive, GOV, etc.

- Bookkeeping: the process of verifying transactions and recording them in a ledger. The bookkeeping process is also called block generation because the STABILA ledger is contained within blocks. We will not distinguish between bookkeeping and block generation in the document.

- Bookkeeping order: block generation order. The descending order of the 21 executives is based on the number of votes they receive.

- Block time: STABILA sets block generation time to 3 seconds. A block is generated every 3 seconds.

- Slot: after each block is generated, it can be put into a slot, and each generated block will take up a slot. For example, there are 20 slots for every minute. When a block is generated during the block time, the corresponding slot will be filled. However, if a block is not generated, then the corresponding slot will be empty. The next block generated will fill in a new corresponding slot.

- Epoch: STABILA sets an Epoch to be 6 hours. The last 2 block time of an Epoch is the maintenance period, during which the block generating an order for the next Epoch will be decided.

- The maintenance period: STABILA sets the period to be 2 block time, which is 6 seconds. This period is used to count the votes for executives. There are 4 Epochs in 24 hours, and naturally, 4 maintenance periods. During the maintenance period, no block is generated, and the next Epoch's generation order is decided.

![image](https://github.com/stabilaprotocol/documentation-en/raw/master/images/sequence_en.jpg)

## Election mechanism
1. Votes

In STABILA, 1 STB equals 1 vote.

2. Voting process

In STABILA, voting for executives is a unique transaction. Nodes can vote for executives through generating a voting transaction.

3. Vote counting

During each maintenance period, the votes for executives will be counted. The top 21 executives with the most votes will be the Governors for the next Epoch.

## Block generation mechanism
During each Epoch, the 21 executives will take turns to generate blocks according to the bookkeeping order. Each Executive can only generate blocks when it is their turn. Executives package the data of multiple verified transactions into each block. The previous block's hash will be included in each new block as the parentHash. The Executive will sign the data of this block with its private key and fill in executive_signature, along with the address of the Executive, the block height, and the time that block is generated, etc.

Through storing the hash of the previous block, blocks are logically connected. Eventually, they form a chain. A typical blockchain structure is shown in the following picture:

![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/blockchain_structure.png)


In ideal circumstances, the bookkeeping process in a DPoS consensus-based blockchain system proceeds according to the bookkeeping order calculated in advance. Executives generate blocks in turn. However, the blockchain network is a distributed and untrusted complex system in the following three ways.

- Due to a poor network environment, blocks generated by some executives cannot be received by other executives in valid time (see Figures b1 and b2).

- The regular operation of a particular executive cannot always be guaranteed (see figure c).

- Some malicious executives will generate fork blocks to fork the chain (see figure d).

![image](https://github.com/stabilaprotocol/documentation-en/raw/master/images/longest_chain1_en.png)

![image](https://github.com/stabilaprotocol/documentation-en/raw/master/images/longest_chain2_en.png)

As mentioned above, the basis for the blockchain system to operate normally is that most of the nodes in the system are honest and reliable. Furthermore, the primary guarantee for the security of the blockchain system is the ledger's security, meaning that illegal data cannot be written into the ledger maliciously, and ledger copies saved on each node should be consistent. Based on the DPoS consensus, the bookkeeping process is carried out by executives. Therefore, the safety of STABILA depends on the reliability of the majority of the executives. STABILA confirmed blocks in the system are irreversible. At the same time, to resist the malicious behaviors of a small number of executive nodes, STABILA recognizes the longest chain as the main chain based on "the longest chain principle."

**The confirmed block principle**

The newly produced blocks are unconfirmed. Only those blocks that are "approved" by more than 70% (i.e. 21 * 70% = 15) of the 21 Executives are considered irreversible blocks, commonly referred to as solidified blocks. The entire blockchain network has confirmed the transactions contained in the solidified blocks. The way to "approve" the unconfirmed state block is that the Executive producing subsequent blocks after it, as shown in Figure d, the Executive C produces block 103, the Executive E produces 104' based on block 103, the block 105', 106', and 107' produced respectively by the Executive G, A, and B, are also subsequent blocks of the 103rd block, which means these four blocks approve the 103rd block. It can be seen that when the block of height 121 is produced, the 103rd block becomes a solidified block, since by this time, the 103rd block has 18 subsequent blocks, and the point to be emphasized here is that the Executives producing these 18 blocks must be different from each other and from the Executives producing the 103rd block.

**The longest chain principle**

An honest executive would always choose to produce blocks on the longest chain when a fork occurs.

## Proposal-based parameter adjustment
An essential characteristic of DPoS is that any parameter adjustment can be proposed on the chain, and executives will decide whether to approve the proposal by starting a vote. The advantage of this method is that it avoids hard fork upgrades when adding new features. Currently, STABILA supports the following parameter adjustments:

1. The interval between two maintenance periods

2. The STB cost of applying to be a bookkeeper candidate

3. The STB cost of account activation

4. The bandwidth cost for one byte in each transaction

5. The STB cost of issuing tokens on STABILA

6. The rewards for producing each block

7. The total amount of STB that is proportionately awarded to the first 100th executives with the most votes

8. The STB cost of account activation through system contract

9. The bandwidth cost for account activation

10. The exchange rate between UCR and Unit

11. The STB cost for building an SRC-10 token-based decentralized trading pair

12. The maximum CPU time allowed for a single transaction execution

13. Whether to allow changes of account names

14. Whether to allow the issuance of assets with duplicate names

15. Whether to allow resource delegation

16. The upper limit for UCR in STABILA blockchain

17. Whether to allow SRC-10 asset transfer in the smart contracts

18. Whether to allow adjustment to UCR upper limit

19. Whether to allow multi-signature

20. The STB cost of updating account access

21. The STB cost of multi-signature transactions

22. Whether to verify block and transaction protobuf message


## Appendix: Reference Documentations

- [Delegated Proof of Stake (DPoS) – Total Beginners Guide](https://www.coinbureau.com/education/delegated-proof-stake-dpos/)
- [Consensus Algorithms: Proof-of-Stake & Cryptoeconomics](https://www.nichanank.com/blog/2018/6/4/consensus-algorithms-pos-dpos)
- [Role of Delegates](http://docs.bitshares.org/en/master/technology/dpos.html#role-of-delegates)
