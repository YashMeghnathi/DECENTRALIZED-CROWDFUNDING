# DECENTRALIZED-CROWDFUNDING
Decentralized crowdfunding is a method of raising funds through blockchain technology, allowing direct contributions from supporters without intermediaries.
# Crowdfunding Contract

This is a smart contract for managing a crowdfunding campaign on the Ethereum blockchain. It allows users to donate to a cause, with features for managing donations, tracking contributors, and allowing the manager to withdraw funds once the campaign is over.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Contract Structure](#contract-structure)
- [Functions](#functions)
- [How to Use](#how-to-use)
- [License](#license)
- [Fork](#fork)

## Overview

This crowdfunding contract allows a manager to set up a campaign with a specific purpose and a donation deadline. Users can donate Ether to the campaign, and the manager can withdraw the funds once the deadline has passed. The contract tracks each donator's contribution and provides functionality to update the campaign purpose.

## Features

- **Donate**: Users can donate Ether to the campaign.
- **Manager Controls**: The manager can update the campaign purpose and withdraw the funds once the donation period ends.
- **Donation Tracking**: The contract tracks the amount each user has donated and the total number of unique donors.
- **Campaign Deadline**: Donations are only allowed before the campaign deadline.
- **Event Emissions**: Events are emitted when donations are made, funds are withdrawn, and the campaign purpose is updated.

## Contract Structure

### State Variables:
- `manager`: The address of the contract manager (creator of the campaign).
- `purpose`: A string representing the purpose of the crowdfunding campaign.
- `deadline`: The timestamp of when the donation period ends.
- `donators`: A mapping of donor addresses to the amount they have donated.
- `noofdonators`: The total number of unique donators.

### Events:
- `DonationMade(address indexed donator, uint amount)`: Emitted when a donation is made.
- `FundsWithdrawn(address indexed manager, uint amount)`: Emitted when the manager withdraws the funds.
- `PurposeUpdated(string newPurpose)`: Emitted when the campaign purpose is updated.

### Modifiers:
- `onlyManager`: Restricts access to certain functions to the contract manager.
- `donationON`: Restricts donation functions to before the campaign deadline.
- `donationOFF`: Restricts donation and withdrawal actions to after the campaign has ended.

## Functions

1. **`constructor(string memory _purpose, uint _deadline)`**
    - Initializes the crowdfunding campaign with the specified purpose and donation deadline.
    - The contract creator is set as the manager.

2. **`donate()`**
    - Allows users to donate to the campaign. Donations must be at least 10 Ether and can only be made before the campaign deadline.
    - An event is emitted each time a donation is made.

3. **`withdraw()`**
    - Allows the manager to withdraw all the funds after the donation period has ended.
    - An event is emitted when the funds are withdrawn.

4. **`updatePurpose(string memory _newPurpose)`**
    - Allows the manager to update the purpose of the campaign.
    - An event is emitted when the purpose is updated.

5. **`donatorshistory()`**
    - Returns the amount donated by the sender address.

6. **`returndonators()`**
    - Returns the total number of unique donators.

7. **`getBal()`**
    - Returns the balance of the crowdfunding contract (total funds raised).

## How to Use

1. **Deploy the Contract**: When deploying, pass the campaign purpose and the donation deadline (in seconds).
   Example:
   ```solidity
   Crowdfunding crowdfunding = new Crowdfunding("Help Build a School", 30 days);
   ## How to Use

1. **Donate to the Campaign**  
   Users can donate to the campaign using the `donate` function. Each donation must be at least 10 Ether and can only be made before the campaign deadline.

2. **Manager Withdraws Funds**  
   Once the donation period ends, the manager can withdraw the funds using the `withdraw` function. All the funds raised during the campaign will be transferred to the manager's address.

3. **Update Campaign Purpose**  
   The manager can update the purpose of the campaign anytime using the `updatePurpose` function. This allows the manager to change the cause or goal of the campaign during the crowdfunding period.

4. **Track Donations**  
   - Donors can check their donation history using the `donatorshistory` function. This will return the total amount donated by the sender's address.
   - Anyone can see the total number of unique donors via the `returndonators` function, which provides the total count of individual donators.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Fork

Feel free to fork this repository and modify it for your own purposes. Contributions are welcome! If you have suggestions or improvements, feel free to open an issue or submit a pull request.


