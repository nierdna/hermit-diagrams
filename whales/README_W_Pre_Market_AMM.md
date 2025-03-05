# W-Pre-market AMM System

This repository contains PlantUML diagrams for the W-Pre-market AMM (Automated Market Maker) system, a specialized AMM designed for pre-market tokens.

## Overview

The W-Pre-market AMM is a system that enables trading of pre-market tokens before they are officially launched. It uses a specialized bonding curve formula to determine the price of tokens within a predefined price range (Pa to Pb).

### Key Features

- **Price Range Bounded Trading**: Trading occurs within a predefined price range (Pa to Pb)
- **Specialized Bonding Curve**: Uses mathematical formulas to determine token prices
- **Liquidity Provision**: LP providers can add liquidity with base tokens and receive LP tokens
- **Token Minting**: The system mints w-token when liquidity is added
- **Trading**: Traders can buy and sell w-token using base tokens

## Mathematical Formulas

The system uses the following key formulas:

### Liquidity (L)
```
L = x / (1/√Pa - 1/√Pb)
```
Where:
- x: Amount of base tokens
- Pa: Minimum price of pre-token
- Pb: Maximum price of pre-token

### Token Amounts at Price P
```
x = L · (1/√P - 1/√Pb)
y = L · (√P - √Pa)
```
Where:
- x: Amount of base tokens
- y: Amount of w-token
- P: Current price
- L: Liquidity constant

### General Formula for w-token Amount
```
y = x · (√Pb - √Pa) / (1/√Pa - 1/√Pb)
```
This formula is used when LP providers add liquidity to calculate how many w-token should be minted.

## Diagrams

This repository contains the following PlantUML diagrams:

1. **Sequence Diagram** (`w_pre_market_amm.wsd`): Shows the interactions between users and the system components
2. **Component Diagram** (`w_pre_market_amm_component.wsd`): Illustrates the system architecture and component relationships
3. **Class Diagram** (`w_pre_market_amm_class.wsd`): Displays the data structures and their relationships
4. **State Diagram** (`w_pre_market_amm_state.wsd`): Shows the different states of the system and transitions between them

## How to Use

1. Install PlantUML: https://plantuml.com/starting
2. Open the `.wsd` files with a PlantUML compatible viewer
3. Generate diagrams using the PlantUML command line or plugins

## System Components

- **AMM Core**: Central component that coordinates all operations
- **Price Calculator**: Implements the bonding curve formulas
- **Token Minter**: Creates new w-token when liquidity is added
- **Liquidity Manager**: Manages the liquidity pool
- **Swap Engine**: Handles token swaps
- **Liquidity Pool**: Stores base tokens and w-token

## User Types

1. **LP Provider**: Provides liquidity with base tokens and defines price range (Pa to Pb)
2. **Trader**: Trades base tokens for w-token or vice versa

## Workflow

### LP Provider Workflow
1. LP provider adds base tokens (e.g., ETH, USDC) with parameters Pa and Pb
2. System calculates the amount of w-token to mint using the formula
3. System mints w-token and adds both tokens to the liquidity pool
4. LP provider receives LP tokens representing their share of the pool

### Trader Workflow
1. Trader sends base tokens to buy w-token (or vice versa)
2. System calculates the output amount based on the bonding curve formula
3. System exchanges the tokens and sends the output to the trader
4. Price adjusts according to the bonding curve formula

## Implementation Notes

- The system ensures that the price always stays within the Pa to Pb range
- The bonding curve formula creates a predictable price curve
- LP providers can remove their liquidity at any time by burning their LP tokens
- The system can support multiple token pairs with different price ranges 