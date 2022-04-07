- Date: 15/02/2022
- Author:**@_dave**
- Topic: `Setting up a Blockchain Development Environment`


# Lecture 002

Hey guys, welcome to today's edition of our 101-tuesdays. 

Today, we will be diving into some real stuff.
We would be Setting up a Blockchain Development Environment.
Are we ready?
if you're ready, let me see some emoji reactions.
haha.
I believe a good number of folks @here are devs.
Before we proceed, I would like to state that this won't be a complete beginner session.

To follow along,  I expect that you should have some basic understanding of programming... 
whether Javascript, python, php, java etc
Ethereum is a super powerful blockchain, thanks to its inherent ability that allows developers deploy 
programmable self-executing logic commonly referred to as **Smart Contract**.

Smart contracts are created using Solidity, Vyper, LLL,  Serpent e.t.c languages.
Amongst these languages, Solidity and Vyper are commonly used.
The creation of Solidity was led by Garvin Wood (now the co-founder of Polkadot blockchain),
and it is highly influenced by JavaScript, C++, Python and currently the most popular language for creating smart contracts.
Logically similar to Solidity and syntactically similar to Python, Vyper on the other hand, 
is another popular language for building smart contract popular amongst smart contracts developers.
Anyways, I won't bore us this evening with much talk.
For the purpose of this session, we'd focus on solidity.

So this is the stack for building dapps:
```
  1. Smart contract development - Solidity
  2. Smart contract testing/deployment framework. - Truffle/Hardhat/Dapptools/Brownie
  3. Web3 Client - Web3js, Ethersjs. 
  4. Frontend Framework - React, Svelte, Vue, Angular, HTML/CSS/JS
  5. Local Blockchain - Ganache CLI, Hardhat CLI (local instance of our blockchain before we deploy to 
     test network (testnet)/ main network (mainnet)
 ```
 
 Tools: 
 ```
1. Metamask - Desktop wallet for interacting with smart contracts (ordinarily, smart contracts are abstract, 
   however, to bring it home to users, a browser client/ web3 provider which securely houses our private key 
   and allows us to sign blockchain transactions is essential. This is how users can relate/interact with the blockchain)
2. Visual Studio Code - our code editor
```

I hope this is not boring guys.
haha.
I know these are new terminologies and are  kinda confusing, but we will get used to them with time.
However, at the end of this session, I'd drop some resources.
So we can all follow up.
So these are required to build a full stack dapp
Remember guys,  dapp is a short term for  **Decentralized application**.

So simply put, an application with a UI/frontend whose backend logic (smart contract) is running on Ethereum blockchain.
So the above technologies/tools will be used as we proceed to build our first dapp.

First off, we would open our VSCode.
We would be using [Truffle](https://github.com/trufflesuite/truffle) as our test/deployment framework.

Recall, guys, Truffle or Hardhat can be used.
For this project, please note that we would be using the following stack:
```
1. Backend
  a. Solidity - building our smart contract.
  b. Ganache - Local instance of our blockchain which will be running on localhost port 7545.
  c. Truffle - testing/deploying smart contract; just to point out that under the hood, Truffle 
     uses Mocha (testing framework) and Chai (Assertion library). 
PS: Truffle and Ganache is a popular combination

2. Frontend 
  a. Web3js -  Web3 Client. 
  b. React - frontend framework.
```

[Ganache](https://trufflesuite.com/ganache/), is the local instance of our blockchain. It's like the localhost for our blockchain application. 

So let's get started.
@here please visit https://trufflesuite.com/ganache/ and download Ganache.

Regardless of your PC OS (Mac, Windows, Linux), you can download and install Ganache.
We should have a screen looking like this when Ganache is successfully installed.

![image](https://user-images.githubusercontent.com/64266194/162193264-c2adaad3-813a-4d13-9302-e113762a8eb0.png)

We would go over some key components of this page.
Remember, when you have ganache running, you should have this page.
On this page, we have our mnemonic phrase (remember guys, never expose your mnemonic phrase. 
I'd never advise us to use this mnemonic phrase for serious/monetary transactions) .
We discussed about Mnemonic phrases last week.
So the mnemonic phrase here is used to generate these accounts prefixed with0x0.

The primary account is account at `index 0` that simulates the main account which we will use for signing our local blockchain transactions
Each account is prefunded with test `100 ETH`.
I want everyone @here to note that this only for test purposes and cannot be used in real live since 
it is siloed in our local blockchain environment and it has no monetary value.
Just good we clarify before some folks in here will be cracking their head on how to use these Ether....haha.

Like i earlier said, Ganache is our local blockchain and it is running on `PORT 7545` - `http://localhost:7545/` by default.
As referenced under `RPC SERVER` section of this already-running ganache page.
TBH if I'm asked "_Which test framework will I choose between Ganache and Hardhat?_" this is my [response](https://discord.com/channels/917010077154680902/917018425728049232/925170313996673025).

However, We would use Ganache cos it's a GUI, pretty easy to visualize and 
it's cool for newbies who would like to see some relevant blockchain metadata as they are being executed in real-time.
So we are done with Ganache.

Let's proceed to `Truffle`.
To install Truffle, you must have [Node](https://nodejs.org/en/) installed on your machine.

I recommend intalling Node 16.14.0 LTS.
After successfully installing node, type `node -v` on your terminal to display the current version
of node running on your machine.

Next, we proceed to install Truffle.
We can do this with `npm install -g truffle` this ensures Truffle is installed globally. After that
just the way we verified the successful installation of Node on our machine,
we can type this command on our terminal: `truffle version`

![image](https://user-images.githubusercontent.com/64266194/162196549-ded885cf-c953-4874-9ae1-8bb3710a6aae.png)

We should have the above info displayed.
Just to be sure, Truffle was successfully installed.
Next, we initialize truffle.

Awesome. So
- Open your vscode
- Create a folder, call it anything you want. As for me, I called mine `tutorial-project`
- CD into this project folder. Make sure you're at the root of this folder
- Then we should initialize a new truffle project with this command `truffle init`

When done, your terminal should look like the referrenced screenshot.
If this step is successful, we should have the following generated folders: 
1. contracts
2. migrations
3. test, then lastly 
4. A file called `truffle-config.js`

So I would explain the purpose of each of these.

1. **Contracts**: this is the folder that will house all our smart contract files.
Inside this folder, we will create a new file called `GM.sol`.
`gm` is the term that depicts positive vibes in web3 community. we use  this term to say good morning.
For us as blockchain devs, instead of the conventional `Hello World` commonly used to start new projecs in web2, we will use `GM`.
So our `GM.sol` should be inside our contracts folder. `.sol` is the extension for save solidity files.

2. **Migrations Folder**: this folder will wrap all the scripts required to deploy our smart contract to the blockchain. 
Truffle already created one already for use  - `1_initial_migration.js`

3. **Test Folder**: This is the folder where we have all our test javascript files.
Testing is pretty important in smart contract development.
So we'd be testing our smart contracts.
We will go over the importance later.

So we are not lost, let's note the following: 
Contract Folder - we save our solidity files, all files with `.sol` extensions are saved here. No javascript file should be saved in this folder.
Migration Folder - all javascript files necessary for deploying our smart contract to the blockchain should be saved in here.
Test Folder - Again here, we have our js test files.
Then the last and pretty important file in our setup is `truffle-config.js`.
This is where we write our truffle config logic. Most importantly, to deploy to a live network
we will use our mnemonic phrase/private key to successfully execute our deployment.
So usually instead of leaving our wallet credentials (mnemonic phrase/private key) exposed in this config file, 
we would be installing and using `dotenv` package.

`npm i dotenv` on the root folder
then we create a `.env` file on our root directory/folder.

Inside this `.env` file, we would safely store our mnemonic phrase/private key. Anyway, let's leave that for now.
We would come to that when we are ready to deploy on live testnet.
So let's start by creating our first Smart Contract (SC) for short.
This is the fun part.

So remember, we created a `GM.sol` file.
So open that file in your vscode.
We would be coding now, this is the fun part.
So we are gonna be building a simple smart contract that says `GM`.

line 1
```
// SPDX-License-Identifier: Unlicensed
```

This specifies the license for this contract we are building.
There are different types of specifications, MIT, GPL-3 etc, 
this line is important otherwise we will always see a warning ⚠️  on our dev terminal.
So it's best practice to add this `Software Package Data Exchange` on the first line of all our solidity files.

Next we declare our pragma statement:
```
pragma solidity >=0.5.0 <0.9.0;
```
This line 2 code simply tells solidity compiler about the range of solidity versions this particular smart contract
can be compiled with.So solidity compilers (solc) greater than 0.5.0 and lesser than 0.9.0 should compile this given contract
we are about to create.

Next we declare our Contract
```
contract GM {

}
```

This is a decaration that shows we are creating our smart contract - `GM`.
The keyword `contract` is reserved.
GM is the name we have given our smart contract.
So by way of convention, the name of our smart contract should be consistent with the name of the  contract's solidity file.
In our case our contract is `GM` and we have also named the solidity file `GM.sol`.
At this point, I will call it a night.
So we don't overwhelm ourselves with too much info.
Next week, we'd start from where we stopped this evening.


Guys, [solidity official docs](https://docs.soliditylang.org/en/v0.8.8/introduction-to-smart-contracts.html#a-simple-smart-contract) is the best resource in our journey to understand some basic concepts about writing smart contracts.
