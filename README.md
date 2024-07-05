Here's the updated README file for your `WutherToken` project, incorporating additional information:

---

# WutherToken (WUWA)

WutherToken (symbol: WUWA) is an ERC20 token built using Solidity and OpenZeppelin libraries. This token contract allows the contract owner to mint tokens to specified addresses and any user to burn and transfer tokens.

## Description

This Solidity contract, named `WutherToken`, stores details about a custom token named "Wuther" with the abbreviation "WUWA". The contract allows for minting new tokens to increase the total supply and burning tokens to decrease the total supply. Each account's balance is tracked using the ERC20 standard provided by OpenZeppelin.

## Getting Started

### Executing Program

To run this program, you can use [Remix](https://remix.ethereum.org/), an online Solidity IDE.

#### Steps

1. **Open Remix**: Go to the [Remix website](https://remix.ethereum.org/).
2. **Create a New File**: Click on the "+" icon in the left-hand sidebar. Save the file with a `.sol` extension (e.g., `WutherToken.sol`).
3. **Copy and Paste Code**: Copy and paste the following code into the new file:

    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.0;

    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

    contract WutherToken is ERC20 {
        address public owner;

        constructor() ERC20("Wuther", "WUWA") {
            owner = msg.sender; // Set the contract deployer as the owner
        }

        modifier onlyOwner() {
            require(msg.sender == owner, "Only the owner can call this function");
            _;
        }

        function mint(address to, uint256 amount) public onlyOwner {
            _mint(to, amount);
        }

        function burn(uint256 amount) public {
            _burn(msg.sender, amount);
        }

        function transfer(address recipient, uint256 amount) public override returns (bool) {
            require(amount > 0, "Transfer amount must be greater than zero");
            return super.transfer(recipient, amount);
        }
    }
    ```

4. **Compile the Code**:
    - Click on the "Solidity Compiler" tab in the left-hand sidebar.
    - Make sure the "Compiler" option is set to a compatible version (e.g., `0.8.x`).
    - Click on the "Compile WutherToken.sol" button.

5. **Deploy the Contract**:
    - Click on the "Deploy & Run Transactions" tab in the left-hand sidebar.
    - Select the "WutherToken" contract from the dropdown menu.
    - Click on the "Deploy" button.

6. **Interact with the Contract**:
    - After deployment, click on the "WutherToken" contract in the left-hand sidebar.
    - You can now call the `mint`, `burn`, and `transfer` functions to manage the token supply.
        - **Mint Tokens**: Call `mint(address to, uint256 amount)` with the desired address and token amount. Only the owner can call this function.
        - **Burn Tokens**: Call `burn(uint256 amount)` to burn the specified amount of tokens from the caller's balance.
        - **Transfer Tokens**: Call `transfer(address recipient, uint256 amount)` to transfer the specified amount of tokens to the recipient address. The transfer amount must be greater than zero.

## Features

- **Token Details**: ERC20 standard token with name "Wuther" and symbol "WUWA".
- **Minting**: Function to mint new tokens, increasing the total supply and the balance of the specified address. Only the owner can mint tokens.
- **Burning**: Function to burn tokens, decreasing the total supply and the balance of the caller.
- **Transferring**: Function to transfer tokens between addresses, ensuring the transfer amount is greater than zero.

## Authors

- **Your Name**
    - Twitter: [@Mhistwy](https://twitter.com/nchlsangls)
