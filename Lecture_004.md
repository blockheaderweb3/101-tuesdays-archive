- Date: 01/03/2022
- Author: **@_dave**
- Topic: **Setting up a Blockchain Development Environment (Continued)**

# Lecture 004

GM @everyone.

How are we all doing?
Trust we're had a wonderful day?

So we started this blockchain local development setup series 2 weeks ago.
In the first week, we introduced solidity and the basic set up tools.
Last week, we wrote our GM contract, we broke down the structure and at the end we successfulluy compiled it.
So today, we'd proceed to the final step, which is 

**Deployment**

So like I said last week, before deployment, it's best practice to test out our contract to ensure 
it's functionally working the way we intended.

> **NOTE**: Upon successful deployment of a contract to the blockchain, its logic cannot be changed. 
If there are errors with the logic, it cannot be modified once it has been successfully deployed 
that's why testing is serious business in smart contract development.

Guys, remember we have our test folder in our root.
Our `test` folder is home to all our JavaScript test files.
We will start by navigating to our test folder, there we will create a file `GM.test.js` like so: 

![image](https://user-images.githubusercontent.com/64266194/162233863-4c042ec5-49a3-4a50-bdcf-ac513522b25b.png)

Inside here `GM.test.js`, we'd write unit tests.

So here we go.
Was trying to make sure everything is up to date and working as intended.
haha

```
const GM = artifacts.require('GM')

let GMContract, gmContract



contract('GM Contract', async ()  => {
  beforeEach(async () => {
    gmContract = await GM.deployed()
  })

  contract('Deployment', () => {
    it('Should successfully deply GM contract', async () => {
      console.log(`gm contract here: ${gmContract}`)
    })
  })
})
```

This should be the content of our `GM.test.js` file (remeber we are adding this to our test folder).
Then for this to work, we need to have a migration file in a our migration folder.

Referring to this screenshot, inside my `migrations` folder, I have my `1_initial_migration.js` file
so there, I will write a script that's responsible for the successful migration of my contract.
Please note that `migration` is the same as `deployment`, we can use both words interchangeably.

So in our case, since we are using truffle, we should have all our deployment/migration script in our migration folder.
So I would add a lil bit of comment so the code is self explanatory.

```
// get an instance of our GM contract
const GM = artifacts.require('GM')
let GMContract, gmContract

contract('GM Contract', async () => {

  // save an instance of our deployed contract as gmContract in the global scope 
  beforeEach(async () => {
    gmContract = await GM.deployed()
  })

  contract('Deployment', () => {
    it('Should successfully deply GM contract', async () => {
      console.log(`gm contract here: ${gmContract}`)
    })
  })
})
```

I added the comments to make a bit more understandable
so moving to our migration file

```
// get an instance of our contract
const GM = artifacts.require("GM")

module.exports = async (deployer)  => {
  // deploy our GM contract
  await deployer.deploy(GM)

  // save the deployed instance of our GM contract
  const gm = await GM.deployed()

  // log the address of the deployed GM contract
  console.log(`gm address: ${gm.address}`)
}
```

This is basically our migration file. Rememeber we saved it as `1_initial_migration.js`. 
The comment is pretty self-explanatory so I will move pretty fast.

However, if anyone @here is kinda confused about any line of code so far, 
please you're free to draw my attention to such unclear area.
I'd go over it, till we get it.

So here's the result of our first unit test: 

![image](https://user-images.githubusercontent.com/64266194/162235897-9cdad2dc-be45-401f-b83d-5d08470d128a.png)

From the root directory, when you run `truffle test` you should have a similar terminal log like the above screenshot.
Let me break down what happened here.
Remeber, our contract must be compiled to bytecode that the EVM must understand.
A contract is vague without successful compilation.
Compilation simply turns our human-readable solidity contract into machine-readable bytecode.
The `bytecode` is what the `Ethereum Virtual Machine - EVM` understands.

Basically when we run `truffle test`, our code is first compiled before being tested.
A poorly structured contract, ridden with errors, will never compile.
Remember guys, we are using `Mocha` (testing framework) and `Chai` (assertion library) under the hood when we run `truffle test`. 

So we move on to the next test.

Truffle is slow 😢.
We would use hardhat in subsequent project.

```
// get an instance of our GM contract
const GM = artifacts.require('GM')

let GMContract, gmContract,  deployer, deployerAccount

contract('GM Contract', async accountsPayload => {
  let accounts = accountsPayload
  deployer = accounts[0]
  // deployerAccount = deployer

  // save an instance of our deployed contract as gmContract in the global scope 
  beforeEach(async () => {
   
    gmContract = await GM.deployed()
  })

  contract('Deployment', async () => {
    it('Should successfully deploy GM contract and log the deployed GM contract address' , async () => {
      console.log(`gm contract here: ${gmContract.address}`)
    })

    
  })
  contract('Transaction', () => {
    it('Should successfully change the state to gm' , async () => {
      // get initial value of gm state
      const initialGMValue = await gmContract.readGM()

      // log initial value of gm state
      console.log(`initial GM state here: ${initialGMValue}`)
      

      // transaction: deployer modifies gm state by setting gm to 'GM'
      await gmContract.setGM('GM', { from: deployer })

      // read gm state again after modification
      const finalGMValue = await gmContract.readGM()


      // log the final value of gm state
      console.log(`initial GM state here: ${finalGMValue}`)

      // assert statement to check the final gm value === the passed in value
      assert.equal(finalGMValue, 'GM')
      
    })
  })
})
```

So we here we have our second unit test.
We are testing the transaction.

**_Recall_**: we first defined a transaction as a state-changing action.
Any action that modifies the state of the blockchain is referred to as transaction.
So again I added comments to make the above code self-explanatory.
If anyone @here has issues interpreting this code, please call my attention.
Remember, to start your web3/blockchain development journey, I assume you must have some practical programming experience especially with JavaScript.

So guys, that's it.
In the above test, we were able to read the initial state of our `gm` state by calling `readGM` function and successfully modify it by calling `setGM`.

Let me show you guys the result of this test: 

![image](https://user-images.githubusercontent.com/64266194/162237903-f189e1bc-f9f4-4be9-95fa-322a4d595ffd.png)

All test cases are successfully passing.
Let me intentionally modify the assert statement so it throws an error,  thus:

![image](https://user-images.githubusercontent.com/64266194/162238039-032d0c59-cf46-4dac-af26-1d2e55795d2f.png)

So here, I modified the assert statement by entering a different value other than what I initially entered. 
Instead of GM, I passed in Blockheader, hence the above error, an intentional move to make the assert statement to fail.
So let me remodify it back to GM.
We should have all our test cases passing.

![image](https://user-images.githubusercontent.com/64266194/162238297-7a64cf55-c990-4e24-8e99-9922c249c3d3.png)

Again our test cases are passing.
With this, we have come to an end of testing.
We move on to the final final step.

**DEPLOYMENT**

This is the process of moving our contract to the blockchain. Remember the test is a simulation of the real thing.
Now we are going to the real thing - to deploy.

Guys, do we remember our `truffle-config.js` file?
This is the file responsible for the configuration necessary for successful deployment to local ganache, testnet and mainnet.

```
module.exports = {
 
  networks: {
    development: {
     host: "127.0.0.1",     // Localhost (default: none)
     port: 7545,            // Standard Ethereum port (default: none)
     network_id: "*",       // Any network (default: none)
    },
  },
  // Configure your compilers
  compilers: {
    solc: {
      version: "0.8.10",    // Fetch exact version from solc-bin (default: truffle's version)
    }
  },
};
```

This is our config file.
So with this we can successfully deploy our contract to ganache.
The network is where we specify the network to which which we want to deploy our contract.
In our case here
We want to deploy to localhost.
Recall ganache is our localhost blockchain.
So we can migrate/deploy our contract with this command `truffle deploy --network development`.

**_Recall_**: in our config file, we specified `development` as name of the network we would be deploying to, 
hence  we have `development` in the above truffle command.

![image](https://user-images.githubusercontent.com/64266194/162241210-1a9d27b5-ab75-438a-af55-4bc700da5065.png)

Boom!

Here we have it. A screenshot of our successfully deployed contract.
With this, we have come to the end our session.

If anyone @here has question about what we covered today, please feel free to ask.
I'm here to respond to questions.


Just to recap:
We started this journey by setting up our environment [here](Lecture_002.md)

Then we wrote the functions of the GM contract which we compiled.

Today, we tested and successfully deployed our contract.

So if you are looking at the starting your journey, please always refer to this channel.
