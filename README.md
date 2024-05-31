# ETH-AVAX-Module-3
# MyToken ERC20 Token

## Overview

MyToken is an ERC20 token implemented in Solidity using the OpenZeppelin library. This token includes minting and burning functionalities. The contract owner can mint new tokens, and any user can burn their tokens.

## Prerequisites

- Node.js and npm installed (if using HardHat for local deployment).
- A web browser with MetaMask installed for deploying on a testnet or mainnet.
- Basic understanding of Solidity and Ethereum smart contracts.

## Contract Details

- **Token Name:** MyToken
- **Token Symbol:** MTK
- **Initial Supply:** 1,000,000 MTK minted to the deployer
- **Functions:**
  - `mint(address to, uint256 amount)`: Mints new tokens to the specified address. Only the contract owner can call this function.
  - `burn(uint256 amount)`: Burns the specified amount of tokens from the caller's balance.

## Getting Started

### Using Remix

1. **Open Remix:**
   - Go to [Remix](https://remix.ethereum.org/).

2. **Create a New File:**
   - In the file explorer, click on the "+" icon to create a new file.
   - Name the file `MyToken.sol`.

3. **Add the Contract Code:**
   - Copy and paste the following Solidity code into the new file:

     ```solidity
     // SPDX-License-Identifier: MIT
     pragma solidity ^0.8.0;

     import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.4.0/contracts/token/ERC20/ERC20.sol";
     import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.4.0/contracts/access/Ownable.sol";

     contract MyToken is ERC20, Ownable {
         constructor() ERC20("MyToken", "MTK") {
             // Mint an initial supply of 1,000,000 tokens to the deployer
             _mint(msg.sender, 1000000 * 10 ** decimals());
         }

         // Function for the owner to mint new tokens
         function mint(address to, uint256 amount) public onlyOwner {
             _mint(to, amount);
         }

         // Function for any user to burn their tokens
         function burn(uint256 amount) public {
             _burn(msg.sender, amount);
         }
     }
     ```

4. **Compile the Contract:**
   - Go to the "Solidity Compiler" tab on the left sidebar.
   - Ensure the compiler version is set to `0.8.0` or higher.
   - Click "Compile MyToken.sol".

5. **Deploy the Contract:**
   - Go to the "Deploy & Run Transactions" tab.
   - Select the environment (e.g., JavaScript VM for local testing, Injected Web3 for deploying to a testnet/mainnet using MetaMask).
   - Ensure your contract `MyToken` is selected in the "Contract" dropdown.
   - Click "Deploy".

6. **Interact with the Deployed Contract:**
   - **Mint Tokens:**
     - In the deployed contract section, expand the `mint` function.
     - Enter the recipient address and the amount of tokens to mint.
     - Click "transact".
   - **Burn Tokens:**
     - Expand the `burn` function.
     - Enter the amount of tokens to burn.
     - Click "transact".
   - **Transfer Tokens:**
     - Use the standard `transfer` function inherited from `ERC20`.
     - Enter the recipient address and the amount of tokens to transfer.
     - Click "transact".



## License

This project is licensed under the MIT License.
