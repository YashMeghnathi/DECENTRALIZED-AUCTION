# DECENTRALIZED-AUCTION
This is an English Auction, where participants place bids on an item, and the auction ends when no higher bids are placed for a defined period.
# Voting Smart Contract

This repository contains a smart contract for a decentralized voting system built on the Ethereum blockchain using Solidity. The contract allows for the management of candidates, voters, and the voting process itself. It supports features such as candidate registration, voter registration, vote casting, vote delegation, and election management.

## Features
- **Candidate Registration**: Admin can add candidates with a name and proposal.
- **Voter Registration**: Admin can register voters.
- **Election Management**: Admin can start and end the election.
- **Vote Casting**: Registered voters can cast their vote for a candidate or delegate their vote to another registered voter.
- **Vote Delegation**: Voters can delegate their vote to another registered voter if they are unable or prefer not to vote themselves.
- **Election Results**: After the election is over, anyone can view the winning candidate and the vote counts.

## Contract Overview
The contract includes the following features:

- **Admin Controls**: Only the contract admin can add candidates, register voters, and start/end the election.
- **Candidate Struct**: Holds the candidate's ID, name, proposal, and vote count.
- **Voter Struct**: Tracks the voter's registration status, vote status, and any delegation of votes.
- **Events**: Emit events for major actions like adding candidates, registering voters, starting/ending elections, casting votes, and vote delegation.
- **Modifiers**: Ensure that certain actions are only performed by the admin or only during an election.

## Functions

### Admin Functions
- **addCandidate(string memory name, string memory proposal)**: 
  Allows the admin to add a candidate before an election starts.
  
- **addVoter(address voter)**: 
  Allows the admin to register a voter before an election starts.

- **startElection()**: 
  Begins the election process.

- **endElection()**: 
  Ends the election process.

### Voter Functions
- **delegateVote(address to)**: 
  Allows a voter to delegate their vote to another registered voter.

- **Vote(uint256 candidateId)**: 
  Allows a voter to cast their vote for a candidate.

- **getVoterProfile(address voter)**: 
  Retrieves the profile of a specific voter (whether they are registered, whether they have voted, etc.).

### Public Functions
- **getCandidate(uint256 candidateId)**: 
  Returns the details of a candidate.

- **getWinner()**: 
  Returns the winner of the election (after it has ended).

- **getVotes(uint256 candidateId)**: 
  Returns the current vote count of a specific candidate.

## Events
The contract emits the following events:

- **CandidateAdded(uint256 id, string name, string proposal)**: 
  Triggered when a candidate is added.
  
- **VoterAdded(address voter)**: 
  Triggered when a voter is registered.

- **ElectionStarted()**: 
  Triggered when the election begins.

- **ElectionEnded()**: 
  Triggered when the election ends.

- **VoteCasted(address voter, uint256 candidateId)**: 
  Triggered when a voter casts their vote.

- **VoteDelegated(address from, address to)**: 
  Triggered when a voter delegates their vote.

## Security & Restrictions
- **Admin-only Actions**: Only the contract admin can register voters, add candidates, and start/end the election.
- **Vote Delegation**: A voter can delegate their vote only if they haven't already voted.
- **Election Status**: Certain actions (like adding candidates and voters) cannot be performed once the election is ongoing.

## Usage
1. Deploy the contract to the Ethereum blockchain.
2. The admin can add candidates and register voters before starting the election.
3. Once the election is started, registered voters can either cast their vote or delegate their vote.
4. At the end of the election, the winner can be queried and displayed.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

Feel free to fork or contribute to this project!

