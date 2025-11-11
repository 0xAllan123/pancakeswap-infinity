# Infinity Core

## Getting Started

### Prerequisites
- Foundry (forge)
- Node.js and Yarn

### Installation

Install project dependencies:

```bash
forge install
yarn install
```

### Running Tests

Execute the test suite with isolation to ensure test independence:

```bash
forge test --isolate
```

> **Note:** The `--isolate` flag is used to prevent test cross-contamination. See [PancakeSwap Infinity Core PR #35](https://github.com/pancakeswap/infinity-core/pull/35) for details.

## Dependency Management

Update all project dependencies:

```bash
forge update
```

## Deployment

### Configuration

Deployment scripts are located in the `/script` directory. Contract addresses are stored in `script/config`.

### Environment Variables

Before deploying, configure the following environment variables:

```bash
# Script configuration file
export SCRIPT_CONFIG=ethereum-sepolia

# RPC endpoint
export RPC_URL=https://your-rpc-url

# Private key (must be prefixed with 0x)
export PRIVATE_KEY=0x...

# Optional: Etherscan API key for contract verification
export ETHERSCAN_API_KEY=...
```

### Deployment Execution

Refer to the deployment script for the specific command. 

**Example:** Deploying the Vault contract using `script/01_DeployVault.s.sol`

```bash
forge script script/01_DeployVault.s.sol:DeployVaultScript -vvv \
    --rpc-url $RPC_URL \
    --broadcast \
    --slow
```

### Contract Verification

Contracts deployed with the CREATE3 method require separate verification.

**Example:** Verifying the Vault contract

```bash
forge verify-contract <address> Vault --watch --chain <chain_id>
```

See individual deployment scripts for specific verification commands.