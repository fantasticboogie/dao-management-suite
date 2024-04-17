# Decentralized Autonomous Organization (DAO) Management Suite

This package provides a comprehensive suite for managing Decentralized Autonomous Organizations (DAOs) on the blockchain.

## Installation

```bash
npm install dao-management-suite
```

## Usage

```javascript
const DAOManagementSuite = require('dao-management-suite');
const Web3 = require('web3');

// Initialize Web3 with your provider
const web3Provider = 'https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID';
const web3 = new Web3(web3Provider);

// Define DAO contract address
const daoContractAddress = '0xYOUR_DAO_CONTRACT_ADDRESS';

// Create a new instance of DAOManagementSuite
const daoManager = new DAOManagementSuite(web3Provider, daoContractAddress);

// Example: Create a proposal
const proposalData = {
    title: 'New Proposal',
    description: 'This is a test proposal.',
    recipient: '0xRECIPIENT_ADDRESS',
    amount: '1000000000000000000', // 1 ETH in wei
    deadline: Math.floor(Date.now() / 1000) + 3600 // 1 hour from now
};
daoManager.createProposal(proposalData)
    .then(proposalId => {
        console.log('Proposal created:', proposalId);
    })
    .catch(error => {
        console.error('Error creating proposal:', error);
    });
```

## API

### `createProposal(proposalData)`

Creates a new proposal in the DAO.

- `proposalData`: An object containing the proposal details, including `title`, `description`, `recipient`, `amount`, and `deadline`.

Returns a promise that resolves to the ID of the created proposal.

### `voteOnProposal(proposalId, vote)`

Casts a vote on a proposal in the DAO.

- `proposalId`: The ID of the proposal to vote on.
- `vote`: The vote to cast (e.g., "yes", "no").

Returns a promise indicating the success of the vote.

### `executeProposal(proposalId)`

Executes a passed proposal in the DAO.

- `proposalId`: The ID of the proposal to execute.

Returns a promise indicating the success of the execution.

### `getProposal(proposalId)`

Retrieves details of a specific proposal from the DAO.

- `proposalId`: The ID of the proposal to fetch.

Returns a promise that resolves to the details of the proposal.

### `getAllProposals()`

Retrieves all proposals from the DAO.

Returns a promise that resolves to an array of all proposals.

### `getDAOBalance()`

Retrieves the balance of the DAO.

Returns a promise that resolves to the balance of the DAO.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
