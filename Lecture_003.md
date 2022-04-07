- Date: 22/02/2022
- Author: **@_dave**
- Topic: `Setting up a Blockchain Development Environment (Continued)`

# Lecture 003

Welcome to today's session.
Hope we all had a great day?

Alright last week, we started our journey on how to set up a local blockchain development environment.
And we did set up our ganache (a blockchain simulation running on localhost - port 7545), 
installed truffle and had vscode set up.
We then proceeded to create our GM contract.

So we stopped here at contract declaration.
Today we would complete this contract.
So it's going to be a simple contract that allows us to store and read data - basic write and read.
Solidity is strictly typed language. Meaning we will have to declare types everytime we want to play with data.

As with every programming language, we will store our variable.
In solidity, every variable outside a function is saved in storage.
Storage variables are saved directly on the blockchain.
So we'd create a string variable thus: `string public gmData`

```
contract GM {
  string public gmData;
}
```

So let's go over each of the component of that variable.

- `string` - this data type is a string.
- `public` this refers to the visibility of this variable,  it can be accessed both within this contract and outside the contract. 
   By default, solidity creates a `getter` function for this variable (meaning, you can call it and you'd get a response with the corresponding value saved in this variable).
- `gmData` - this is a user-defined name, you can call it whatever you wish (name, kd, myVar etc) but i've chosen to call it `gmData`.

Now we can proceed to create a function.
```
function setGM(string memory data) public {
  gmData = data;
}
```

So let's break our function down. If you are familiar with JavaScript, you'd discover that this syntax looks more like JavaScript.
Keyword `function` for creating logic.

- `setGM` is the name of the function, whenever we call `setGM` it references the logic we created in this function.
   So since this  function changes the state of the blockchain, we refer to it as a transaction whenever it is called.
- `(string memory data)` we passed in a string parameter called `data` (we can call it anything tho).
- `public` this specifies the visibility of this function.

Then inside the function body we tie our state variable `gmData` to the passed in `data`

We would create a read function.
```
function readGM() public view returns(string memory) {
  return gmData;
}
```
So when we do this: we want to read the already stored string value we saved when we called `setGM` and passed in some string.
Let's break this function down:
- same `function` keyword.
- `public` again this refers to the visibility of this function. If we specify it as private, this function cannot be called outside this contract. 
   We will deal more on visibility later.
- `view` keyword means this function is a read function, meaning it does not change state.
   So whenever we call this function, we can say we have executed a contract call.
- Next is `returns` - this specifies that this function will return data. It's important to state at this point that we must 
  specify the number of data you expect this function to return. So in our case, we are only expecting one data, 
  so we pass in (`string memory`) as the only data we expect. 

Remember solidity is strongly typed language, every data type must be specified.
So that's all guys


Next we would compile our contract and see how we fared.
haha.

I would proceed to compile my contract, then show the result.
Boom, contract successfully compiled.

![image](https://user-images.githubusercontent.com/64266194/162223211-c696b011-ff17-4b89-adb7-3fd5ca2fe5ea.png)


Next we will test our contract.

```
// SPDX-License-Identifier: Unlicensed

pragma solidity >=0.6.0 <0.9.0;

contract GM {
  string public gmData;

  function setGM(string memory data) public {
    gmData = data;
  
  }

  function readGM() public view returns(string memory) {
    return gmData;
  }
}
```

It's best practice to always test our contracts.
Given that after deployment, our contract logic cannot be changed, we must carefully test our logic before we proceed with deployment.

In order not to overwhelm us with too much information this evening, we'd stop here today so that we'd continue next week to finish testing and deployment.
Guys, please feel free to draw my attention to areas that need further clarification.
I'm more than willing to pause whatsoever I'm doing to go over it.
I'm here anytime, to take questions regarding what we've covered so far.
