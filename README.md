# Token-main (ERC-20)

This repository contains the source code for the Token-main(TM) token, an ERC-20 token deployed on the Sepolia testnet. The token is initialized with a total supply of 2000 tokens and includes extra functionality to access transaction details.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [License](#license)

## Features

- **ERC-20 Standard**: Implements the ERC-20 token standard.
- **Initial Supply**: Mints 2000 tokens to the deployer’s address upon deployment.
- **Transaction Information**:
- Get the block timestamp of the most recent transaction in a readable format.  
- Get the sender's address of the transaction.  
- Get the receiver's address of the transaction.  

## Prerequisites

Before starting, make sure the following are installed:

- [Node.js](https://nodejs.org/) (v16 or higher)
- [Hardhat](https://hardhat.org/)
- [MetaMask](https://metamask.io/) 
- Sepolia testnet ETH 

## Installation

1. Clone the repository:

    ```
    git clone https://github.com/Kuvernoori/Token.git
    cd Token
    ```
2. Install dependencies:
    ```
    npm install
    ```
3. Set up environment variables:
   
    Create a `.env` file in the root directory and add the following:
    ```
      url: process.env.QUICKNODE_URL,
      accounts: [process.env.PRIVATE_KEY],
    ```
## Usage
### Compile the Contract
Compile the smart contract:
```
npx hardhat compile
```
### Deploy the Contract
Deploy the contract to the Sepolia testnet:
```
npx hardhat run scripts/deploy.js --network sepolia
```
### Interact with the Contract
1. Open the Hardhat console:
    ```
    npx hardhat console --network sepolia
    ```
2. Attach to the deployed contract:
    ```
    const contractAddress = "0xYourContractAddress";
    const AITU2329 = await ethers.getContractFactory("AITU2329");
    const token = await AITU2329.attach(contractAddress);
    ```
3. Example interactions:
    - **Get the latest transaction timestamp:**
      ```
      const timestamp = await token.getLatestTransactionTimestamp();
      console.log("Latest Transaction Timestamp:", timestamp);
      ```
    - **Get the transaction sender:**
      ```
      const sender = await token.getTransactionSender();
      console.log("Transaction Sender:", sender);
      ```
    - **Get the transaction receiver:**
      ```
      const receiverAddress = "0xReceiverAddress";
      const receiver = await token.getTransactionReceiver(receiverAddress);
      console.log("Transaction Receiver:", receiver);
      ```
## Examples
### Deploying the Contract
```
npx hardhat run scripts/deploy.js --network sepolia
```
### Checking Token Balance
```
const balance = await token.balanceOf("0xYourWalletAddress");
console.log("Token Balance:", balance.toString());
```
## License
This project is licensed under the MIT License. See the [LICENSE](LICENCE) file for details.
