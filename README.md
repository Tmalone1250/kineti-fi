# KinetiFi: Autonomous DeFi Optimization (Base Mainnet)

**KinetiFi** is a next-generation decentralized finance (DeFi) portfolio optimizer that bridges AI-driven market intelligence with non-custodial on-chain execution. It enables users to deploy a personal **KinetiFi AI Agent** that scans the **Base Mainnet** ecosystem for yield opportunities and registers "Intents" to autonomously improve portfolio performance.

---

## 📱 Screenshots

|                     **Portfolio Intelligence Overview**                     |                      **AI Agent Strategy Chat**                       |
| :-------------------------------------------------------------------------: | :-------------------------------------------------------------------: |
| ![Portfolio Overview](./public/assets/Screenshot%202026-04-03%20121239.png) |  ![Agent Chat](./public/assets/Screenshot%202026-04-03%20121352.png)  |
|        _Real-time net worth tracking and multi-chain distribution._         | _Large Language Model (LLM) agent generating strategic yield theses._ |

|                       **DeFi Position Discovery**                       |                     **Yield Upgrade Opportunities**                     |
| :---------------------------------------------------------------------: | :---------------------------------------------------------------------: |
| ![DeFi Positions](./public/assets/Screenshot%202026-04-03%20121336.png) | ![Yield Upgrades](./public/assets/Screenshot%202026-04-03%20121409.png) |
|   _Automated scanning of Uniswap V3, Aerodrome, and Beefy positions._   |     _AI-identified upgrades with highlighted APY boost potential._      |

|                     **Intelligence Strategy Feed**                     |                       **Unified Transaction History**                        |
| :--------------------------------------------------------------------: | :--------------------------------------------------------------------------: |
| ![Strategy Feed](./public/assets/Screenshot%202026-04-03%20121324.png) | ![Transaction History](./public/assets/Screenshot%202026-04-03%20121424.png) |
|   _Live audit logs of agent discovery and portfolio optimizations._    |         _Consolidated history of EOA and Smart Account operations._          |

---

## 🏗 System Architecture

KinetiFi is composed of three primary layers working in orchestration on **Base Mainnet (Chain ID 8453)**:

### 1. Smart Contract Layer (Mainnet)

The foundation of KinetiFi is a secure, intent-based account abstraction framework:

- **KinetiFiAgentNFT**: An ERC-721 token representing your unique AI Agent identity. Owning this NFT is required to register intents.
- **KinetiFiAccount**: An advanced smart account (ERC-4337 style) supporting local session modules.
- **IntentRegistry**: A central logic contract where Agents log signed optimization intents (Target Vault, Min APY, CallData, Deadline).
- **KinetiFiSessionModule**: Manages ephemeral authorizations. Users grant the Agent a session key, allowing it to register intents without a manual signature for every discovery.

### 2. On-Chain Discovery Engine

Replacing fragile legacy APIs, KinetiFi uses a robust, event-based discovery system:

- **Gauge Scanning**: Automatically discovers staked NFT positions by scanning Aerodrome Slipstream Gauge logs.
- **Resilient Multicall**: Uses isolated multicall batches with `allowFailure: true` to prevent single ABI decode errors from poisoning the entire portfolio view.
- **Deterministic Valuation**: Employs a tick-based valuation pipeline for Uniswap V3 and Aerodrome Slipstream positions, fetching real-time `slot0` data from concentrated liquidity pools.

### 3. Frontend Dashboard (React/Vite)

A premium interface built for transparency and control:

- **Tech Stack**: React 18, Vite, Framer Motion, Tailwind CSS, Wagmi v2, Reown AppKit, TanStack Query.
- **Performance Optimized**: Custom build pipeline with 4GB Node.js memory allocation to handle complex DeFi dependency trees.

---

## 🛡 Security & Resilience

- **Isolated Multicall**: Every position discovery call is isolated. If one protocol (e.g., a specific Aerodrome Gauge) fails to decode, the rest of your portfolio still displays correctly.
- **Tick-Based Pricing**: We don't rely on external price APIs. Valuation is derived directly from the `sqrtPriceX96` of the underlying liquidity pool.
- **Non-Custodial**: All intents are registered through your Smart Account and require a valid Session Key (SessionModule) or your EOA signature.

---

## 📜 Verified Contract Registry (Base Mainnet)

| Contract              | Address                                      |
| :-------------------- | :------------------------------------------- |
| **AgentNFT**          | `0x5eCeC712ab5a1DFfaeab0086f04124574D5913Ec` |
| **IntentRegistry**    | `0x142f2c70fb19a46b2c71052cf0f5c72210bd737b` |
| **EntryPoint (v0.7)** | `0x0000000071727De22E5E9d8BAf0edAc6f37da032` |
| **Factory**           | `0x52bdc8eb286b279aab769fc3ec433cc8df61ce43` |
| **SessionModule**     | `0x94044d6cdf49f1278f4a097776f40dd6e5943820` |
| **Aerodrome NFPM**    | `0xa990C6a764B73BF43Cee5BB40339C3322fb9D55f` |

---

## 🛠 Project Structure

- `src/hooks/useDeFiPositions`: The core orchestrator for discovery and valuation.
- `src/lib/discovery/gaugeDiscovery.ts`: Logic for scanning Gauge events.
- `src/constants/contracts.ts`: Verified ABIs and Mainnet addresses.
- `src/wagmi.ts`: Wallet connection and AppKit configuration.

---

_Built with ❤️ for the KinetiFi Ecosystem. AI is the standard. Optimization is the goal._
