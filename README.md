## Mttok (MTT) Token Contract
## Overview
Mttok (MTT) is an ERC-20 compliant token with additional features, including burn functionality and an access control mechanism. The token contract is built on top of the OpenZeppelin library, which provides widely-used and audited implementations of ERC-20 tokens.

## Contract Details
The Mttok contract extends the following OpenZeppelin contracts:

#### ERC20:
This is the base ERC-20 token contract, providing standard functionalities such as transferring tokens, checking balances, and managing allowances.

#### ERC20Burnable:
This extension allows users to burn (destroy) their own tokens, reducing the total supply.

#### AccessControl:
This extension implements a role-based access control mechanism, allowing the contract owner to grant specific roles to designated addresses. In this contract, we define the role of a "Minter" who has the ability to mint new tokens.

#### ERC20Permit: 
This extension adds the EIP-2612 permit function, enabling users to approve token transfers with a single call, which is useful for integrating with certain DeFi protocols and applications.

## Roles
The contract defines one custom role:

## MINTER_ROLE:
This role is used to designate addresses that are allowed to mint new tokens.
## Constructor
The contract constructor is called once when deploying the contract to the blockchain. The constructor initializes the token with the following parameters:

name: The name of the token (e.g., "mttok").
symbol: The token symbol (e.g., "MTT").
permitName: The name used for the EIP-2612 permit function (in this case, "mttok").
## Initialization
The contract's constructor grants the DEFAULT_ADMIN_ROLE and the MINTER_ROLE to the deployer of the contract (i.e., the contract creator). The DEFAULT_ADMIN_ROLE is a built-in role in the AccessControl contract and is given the highest privileges for the contract.

## Minting
Only addresses with the MINTER_ROLE can mint new tokens. The mint function is restricted using the onlyRole modifier, which ensures that only addresses with the required role can call the function. The mint function allows the contract owner (who has the MINTER_ROLE) to create and distribute new tokens to other addresses.

## Permit
The contract supports the EIP-2612 permit function, which allows users to approve token transfers without the need for multiple transaction calls. This feature is optional and can be useful when interacting with certain DeFi platforms or decentralized applications.

## License
The contract is released under the MIT License, which is a permissive open-source license allowing for reuse and distribution of the code. You can find the license text at the top of the Solidity file.

