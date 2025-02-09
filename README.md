## Placeholder-avs-contract 

**Smart contracts to implement  AVS (Actively Validated Service) that verifies sentiment analysis of user feedback.**


## Contract Events

### NewTaskCreated
```solidity
event NewTaskCreated(uint32 indexed taskIndex, Task task);
```
Tracks when a user submits new feedback to the system. Every feedback submission gets a unique ID (taskIndex) and includes:

- The user's written comment
- A rating (1-5)
- The block number when submitted

Example:
```json
{
    "taskIndex": 1,
    "task": {
        "comment": "Great service!",
        "rating": 5,
        "taskCreatedBlock": 21808375
    }
}
```

### TaskResponded
```solidity
event TaskResponded(
    uint32 indexed taskIndex,
    Task task,
    string sentiment,
    address operator
);
```
Tracks when an operator analyzes a piece of feedback. Records:

- Which feedback they analyzed (taskIndex)
- The original feedback details
- Their sentiment analysis result (positive/negative/neutral)
- The operator's address

Example:
```json
{
    "taskIndex": 1,
    "task": {
        "comment": "Great service!",
        "rating": 5,
        "taskCreatedBlock": 21808375
    },
    "sentiment": "POSITIVE",
    "operator": "0x70997970C51812dc3A010C7d01b50e0d17dc79C8"
}
```

## Installations
```shell
forge install Layr-Labs/eigenlayer-middleware@mainnet
```

## Deployment
```shell
 ### Terminal 1 (Run the anvil node)
anvil --chain-id 31337 --fork-url https://eth-mainnet.g.alchemy.com/v2/key
```
```shell
### Terminal 2 (Script to deploy the contract on Eigen Layer and AVS)
forge script script/DeployManager.sol --rpc-url http://127.0.0.1:8545 --broadcast


##### anvil-hardhat
✅  [Success] Hash: 0xb4f1a071ef6ff6e6cea75d66eb62b88424af582d226a833c77eed019039866b5
Contract Address: 0xe3EF345391654121f385679613Cea79A692C2Dd8
Block: 21808375

##### anvil-hardhat
✅  [Success] Hash: 0x75b40857f7eabbc418480bf390d8820e67e50d7cc8bbd88440cb222609c5fb29
Block: 21808376


##### anvil-hardhat
✅  [Success] Hash: 0x55d17bf3de917cea3f91d631d96c2bd662d9790f85eadad5459db86fbb2020f6
Block: 21808377
Paid: 0.00007202453545676 ETH (118142 gas * 0.60964378 gwei) ```                                                                                                     
```

