# MPCNode-airdrop
MPC node airdrop smart contract

# compile

## use solc

solcjs --abi --bin --output-dir build --evm-version byzantium --optimize --runs=200 contracts/*.sol

## use remix

<https://remix.ethereum.org/#optimize=true&evmVersion=null&version=soljson-v0.5.4+commit.9549d8ff.js&runs=200>

# interfaces

## query rewards

```javascript
rewards(address _user) returns (uint256)
````

## set rewards

require user has not setted rewards before, and the setting amount is not equal to 1

```javascript
struct RewardInfo {
    address user;
    uint256 amount; // 0: no reward, 1: claimed, others: reward amount
}
```

```javascript
setRewards(RewardInfo[] _infos) onlyOwner {
```

## claim rewards

require sender's rewards is greater than 1, and token balance of this contract is enough

```javascript
claim() returns (bool)
```
