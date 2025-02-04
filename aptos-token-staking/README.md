
# Build an Aptos DApp: Token Staking Template

Empower your blockchain application with a versatile token staking solution. This template offers a ready-to-use, customizable user interface and is optimized for live deployment.

## Comprehensive Documentation

For setup instructions and further details, please refer to the [Token Staking Dapp Template Docs](#).

## Template Highlights

-   **Flexible Asset Selection:**  
    The deployer has the ability to choose any fungible asset for both staking and reward distribution.
    
-   **Reward Scheduling:**  
    The designated reward creator can establish a reward plan based on a specified reward per second (RPS) and a defined duration (in seconds).
    
    > _Note:_ Currently, the system supports only one reward schedule. To implement multiple schedules, deploy separate staking pools.
    
-   **User Engagement:**  
    Users can stake their assets and claim rewards in line with the configured schedule.
    

## How Rewards Are Calculated

1.  **Update the Reward Index:**  
    The reward index is computed with the formula below, representing the incremental reward per staked asset:
    
    bash
    
    CopyEdit
    
    `reward index = old_index + (current_ts - last_update_ts) * rps / total_stake` 
    
2.  **Determine User Rewards:**  
    Each user’s reward is calculated as:
    
    bash
    
    CopyEdit
    
    `reward = user_stake * (reward_index - user_index_at_last_claim)` 
    

## Limitations

For simplicity, this template does not feature a mechanism to reclaim unclaimed rewards after the reward schedule expires. One possible approach is to transfer any remaining rewards post-duration; however, this might restrict users with pending rewards from claiming them.

## Core Features

-   **Token Staking Interface:**  
    A dedicated page for staking fungible assets.
    
-   **Reward Claim Component:**  
    A user-friendly component that allows stakers to claim their rewards.
    
-   **Token Unstaking Module:**  
    A simple interface for users to withdraw their staked tokens.
    
-   **Incentivized Pool Creation:**  
    Enables an authorized creator to launch a rewards pool for a chosen fungible asset.
    

## Underlying Tools and Technologies

-   **React Framework:**  
    For building dynamic and interactive UIs.
    
-   **Vite:**  
    A fast development environment for modern web projects.
    
-   **shadcn/ui + Tailwind CSS:**  
    Provides modern, responsive design and styling.
    
-   **Aptos TS SDK & Aptos Wallet Adapter:**  
    These tools enable seamless integration with the Aptos blockchain.
    
-   **Node-based Move Commands:**  
    Facilitates the management of Move contracts within a Node environment.
    

### Available Move Commands

The template leverages the [aptos-cli npm package](https://github.com/aptos-labs/aptos-cli) to integrate Aptos CLI into a Node setup. Key commands include:

-   `npm run move:publish` — Publishes the Move contract.
-   `npm run move:test` — Executes unit tests for Move contracts.
-   `npm run move:compile` — Compiles the Move contract.
-   `npm run move:upgrade` — Upgrades the existing Move contract.
-   `npm run deploy` — Deploys the DApp to Vercel.

For additional commands, run `npx aptos` to view the complete list.
