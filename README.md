# MyToken Contract

This Solidity contract implements a basic ERC20-like token with functionalities to initialize the token, mint new tokens, and burn existing tokens.

## Requirements
1. Public variables to store the details about the coin (Token Name, Token Abbreviation, Total Supply).
2. A mapping of addresses to balances (`address => uint`).
3. A `mint` function that increases the total supply and the balance of the specified address.
4. A `burn` function that decreases the total supply and the balance of the specified address, with a check to ensure the balance is sufficient.

## Contract Description

### State Variables
- `string public name`: The name of the token.
- `string public symbol`: The abbreviation of the token.
- `uint256 public totalSupply`: The total supply of the token.
- `mapping(address => uint256) public balances`: A mapping to store the balance of each address.

### Constructor
- `constructor(string memory _name, string memory _symbol, uint256 _totalSupply)`: Initializes the contract with the given name, symbol, and total supply. Assigns the total supply to the deployer's balance.

### Functions
- `function mint(address _address, uint256 _value) public`: Mints new tokens and assigns them to the specified address. Increases the total supply by `_value` and adds `_value` tokens to the balance of `_address`.

- `function burn(address _address, uint256 _value) public`: Burns (destroys) tokens from the specified address. Checks if the balance of `_address` is greater than or equal to `_value`, and if so, reduces the total supply by `_value` and deducts `_value` tokens from the balance of `_address`.

## Deployment

1. Open Remix (https://remix.ethereum.org/)
2. Create a new file and paste the contract code.
3. Go to the "Solidity Compiler" tab and compile the contract.
4. Go to the "Deploy & Run Transactions" tab.
5. Select your contract (`MyToken`) from the dropdown.
6. Enter the values for `_name`, `_symbol`, and `_totalSupply` in the "Deploy" section.
7. Click on "Deploy" to deploy the contract.

## Usage

### Mint Tokens
To mint tokens, call the `mint` function with the address and the amount of tokens to mint.

Example:
```solidity
MyToken.mint("0xYourAddress", 1000);





To burn tokens, call the burn function with the address and the amount of tokens to burn
MyToken.burn("0xYourAddress", 500);


To check the balance of an address, call the balances mapping with the address
uint256 balance = MyToken.balances("0xYourAddress");




Example Demo
// Deploy the contract with initial values
MyToken token = new MyToken("MyToken", "MTK", 1000000);

// Check initial balance of deployer
uint256 initialBalance = token.balances(msg.sender); // Should be 1000000

// Mint 1000 tokens to an address
token.mint("0x123...", 1000);

// Check the balance after minting
uint256 newBalance = token.balances("0x123..."); // Should be 1000

// Burn 500 tokens from the same address
token.burn("0x123...", 500);

// Check the balance after burning
uint256 finalBalance = token.balances("0x123..."); // Should be 500
