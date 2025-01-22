# Auction Contract

This is a smart contract for conducting an auction on the Ethereum blockchain. The contract allows users to place bids on an item, with features for managing bidders, ending the auction, and transferring funds to the owner.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Contract Structure](#contract-structure)
- [Functions](#functions)
- [How to Use](#how-to-use)
- [License](#license)
- [Fork](#fork)

## Overview

This auction contract allows the owner to create an auction for a specific item. Users can place bids on the item, and the highest bidder at the end of the auction wins. The contract includes features to track bidders, the highest bid, and handle the final transfer of funds.

## Features

- **Add Bidders**: The owner can add new bidders with a name and ID.
- **Place Bids**: Users can place bids higher than the current highest bid.
- **Auction Details**: The contract provides details about the auction, including the item, time remaining, highest bidder, and highest bid.
- **Auction End**: The owner can end the auction, transferring the highest bid to the owner.

## Contract Structure

### State Variables:
- `owner`: The address of the contract owner.
- `bidders`: A list of bidders with their name and ID.
- `bidderInfo`: A mapping of bidder addresses to their name and ID.
- `timeend`: The timestamp of when the auction ends.
- `item`: The name of the item being auctioned.
- `highestbidder`: The address of the current highest bidder.
- `highestbid`: The current highest bid.

### Events:
- `BidPlaced(address indexed bidder, uint amount)`: Emitted when a new bid is placed.
- `AuctionEnded(address indexed winner, uint amount)`: Emitted when the auction ends.
- `NewBidderAdded(address indexed bidder, string name, uint id)`: Emitted when a new bidder is added.

### Modifiers:
- `onlyOwner`: Restricts access to functions to the contract owner.
- `AuctionTime`: Restricts bidding to the time before the auction ends.
- `Endtime`: Restricts auction-ending actions to after the auction has concluded.

## Functions

### `constructor(uint _timeend, string memory _item)`
- Initializes the auction with a specified duration (in seconds) and item name.
- The contract creator is set as the owner.

### `addbidder(string memory _name, uint _id)`
- Allows the owner to add a bidder by providing their name and ID.
- The bidder's information is stored, and an event is emitted.

### `bid()`
- Allows users to place a bid.
- A new bid must be higher than the current highest bid.
- If a new bid is placed, the previous highest bidder is refunded.
- An event is emitted when a new bid is placed.

### `endAuction()`
- Allows the owner to end the auction and transfer the highest bid to the owner.
- An event is emitted when the auction ends.

### `getAuctionDetails()`
- Returns the auction details: item name, auction end time, highest bidder address, and highest bid.

### `getBidderData(address _bidder)`
- Returns the name and ID of a bidder by their address.

## How to Use

1. **Deploy the Contract**: When deploying, pass the auction duration (in seconds) and the item name.
2. **Add Bidders**: The contract owner can add bidders using the `addbidder` function.
3. **Place Bids**: Users can place bids using the `bid` function. Bids must be higher than the current highest bid.
4. **End Auction**: Once the auction time is up, the owner can call the `endAuction` function to finalize the auction and receive the highest bid.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Fork

Feel free to fork this repository and modify it for your own purposes. 
