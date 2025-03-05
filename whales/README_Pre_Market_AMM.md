# W-Pre-market AMM System

This repository contains PlantUML diagrams for the W-Pre-market AMM (Automated Market Maker) system, a specialized AMM designed for pre-market tokens.

## Overview

The W-Pre-market AMM is a system that enables trading of pre-market tokens before they are officially launched. It uses a specialized bonding curve formula to determine the price of tokens within a predefined price range (Pa to Pb).

### Key Features

- **Price Range Bounded Trading**: Trading occurs within a predefined price range (Pa to Pb)
- **Specialized Bonding Curve**: Uses mathematical formulas to determine token prices
- **Liquidity Provision**: LP providers can add liquidity with base token and receive LP tokens
- **Token Minting**: The system mints pre-token when liquidity is added
- **Trading**: Traders can buy and sell pre-token using base token
- **Collateral Requirement**: LP providers must provide additional base token as collateral
- **Settlement Phase**: After TGE, LP providers can withdraw liquidity by providing real tokens
- **Token Swapping**: Traders can swap pre-token for real token at a 1:1 ratio after TGE

## Mathematical Formulas

The system uses the following key formulas:

### Liquidity (L)
```
L = x / (1/√Pa - 1/√Pb)
```
Where:
- x: Amount of base token
- Pa: Minimum price of pre-token
- Pb: Maximum price of pre-token

### Token Amounts at Price P
```
x = L · (1/√P - 1/√Pb)
y = L · (√P - √Pa)
```
Where:
- x: Amount of base token
- y: Amount of pre-token
- P: Current price
- L: Liquidity constant

### General Formula for pre-token Amount
```
y = x · (√Pb - √Pa) / (1/√Pa - 1/√Pb)
```
This formula is used when LP providers add liquidity to calculate how many pre-token should be minted.

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
- **Token Minter**: Creates new pre-token when liquidity is added
- **Liquidity Manager**: Manages the liquidity pool
- **Swap Engine**: Handles token swaps
- **Liquidity Pool**: Stores base token and pre-token
- **Settlement Manager**: Handles the settlement phase after TGE
- **LP Position Trackers**: Tracks LP positions, collateral, and initial pre-token amounts

## User Types

1. **LP Provider**: Provides liquidity with base token and defines price range (Pa to Pb)
2. **Trader**: Trades base token for pre-token or vice versa

## Workflow

### LP Provider Workflow
1. LP provider adds base token (e.g., ETH, USDC) with parameters Pa and Pb
2. System calculates the amount of pre-token to mint using the formula
3. System mints pre-token and adds both tokens to the liquidity pool
4. LP provider adds an equal amount of base token as collateral
5. System records the initial pre-token amount minted for the LP position
6. LP provider receives LP tokens representing their share of the pool

### Trader Workflow
1. Trader sends base token to buy pre-token (or vice versa)
2. System calculates the output amount based on the bonding curve formula
3. System exchanges the tokens and sends the output to the trader
4. Price adjusts according to the bonding curve formula

### Settlement Phase Workflow (After TGE)
1. System enters settlement phase after token generation event (TGE)
2. Real tokens are added to the system

#### LP Provider Settlement Workflow
1. LP provider requests to withdraw liquidity
2. System calculates required token amount = initial pre-token amount - current pre-token balance
3. LP provider provides the required token amount
4. System returns the LP provider's base token and collateral

#### Trader Settlement Workflow
1. Trader with pre-token can swap them for real tokens at a 1:1 ratio
2. System burns the pre-token and transfers real tokens to the trader

## Implementation Notes

- The system ensures that the price always stays within the Pa to Pb range
- The bonding curve formula creates a predictable price curve
- LP providers must provide collateral when adding liquidity
- LP providers can only withdraw liquidity in settlement phase by providing real tokens
- The amount of real tokens required is equal to the difference between initial pre-token amount and current pre-token balance
- Traders can swap pre-token for real token at a 1:1 ratio in settlement phase
- The system can support multiple token pairs with different price ranges 