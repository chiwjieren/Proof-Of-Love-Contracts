# Proof of Love 💝

A decentralized application that allows couples to prove their commitment through token locking and earn NFTs + rewards over time.

## 🌟 Problem Statement

[Insert compelling image showing the problem]

In today's digital age, couples want to:
- Demonstrate their commitment in meaningful ways
- Have tangible proof of relationship milestones
- Be rewarded for staying together
- Have their love story recorded on the blockchain

## 💡 Solution

<img width="1825" height="711" alt="Screenshot 2025-10-21 170626" src="https://github.com/user-attachments/assets/bd823083-12ac-40aa-b77f-0bace199d023" />


Proof of Love is a Web3 dApp that enables couples to:
1. Lock tokens together as a symbol of commitment
2. Earn unique NFTs at relationship milestones (1, 2, and 3 years)
3. Receive token rewards through airdrops based on their commitment duration
4. Have their love story permanently recorded on the blockchain

## 🖼️ Gallery

[Insert screenshots/GIFs of the application]

## 🛠️ Technology Stack

- **Frontend**: NextJS, RainbowKit, Wagmi, TypeScript
- **Smart Contracts**: Solidity, Hardhat
- **Design**: TailwindCSS, daisyUI
- **Testing**: Hardhat Test Suite
- **Deployment**: Vercel (Frontend), IPFS (NFT Metadata)

## 🔗 Smart Contracts

### Core Contracts
1. **STAYToken (ERC20)**
   - Custom token for commitment locking
   - Exchange rate: 1 ETH = 1000 STAY
   - Buyable with ETH

2. **LoveVault**
   - Manages token locking mechanism
   - Handles commitment periods
   - Tracks NFT eligibility
   - Key durations:
     - Join timelock: Partner must join within this period
     - Lock duration: Total commitment period
     - NFT tiers: 1 year (Bronze), 2 years (Silver), 3 years (Gold)

3. **StillTogetherNFT (ERC721)**
   - Represents relationship milestones
   - Three tiers with unique artwork
   - Minted upon reaching duration milestones

4. **AirdropVault**
   - Manages token rewards for NFT holders
   - Different reward rates per tier:
     - Bronze: 10% of available tokens
     - Silver: 20% of available tokens
     - Gold: 30% of available tokens

## 🎮 Demo Flow (Using Scaffold-ETH Debug Page)

1. **Initial Setup**
   - Visit http://localhost:3000/debug
   - Connect MetaMask to Hardhat Network (http://localhost:8545)
   - Have two accounts ready (Partner 1 & 2)

2. **Getting STAY Tokens**
   - Go to `STAYToken` contract
   - Use `buyWithEth` function (send 1 ETH for 1000 STAY)
   - Verify balance with `balanceOf`
   - Current exchange rate: 1 ETH = 1000 STAY (check with `exchangeRate`)

3. **Creating a Love Vault**
   Partner 1:
   - Go to `STAYToken` → `approve` LoveVault to spend tokens
   - Go to `LoveVault` → `createVault`
     - Enter Partner 2's address
     - Enter amount of STAY tokens to lock

   Partner 2:
   - Switch to Partner 2's account
   - Go to `STAYToken` → `approve` LoveVault
   - Go to `LoveVault` → `deposit`

4. **Checking Vault Status**
   - Use `LoveVault.vaults` with either partner's address
   - Check:
     - `isActive`: Should be true
     - `partner1Deposited` & `partner2Deposited`: Both true
     - `lockStartTime`: When commitment began

5. **Claiming NFTs**
   After respective periods:
   - Check eligibility: `LoveVault.isEligibleForNFT`
   - Go to `StillTogetherNFT` → `mintNFT`
   - Verify with `balanceOf`
   - View NFT URI with `tokenURI`

6. **Claiming Airdrops**
   With NFT:
   - Go to `AirdropVault` → `claimAirdrop`
   - Enter your NFT's tokenId
   - Check STAY balance increase

## 🚀 Getting Started

1. Clone the repository
2. Install dependencies: `yarn install`
3. Start local chain: `yarn chain`
4. Deploy contracts: `yarn deploy`
5. Start frontend: `yarn start`
6. Visit http://localhost:3000

## 🧪 Testing

Run the comprehensive test suite:
```bash
cd packages/hardhat
yarn test
```

Tests cover:
- Token purchasing and transfers
- Vault creation and management
- NFT minting and tier logic
- Airdrop distribution
- Error cases and security

## 📝 License

MIT

## 🤝 Contributing

[Guidelines for contributing to the project]

## 🙏 Acknowledgments

Built with [Scaffold-ETH 2](https://github.com/scaffold-eth/scaffold-eth-2)
