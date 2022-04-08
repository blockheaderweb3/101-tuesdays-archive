- Date: 22/03/2022
- Author: **@_dave**
- Topic: **The Block Header**

# Lecture 007

Hey @everyone.

GE

Welcome to today's edition of 101-tuesdays.
Like @Ameenah rightly [announced](https://discord.com/channels/917010077154680902/917018045015293952/955873858412486708), we will be talking about an integral part of the blockchain.

#### The Block header

Yeah, today's topic is synonymous with our community name.

haha

I know quite a number of us have been wondering what is BlockHeader?
In this session, we will demystify this terminology.
I'll want to appreciate Mayowa's definition of the blockchain.
In case anyone @here, missed that, please refer this [message](https://discord.com/channels/917010077154680902/917018045015293952/955231773799886921)

Blockchain - 2 words:
1. Block 
2. Chain

According to Mayowa, a block is a common noun for a collection of transactions.

What then is a transaction?

A transaction is a binary network message that consists of a sender, recipient, value and data payload. 
Transactions when successfully executed, change the state of network.

**_PS_**: for emphasis, I'm referring to Ethereum blockchain.

**_Recall_**: Ethereum is an open source, globally decentralized computing infrastructure that executes programs called smart contracts.
This collection of transactions (block) are chained/synced/linked together to make the blockchain.

Back to the block: 

Let's break down the composition of a block.

Usually, we use https://etherscan.io/, a block explorer tool to visualize/get real-time block stats/info/transactions as it pertains tokens, blocks, contracts e.t.c.

We can view all the blocks are they're produced in real-time by referring to this tool: https://etherscan.io/blocks - we can find 
details of each block: block number, age (how long ago a given block was produced), transactions (total number of transactions bundled to 
make up a given block), miner details etc. 

Really helpful tool if you want to visualize every thing as they happen in real-time.

Let's take a random block that was recently mined: https://etherscan.io/block/14437811 

This is a reference to block **#14437811**.

When you visit the above page, you'll find important info about this particular block.
This block **#14437811** consists of 68 transactions and 25 contract internal transactions.
Altogether, we have 68 + 25 = total of 93 transaction.

I hope we are following.
At the end of this session, the knowledge we've garnered will be helpful as we dive into querying the blockchain for relevant info.

So back to our breakdown: 

A block consists of: 

1. Block header (this is the part where we drew inspiration for naming this community 😄).

2. Transactions (which are usually bundled up). So let's dive into this part - Block header

The block header consists of: 
   
   A. **ParentHash**: This refers to the Keccak 256-bit hash of the parent/preceeding block’s header, in its entirety.
   
   B. **OmmersHash**: refers to the Keccak 256-bit hash of the ommers list portion of this block.
   
I know this Keccak is a new concept and most of us will be wondering "What is this one again?
I absolutely get it, it's completely understandable.
Ethereum uses Keccak-256 as its cryptographic hash function
So anytime you come across Keccak-256, just remember that Ethereum uses this as its cryptographic hash function.

Let's continue, the third component of the block is

  C. **Beneficiary**: This is the block miner's address, a 160-bit address to which all fees collected from the successful mining of this block be transferred.
  
  D. **State Root**: The Keccak 256-bit hash of the root node of the state trie, after all transactions are executed and finalisations applied.
  
  E. **Difficulty**:  refers to the difficulty of a given block, usually calculated from the previous block’s difficulty level and the timestamp.
  
  F. **Number**: A scalar value equal to the number of ancestor blocks. The genesis block has a number of zero. With reference to https://etherscan.io/block/14437811, the number here is 14437811.
  
  G. **Gas Limit**: A scalar value equal to the current limit of gas expenditure per block.
  
  H. **Gas Used**: A scalar value equal to the total gas used in transactions in this block.
  
  I. **Timestamp**: A scalar value equal to the reasonable output of Unix’s time() at this block’s inception.
  
  J. **Nonce**: A 64-bit value which, combined with the mixhash, proves that a sufficient amount of computation has been carried out on this block.
  
  K. **MixHash**: A 256-bit hash which, combined with the nonce, proves that a sufficient amount of computation has been carried out on this block.
  
If you have carefully followed, you would understand how all these work.
So first , we defined the blocks referring to  Mayowa's position during the last AMA session.

We broke down the components of the block.

Recall, we said the block consists of: Block header and transactions. 

We further broke down the components of the block header, outlining the above key components.

With the above, we have come to the end of today's session. If anyone has questions (I know most people here do cos the whole stuff is technical), 
please feel free to reach out. I'd be more than willing to help clarify the grey areas. 

GN guys 

WAGMI 🚀
