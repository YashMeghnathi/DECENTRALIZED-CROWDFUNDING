# DECENTRALIZED CROWDFUNDING

Decentralized crowdfunding is a method of raising funds through blockchain technology, allowing direct contributions from supporters without intermediaries.

## Crowdfunding Contract

This is a smart contract for managing a crowdfunding campaign on the Ethereum blockchain. It allows users to donate to a cause, with features for managing donations, tracking contributors, and allowing the manager to withdraw funds once the campaign is over.

## Overview

The Crowdfunding Contract is a decentralized platform on the Ethereum blockchain designed to enable secure, transparent fundraising campaigns. It allows users to donate directly to a cause, with the campaign manager controlling the campaign’s purpose and fund withdrawal after the donation period ends. Donations are tracked and only accepted before the deadline, ensuring full transparency and eliminating the need for intermediaries. The contract allows the manager to update the campaign's purpose and withdraw funds once the goal is reached, providing a flexible and secure solution for fundraising.

## Objective

The primary objective of the Crowdfunding Contract is to create a decentralized, secure, and transparent platform for fundraising. By using blockchain technology, the contract removes the need for intermediaries, ensuring that all transactions are directly between the donors and the campaign manager. Key objectives of the contract include:

- **Decentralized Donations**: All donations are processed directly on the blockchain, removing the need for centralized intermediaries.
- **Transparency**: The donation history, amount raised, and contributors are fully visible on the blockchain, ensuring transparency.
- **Security**: The funds are safely stored in the contract until the manager withdraws them after the campaign deadline.
- **Manager Flexibility**: The manager has the flexibility to update the campaign's purpose as needed during the donation period.
- **Efficient Fund Withdrawal**: Once the donation period ends, the manager can withdraw the funds, providing an easy and secure method to access the raised funds.

This contract provides an essential framework for running crowdfunding campaigns with complete transparency and trust, leveraging the security and immutability of the Ethereum blockchain.

## Features

- **Donate**: Users can donate Ether to the campaign.
- **Manager Controls**: The manager can update the campaign purpose and withdraw the funds once the donation period ends.
- **Donation Tracking**: The contract tracks the amount each user has donated and the total number of unique donors.
- **Campaign Deadline**: Donations are only allowed before the campaign deadline.
- **Event Emissions**: Events are emitted when donations are made, funds are withdrawn, and the campaign purpose is updated.

## Technologies Used

- **Solidity**: The smart contract is written in Solidity, the primary language for developing Ethereum smart contracts.
- **Ethereum Testnet**: The contract is deployed and tested on an Ethereum test network before deploying to the Ethereum mainnet.
- **MetaMask**: A popular cryptocurrency wallet and browser extension used to interact with the Ethereum testnet and manage transactions during deployment.
