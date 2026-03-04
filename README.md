# 🗳️ E-Voting System — Ethereum + Vue.js

A decentralized electronic voting application built on the Ethereum blockchain. Voters authenticate using their **Turkish National ID (TC Kimlik)**, cast a single vote for a candidate, and can immediately view real-time vote statistics. An admin panel allows authorized users to add or remove candidates before/during the election.

---

## ✨ Features

- **Turkish National ID validation** — only valid TC Kimlik numbers are accepted via `turkish-id-checker`
- **One-voter-one-vote enforcement** — the smart contract tracks voter IDs on-chain to prevent double voting
- **Candidate management** — admin can add candidates (name + image URL) or remove those with zero votes
- **Live vote statistics** — a donut chart displays real-time vote counts after voting
- **MetaMask integration** — transactions are signed through the user's MetaMask wallet
- **Reactive Web3 UI** — powered by Drizzle for automatic contract state synchronization

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Smart Contract | Solidity 0.8.11, Truffle |
| Frontend | Vue.js 2, Vue Router, Vuex |
| UI Components | Buefy, Bulma |
| Charts | Chart.js, vue-chartjs |
| Web3 / Blockchain | Drizzle (`@drizzle/vue-plugin`), MetaMask |
| Local Blockchain | Ganache (port 7545) |
| ID Validation | `turkish-id-checker` |

---

## 📋 Prerequisites

- [Node.js](https://nodejs.org/) (v14+)
- [Truffle](https://trufflesuite.com/) — `npm install -g truffle`
- [Ganache](https://trufflesuite.com/ganache/) (desktop app or `ganache-cli`)
- [MetaMask](https://metamask.io/) browser extension

---

## 🚀 Getting Started

### 1. Install dependencies
```bash
npm install
```

### 2. Start a local Ethereum node with Ganache
Open Ganache and start a workspace on **port 7545**, or run:
```bash
npx ganache-cli -p 7545
```

### 3. Deploy the smart contract
```bash
truffle migrate
# For a clean re-deploy:
truffle migrate --reset
```

### 4. Connect MetaMask
- Set the MetaMask network to **Localhost 7545**
- Import one of the Ganache accounts using its private key

### 5. Run the development server
```bash
npm run serve
```
Open [http://localhost:8080](http://localhost:8080) in your browser.

---

## 🗂️ Application Flow

```
Home (enter TC Kimlik ID)
  └─▶ Verify (OTP / verification code)
        └─▶ Vote (pick a candidate, confirm via MetaMask)
              └─▶ Result (thank-you page + live donut chart)

Admin Login ─▶ Admin Panel (add / remove candidates)
```

---

## 📄 Smart Contract — `Election.sol`

Deployed to the local Ganache network. Key functions:

| Function | Description |
|---|---|
| `addCandidate(name, image)` | Add a new candidate |
| `deleteCandidate(id)` | Remove a candidate (only if 0 votes) |
| `vote(candidateId, voterId)` | Cast a vote; reverts if voter already voted |
| `getCandidates()` | Return all candidates as an array |
| `isAdmin(username, password)` | Validate admin credentials (stored on-chain) |

> **Note:** Three demo candidates (McDonald's, KFC, Burger King) are added in the constructor.

---

## 🏗️ Other Build Commands

```bash
# Production build
npm run build

# Lint & fix source files
npm run lint
```

See the [Vue CLI Configuration Reference](https://cli.vuejs.org/config/) for advanced options.

---

## 🏷️ Suggested GitHub Topics

Add these topics to the repository's **About** section on GitHub:

```
blockchain ethereum solidity smart-contracts vue vuejs vue2
web3 dapp truffle ganache metamask drizzle e-voting buefy
```
