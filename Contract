// SPDX-License-Identifier: MIT
pragma solidity >=0.8.0;

import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

// Crowdfunding contract inheriting from ReentrancyGuard to prevent re-entrancy attacks
contract Crowdfunding is ReentrancyGuard {

    // State variables
    address public manager;            // The manager of the crowdfunding campaign
    string public purpose;             // The purpose of the campaign
    uint public deadline;              // The deadline for the crowdfunding campaign
    mapping(address => uint) public donators;  // Mapping to track how much each address has donated
    uint public noofdonators;          // Total number of unique donators

    // Modifier that restricts function access to only the manager of the campaign
    modifier onlyManager() {
        require(msg.sender == manager, "Only the manager can call this function");
        _;
    }

    // Modifier to check if donations are still open (before deadline)
    modifier donationON() {
        require(block.timestamp < deadline, "The donation period has ended");
        _;
    }

    // Modifier to check if donations are closed (after the deadline)
    modifier donationOFF() {
        require(block.timestamp >= deadline, "The donation period is still ongoing");
        _;
    }

    // Events for logging important actions
    event DonationMade(address indexed donator, uint amount);
    event FundsWithdrawn(address indexed manager, uint amount);
    event PurposeUpdated(string newPurpose);

    // Constructor to initialize the crowdfunding campaign
    constructor(string memory _purpose, uint _deadline) {
        manager = msg.sender;                // Set the manager as the address deploying the contract
        purpose = _purpose;                  // Set the initial purpose of the campaign
        deadline = block.timestamp + _deadline; // Set the deadline for the crowdfunding
    }

    // Function to donate to the campaign (only allowed before the deadline)
    function donate() public payable donationON {
        // Ensure that the donation is at least 10 ether
        require(msg.value >= 10 ether, "at least pay 10 ether");

        // If the donator has not donated before, increment the number of unique donators
        if (donators[msg.sender] == 0) {
            noofdonators++;
        }

        // Increase the donation amount for the sender
        donators[msg.sender] += msg.value;

        // Emit the donation event
        emit DonationMade(msg.sender, msg.value);
    }

    // Function for the manager to withdraw the funds after the deadline
    function withdraw() public onlyManager donationOFF {
        uint balance = address(this).balance; // Get the balance of the contract
        payable(manager).transfer(balance);   // Transfer the balance to the manager
        emit FundsWithdrawn(msg.sender, balance); // Emit the withdraw event
    }

    // Function to allow the manager to update the campaign purpose
    function updatePurpose(string memory _newPurpose) public onlyManager {
        purpose = _newPurpose;             // Update the purpose of the campaign
        emit PurposeUpdated(_newPurpose);  // Emit an event when the purpose is updated
    }

    // Function to check how much a specific address has donated
    function donatorshistory() public view returns (uint) {
        // Ensure the sender has donated before
        require(donators[msg.sender] > 0, "You haven't donated yet");
        return donators[msg.sender]; // Return the amount donated by the sender
    }

    // Function to get the total number of unique donators
    function returndonators() public view returns (uint) {
        return noofdonators; // Return the total number of unique donators
    }

    // Function to get the current balance of the contract
    function getBal() public view returns (uint256) {
        return address(this).balance; // Return the balance of the contract
    }
    
    // Additional featuresd could be added
    //  Minimum donation limit can be set dynamically and updated by the manager if needed.
    //  Refund function could be added if the campaign goal isn't met.
    //  Total funds raised could be calculated by tracking the sum of donations.
    //  donation goal can be added to cap the maximum amount to be raised.
}
