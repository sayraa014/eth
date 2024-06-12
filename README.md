# STRATS Token Contract

The STRATS Token contract is a straightforward implementation of a custom token on the Ethereum blockchain using Solidity. This contract allows you to mint and burn tokens, keeping track of token balances for various addresses.

## Contract Summary

### Public Variables

- **tokenName**: Holds the name of the token, which is "STRATS".
- **tokenAbbrv**: Stores the token's abbreviation, "STRT".
- **totalSupply**: Represents the total number of tokens in circulation, initially set to 0.

### Balance Mapping

- **balances**: A mapping that links addresses to their respective token balances.

## Core Functions

### Minting Tokens

The `mint` function allows the creation of new tokens. It takes an address and a value as parameters, increasing both the total token supply and the balance of the specified address.

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

### Burning Tokens
The `burn` function allows the destruction of tokens. It takes an address and a value as parameters, decreasing both the total token supply and the balance of the specified address. It ensures that the address has enough tokens before proceeding with the burn.

```solidity
function burn(address _address, uint _value) public {
    if (balances[_address] >= _value) {
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
```

## Features
- Public Variables: The contract includes public variables for the token's name, abbreviation, and total supply.
- Balance Tracking: The contract maintains a mapping of addresses to token balances.
- Minting Functionality: Allows the creation of new tokens, increasing the total supply and the balance of a specified address.
- Burning Functionality: Enables the destruction of tokens, decreasing the total supply and the balance of a specified address with necessary checks.
