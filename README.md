# Proveably Random Raffle Contracts

## About

This code is to create a proveably random smart contract lottery.

## What We Want it to do?

# 1. Users can enter by paying for a ticket.
     1. The ticket fees are going to go to the winner during the draw
  2. After X period of time, the lottery will automatically draw a winner.
    1.This will be done programatially
  3. Chainlink VRF and Chainlink Automation.
    1. Chainlink VRF -> Randomness
    2. Chainlink Automation -> Time based trigger

##Tests!
1. Write some deploy scripts.
2. Write our tests.
   1. Work on a local chain
   2. Forked testnet
   3. forked mainnet

Foundry Smart Contract Lottery
Getting Started
Requirements
Quickstart
Optional Gitpod
Usage
Start a local node
Library
Deploy
Deploy - Other Network
Testing
Test Coverage
Deployment to a testnet or mainnet
Scripts
Estimate gas
Formatting
Thank you!
Getting Started
Requirements
git
You'll know you did it right if you can run git --version and you see a response like git version x.x.x
foundry
You'll know you did it right if you can run forge --version and you see a response like forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)
Quickstart
git clone https://github.com/Cyfrin/foundry-smart-contract-lottery-f23
cd foundry-smart-contract-lottery-f23
forge build
Optional Gitpod
If you can't or don't want to run and install locally, you can work with this repo in Gitpod. If you do this, you can skip the clone this repo part.

Open in Gitpod

Usage
Start a local node
make anvil
Library
If you're having a hard time installing the chainlink library, you can optionally run this command.

forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 --no-commit
Deploy
This will default to your local node. You need to have it running in another terminal in order for it to deploy.

make deploy
Deploy - Other Network
See below

Testing
We talk about 4 test tiers in the video.

Unit
Integration
Forked
Staging
This repo we cover #1 and #3.

forge test
or

forge test --fork-url $SEPOLIA_RPC_URL
Test Coverage
forge coverage
Deployment to a testnet or mainnet
Setup environment variables
You'll want to set your SEPOLIA_RPC_URL and PRIVATE_KEY as environment variables. You can add them to a .env file, similar to what you see in .env.example.

PRIVATE_KEY: The private key of your account (like from metamask). NOTE: FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
You can learn how to export it here.
SEPOLIA_RPC_URL: This is url of the sepolia testnet node you're working with. You can get setup with one for free from Alchemy
Optionally, add your ETHERSCAN_API_KEY if you want to verify your contract on Etherscan.

Get testnet ETH
Head over to faucets.chain.link and get some testnet ETH. You should see the ETH show up in your metamask.

Deploy
make deploy ARGS="--network sepolia"
This will setup a ChainlinkVRF Subscription for you. If you already have one, update it in the scripts/HelperConfig.s.sol file. It will also automatically add your contract as a consumer.

Register a Chainlink Automation Upkeep
You can follow the documentation if you get lost.

Go to automation.chain.link and register a new upkeep. Choose Custom logic as your trigger mechanism for automation. Your UI will look something like this once completed:

Automation

Scripts
After deploying to a testnet or local net, you can run the scripts.

Using cast deployed locally example:

cast send <RAFFLE_CONTRACT_ADDRESS> "enterRaffle()" --value 0.1ether --private-key <PRIVATE_KEY> --rpc-url $SEPOLIA_RPC_URL
or, to create a ChainlinkVRF Subscription:

make createSubscription ARGS="--network sepolia"
Estimate gas
You can estimate how much gas things cost by running:

forge snapshot
And you'll see an output file called .gas-snapshot

Formatting
To run code formatting:

forge fmt
Thank you!

   



   
