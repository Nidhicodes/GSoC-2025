# Google Summer of Code 2025 - Final Project Report

**Contributor:** Nidhi Singh  
**Email:** nidhis@iitbhilai.ac.in  
**GitHub:** [Nidhicodes](https://github.com/Nidhicodes)  
**LinkedIn:** [Nidhi Singh](https://www.linkedin.com/in/nidhi-singh-376a171b8/)  
**Discord:** 0xcryptic  
**Organization:** [Australian Open Source Software Innovation and Education (AOSSIE)](https://aossie.org/)  
**Project Repository:** [Bountiful - Ergo Bounty Platform](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo) & [StablePay Merchant Dashboard](https://github.com/DjedAlliance/StablePay-MerchantDashboard)  
**Project Duration:** 350 Hours (Large Project, 22 Weeks)  
**Mentors:** Dr. Bruno Woltzenlogel Paleo, Aditya Bhattad and José Miguel Avellana  
**Project Demo Video Link:** [Demo Video](https://drive.google.com/file/d/1qwk6Az7m1QJcfZZVHPnqWYE0nzqgvbsO/view?usp=sharing)

---

## Executive Summary

During my Google Summer of Code 2025 journey with AOSSIE, I successfully worked on two groundbreaking blockchain projects that address critical challenges in decentralized finance and bounty management. This report details the comprehensive work done on **Bountiful** - a decentralized bounty platform built on the Ergo blockchain, and **StablePay Merchant Dashboard** - an enhanced cryptocurrency payment solution for merchants.

Both projects represent significant contributions to the blockchain ecosystem, implementing complex smart contract architectures using ErgoScript, modern web interfaces with Svelte and React, and solving real-world challenges in decentralized task fulfillment and crypto payments.

---

# Bountiful - Ergo Bounty Platform

## Project Overview

Bountiful is a comprehensive decentralized bounty platform built on the Ergo blockchain that transforms development funding through trust-based and competitive bounties. By leveraging smart contracts for secure escrow, the platform ensures funds are only released when problems are verifiably solved, eliminating intermediaries and centralized control.

### Key Innovation: Hybrid Trust Model

The platform implements a dual-track evaluation system:
- **Trusted Projects:** Creators can act as judges, reducing overhead and enabling faster resolution
- **Untrusted Projects:** Utilize independent judges selected through reputation-based mechanisms

### Core Features

- **Trustless Escrow:** Smart contracts lock funds and only release upon verified completion
- **Reputation System:** On-chain reputation tracking for judges based on historical performance
- **Dispute Resolution:** Comprehensive dispute mechanism for fair conflict resolution
- **Cryptographic Verification:** All judgments are cryptographically signed and verifiable
- **Token-Based Identity:** Judge profiles and reputation stored as blockchain tokens

---

## GitHub Repository

- **Main Repository:** [Bountiful-BountyPlatform-Ergo](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo)
- **Live Demo:** *Deployment in progress*

---

## Major Pull Requests & Contributions

### PR #8: Add Basic Bounty Creation and Wallet Integration  
**Status:** ✅ Merged  
**Link:** [Pull Request #8](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/8)  

**Description:**
This foundational PR established the core functionality of the platform:
- Implemented basic bounty creation workflow with form validation
- Integrated Nautilus wallet SDK for Ergo blockchain interactions
- Created bounty submission and storage mechanisms
- Added wallet connection state management
- Implemented basic UI components for bounty creation

**Technical Highlights:**
- Connected to Nautilus wallet using `@nautilus-js/sdk`
- Implemented transaction signing and submission flows
- Created type-safe bounty data structures

**Impact:** This PR laid the foundation for all subsequent bounty-related features.

---

### PR #11: Bounty Dashboard UI Improvements + Judge Address Metadata + Proposal Submission Form  
**Status:** ✅ Merged  
**Link:** [Pull Request #11](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/11)  

**Description:**
Significantly enhanced the bounty dashboard with comprehensive metadata display and proposal functionality:
- Added judge address display with truncation for better UX
- Implemented proposal count tracking per bounty
- Created proposal submission form for active bounties
- Improved bounty detail view with structured layouts
- Added current user detection for judge assignments

**Key Features:**
- **Judge Metadata:** Displays all assigned judges with user-friendly address truncation
- **Proposal Tracking:** Shows real-time proposal count on bounty cards
- **Proposal Submission:** Complete form with summary, deliverables, repository links, and demo URLs
- **User Highlighting:** Automatically highlights if current user is assigned as judge
- **Multi-Judge Support:** Bounty creation form now accepts multiple judge addresses

---

### PR #12: Proposal Fetch and Submit Functionalities Implemented  
**Status:** ✅ Merged  
**Link:** [Pull Request #12](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/12)  

**Description:**
This PR integrated full on-chain proposal management with the ErgoScript smart contracts:
- Implemented proposal submission linked to smart contract interactions
- Added comprehensive proposal display with all metadata
- Enhanced judge visibility with role badges
- Updated bounty dashboard with proposal counts

**Proposal System Features:**
- **Submission Form:** Developers can submit proposals with summary and code URL
- **On-Chain Storage:** All proposals stored on Ergo blockchain via smart contracts
- **Rich Display:** Each proposal shows:
  - Clickable developer address (truncated)
  - Submission timestamp
  - Clickable repository/code URL
  - Associated bounty ID
  - Extracted requirements from bounty description

**Judge Integration:**
- Judge badge displayed for current user when assigned
- Clickable judge addresses for non-judges
- Role-based UI rendering

**Dashboard Enhancements:**
- Each bounty card displays:
  - Truncated judge address
  - Total submitted proposals count
  - Active status indicators

---

### PR #13: Proposal Approval Logic and UI Added  
**Status:** ✅ Merged  
**Link:** [Pull Request #13](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/13)  

**Description:**
Implemented the critical proposal approval flow enabling creators to approve proposals and trigger automatic reward distribution:

**Smart Contract Integration:**
- Added an approval function in ErgoScript
- Implemented validation for bounty value and fee calculations
- Automated UTXO creation for approved proposals
- Validated proposer and contributor reward distribution

**Payout Mechanism:**
- Validated reward amounts against bounty balance
- Calculated and deducted developer fees
- Distributed rewards to proposers automatically
- Ensured correct token distributions

**Impact:** Creators can now seamlessly approve proposals from the UI, triggering all reward distribution and on-chain state updates automatically.

---

### PR #14: Add Dispute Functionality to Proposal Contract  
**Status:** ✅ Merged  
**Link:** [Pull Request #14](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/14)  

**Description:**
This massive PR implemented comprehensive dispute functionality and fixed critical ErgoScript validation bugs:

**Dispute System:**
- Proposers and bounty creators can now dispute proposals
- Disputes can be initiated from any proposal state (Pending, Approved, Rejected)
- Added R8 register for tracking proposal lifecycle states:
  - `0`: Pending (awaiting approval)
  - `1`: Approved (creator approved, rewards distributed)
  - `2`: Rejected (creator rejected)
  - `3`: Disputed (dispute initiated)

**Authorization & Security:**
- Only proposers and bounty creators can initiate disputes
- Signature validation separated from Boolean logic
- Pure Boolean validation functions for contract logic
- Transaction-level authorization for better security

**Testing Infrastructure:**
- Established comprehensive testing framework using Jest + TypeScript
- Added test scripts and updated dependencies
- Bumped TypeScript toolchain for better compatibility

**Impact:** This PR established a robust dispute resolution system while fixing critical contract validation issues that were preventing transactions from succeeding.

---

### PR #15: Add Judge Selection, Profiles, and Reputation System  
**Status:** ✅ Merged  
**Link:** [Pull Request #15](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/15)  

**Description:**
This comprehensive PR introduced the complete judge ecosystem with selection, profiles, and reputation tracking:

**Judge Selection in Bounty Creation:**
- Added dropdown menu listing all registered judges
- Each judge displayed with truncated, user-friendly address
- "Use" button to populate manual input field with selected judge
- "View" button for direct link to judge profile
- Manual address entry still supported for flexibility

**Judge Profiles (`/judges/[id]`):**
- New dynamic route for individual judge profiles
- Client-side data fetching with ergoTree to base58 conversion
- Displays on-chain reputation data
- Shows linked social profiles (Twitter, GitHub, LinkedIn)
- All judge addresses across the app now clickable links to profiles

**Judge Registration System:**
- "Register as Judge" page for new judge onboarding
- Creates on-chain reputation proof upon registration
- Stores wallet addresses and social profile links on-chain
- Reputation contracts implemented in ErgoScript

**Judge Discovery:**
- "Browse Judges" page lists all registered judges
- Searchable and filterable judge directory
- Easy discovery of available judges

**Impact:** This PR delivered the foundation for a decentralized judge system, providing bounty creators with a frictionless way to select trusted judges while enabling judges to build verifiable reputations.

---

### PR #16: Fix Judge Selection and Detection System
**Status:** 🔄 Open (Under Review)   
**Link:** [Pull Request #16](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/16)  

**Description:**
This PR addresses critical issues in the judge reputation system identified during testing:

**Problems Solved:**

1. **Judge Identification Issue:**
   - **Problem:** System was using wallet addresses instead of reputation token IDs
   - **Why It's Wrong:** In Ergo's reputation system, judges are identified by unique reputation token IDs (NFTs), not addresses
   - **Solution:** Updated entire system to consistently use reputation token IDs:
     - Bounty creation stores judge token IDs in content
     - Judge selection dropdown shows token IDs with preview
     - Judge validation checks for proper 64-character hex format

2. **Address Display Confusion:**
   - **Problem:** All judges showed same "contract address" (e.g., `2kCeUT...fqNm`), making them appear identical
   - **Root Cause:** All reputation proof boxes use the same smart contract (ergoTree), so contract address is identical
   - **What Makes Judges Unique:**
     - Reputation token ID (stored in box assets)
     - Owner hash (R7 register - blake2b256 hash of wallet's ergoTree)
   - **Solution:** Clarified display to show:
     - "Judge ID" (reputation token ID) as unique identifier
     - "Owner Script Hash" (R7 value) proving ownership

**Impact:** This PR fixes fundamental issues in judge identification, aligning the implementation with actual blockchain data structures and ensuring reliable judge detection throughout the platform.

---

### PR #17: Refactor - Load Ergo Smart Contracts from .es Files
**Status:** 🔄 Open (Under Review)  
**Link:** [Pull Request #17](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/17)  

**Description:**
Major refactoring to improve maintainability by extracting smart contracts from embedded strings:

**Previous Approach:**
- All ErgoScript contracts defined as TypeScript string literals
- Embedded directly in source code files
- Difficult to maintain, edit, and test
- Reduced code readability

**New Approach:**
- All contracts moved to separate `.es` files in `contracts/` directory
- TypeScript logic fetches and compiles contracts dynamically
- Clean separation of concerns

**Benefits:**
- **Maintainability:** Easier to edit and version contract code
- **Readability:** Cleaner TypeScript files without long string literals
- **Testing:** Can test contracts independently
- **Modularity:** Clear contract organization and import paths
- **Developer Experience:** Syntax highlighting for `.es` files

**Future Improvements:**
- Automated validation for `.es` contracts
- Compilation tests in CI/CD pipeline
- Contract versioning system

---

### PR #18: Fix Static Build & Add GitHub Actions Deployment Workflow
**Status:** 🔄 Open (Under Review)  
**Link:** [Pull Request #18](https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo/pull/18)  

**Description:**
Addressed critical build issues for static deployment and automated CI/CD:

**GitHub Actions Workflow:**
- Automated build and deployment to GitHub Pages
- Triggers on push to `main` or manual dispatch
- CI/CD automation for future deployments
- Ensures repeatable, reliable deployments

**Outcome:**
- Static deployment now succeeds without errors
- Dynamic routes render correctly in browser
- Automated deployment pipeline established
- Consistent build process across environments

---

## Technical Architecture

### Smart Contract Design (ErgoScript)

The platform uses a comprehensive box model for the bounty lifecycle:

**Bounty Box Structure:**

**Tokens:**
- **BBT (Bountiful Bounty Token):** Unique bounty identifier holding allocated rewards
- **PBT (Proof of Bounty Token):** Represents submissions, minted upon acceptance
- **RBT (Reputation Bounty Token):** Represents reputation events for judges

**Register Schema:**
- **R4:** `Int` - Block height (deadline)
- **R5:** `Long` - Minimum submissions required
- **R6:** `Coll[Long]` - [Total Submissions, Accepted, Rejected]
- **R7:** `Long` - Reward amount in ERG
- **R8:** `Coll[Byte]` - Encoded JSON with creator/judge data, trust status
- **R9:** `Coll[Byte]` - Encoded JSON with bounty metadata, submissions, judgments

---

### Technology Stack

**Frontend:**
- **Framework:** SvelteKit (modern, reactive framework)
- **Styling:** Tailwind CSS for responsive design
- **UI Components:** Custom Svelte components
- **State Management:** Svelte stores

**Blockchain:**
- **Smart Contracts:** ErgoScript
- **SDK:** FleetSDK, Nautilus SDK
- **Wallet:** Nautilus Wallet integration
- **Hashing:** Blake2b-256

**Development Tools:**
- **Testing:** Jest + TypeScript
- **Build:** Vite
- **Version Control:** Git, GitHub
- **CI/CD:** GitHub Actions
- **Deployment:** GitHub Pages (static)

---

## Key Achievements

### Completed Core Deliverables

✅ **Functional Platform:** Complete bounty lifecycle from creation to payout  
✅ **Smart Contract Suite:** All 9 core contract functions implemented and tested  
✅ **Wallet Integration:** Seamless Nautilus wallet connectivity  
✅ **Judge System:** Complete judge registration, selection, and reputation tracking  
✅ **Proposal Management:** Full proposal submission, display, and approval flow  
✅ **Dispute Resolution:** Comprehensive dispute mechanism with on-chain tracking  
✅ **Cryptographic Verification:** Merkle tree-based judgment verification  
✅ **Reputation Framework:** Token-based, browser-calculated reputation system  
✅ **UI/UX:** Intuitive, responsive interface for all user journeys  
✅ **Testing Infrastructure:** Jest-based testing framework established  
✅ **CI/CD Pipeline:** Automated deployment workflow via GitHub Actions

### Technical Challenges Overcome

1. **ErgoScript Type System:** Resolved SSigmaProp/Boolean mixing issues
2. **Scalability:** Implemented Merkle trees to handle unlimited judgments
3. **Judge Identity:** Shifted from addresses to reputation token IDs
4. **Contract Maintainability:** Refactored to separate `.es` files
5. **Static Build:** Fixed SvelteKit adapter issues for GitHub Pages deployment

---

# StablePay Merchant Dashboard

## Project Overview

StablePay Merchant Dashboard is an enhanced cryptocurrency payment solution that simplifies crypto transactions for merchants by creating a seamless bridge between traditional e-commerce platforms and decentralized finance. The dashboard provides merchants with comprehensive control over their crypto payment infrastructure.

---

## GitHub Repository

- **Main Repository:** [StablePay-MerchantDashboard](https://github.com/DjedAlliance/StablePay-MerchantDashboard)
- **Live Demo:** *Deployment in progress*

---

## Major Pull Requests & Contributions

### PR #2: Integrate Wallet Connection Using Wagmi and Custom Hook
**Status:** 🔄 Open (Under Review)  
**Link:** [Pull Request #2](https://github.com/DjedAlliance/StablePay-MerchantDashboard/pull/2)  

**Description:**
This comprehensive PR transforms wallet connectivity from hardcoded implementation to dynamic, multi-wallet support:

**New Architecture:**
- Created reusable `useWallet` hook for managing wallet state
- Wrapped application with `WagmiProvider` for wallet context
- Implemented wallet connection/disconnection flows
- Added dynamic wallet address display

**Key Features:**
- **Connect Wallet Button:** Users can connect/disconnect wallets from dashboard
- **Dynamic Address Display:** Real-time wallet address updates
- **Session Persistence:** Wallet connection state preserved across sessions
- **Multi-Wallet Ready:** Architecture supports multiple wallet types
---

### PR #3: Implement Transaction Filtering by Wallet Address
**Status:** 🔄 Open (Under Review)  
**Link:** [Pull Request #3](https://github.com/DjedAlliance/StablePay-MerchantDashboard/pull/3)  

This PR enhances the transaction fetching and caching logic for merchant-specific data. Key updates include:

* Reduces unnecessary blockchain queries by fetching only relevant and new transactions.
* Improves performance and reliability by persisting cached data.
* Provides a foundation for future improvements, such as deduplication and robust error handling.

---

## Technology Stack

**Frontend:**
- **Framework:** React with Next.js
- **Styling:** Tailwind CSS
- **UI Library:** Material UI components
- **State Management:** React hooks, Context API

**Web3 Integration:**
- **Wallet Connection:** Wagmi library
- **Web3 Providers:** Ethers.js
- **Blockchain Interaction:** Viem

**Development Tools:**
- **Build Tool:** Webpack, Vite
- **Testing:** Jest, React Testing Library
- **Linting:** ESLint, Prettier
- **Version Control:** Git, GitHub

---

## Key Achievements

### Completed Core Deliverables

✅ **Dynamic Wallet Connection:** Wagmi-based wallet integration with reusable hooks  
✅ **Multi-Wallet Architecture:** Adapter pattern for supporting multiple wallet providers  
✅ **Dashboard UI:** Clean, intuitive merchant dashboard interface  
✅ **Wallet State Management:** Persistent wallet connection across sessions  
✅ **Responsive Design:** Mobile-first, responsive layouts

---

# Learning Experience

## Technical Insights

1. **Blockchain Development:**
   - ErgoScript's UTXO model requires different thinking than account-based chains
   - Type safety is crucial - mixing SBoolean and SSigmaProp causes hard-to-debug errors
   - Off-chain computation with on-chain verification scales better than pure on-chain logic
   - Merkle trees are essential for managing large datasets on-chain

2. **Frontend Integration:**
   - Browser-side calculation provides flexibility while maintaining verification
   - Static site generation requires careful handling of dynamic routes
   - Wallet connection state management needs robust error handling
   - User experience suffers without proper loading states and feedback

3. **Smart Contract Design:**
   - Simple, focused contracts are easier to audit and maintain
   - Modular contract architecture enables easier updates
   - Comprehensive validation prevents many attack vectors
   - Register space is precious - plan data storage carefully

## Project Management

1. **Scope Management:**
   - Breaking large features into smaller PRs improves review quality
   - Regular mentor communication prevents scope creep
   - Prioritizing core features over nice-to-haves ensures MVP completion

2. **Testing Strategy:**
   - Early testing infrastructure saves debugging time later
   - Integration tests catch issues unit tests miss
   - Manual testing remains essential for user experience validation

3. **Documentation:**
   - Writing documentation alongside code prevents knowledge loss
   - Clear commit messages aid future debugging
   - API documentation should include examples

## Community Engagement

1. **Open Source Collaboration:**
   - Pull request descriptions should be detailed and include testing notes
   - Responding to reviewer feedback promptly accelerates merge time
   - Contributing to discussions builds community trust

2. **Knowledge Sharing:**
   - Documenting challenges helps future developers
   - Sharing solutions benefits the broader ecosystem
   - Mentoring others reinforces own understanding

---

# Acknowledgments

I am deeply grateful to **Dr. Bruno Woltzenlogel Paleo**, my amazing mentors and the entire **AOSSIE team** for their constant guidance, support, and valuable feedback throughout my GSoC journey. Their expertise in blockchain technology and smart contract development was instrumental in overcoming technical challenges and achieving project goals.

Special thanks to:
- **AOSSIE Mentors:** For code reviews, architectural guidance, and patient explanations of ErgoScript intricacies
- **Ergo Community:** For technical support, documentation, and answering questions on Discord
- **Google Summer of Code Program:** For providing this incredible opportunity to contribute to open-source blockchain technology

This experience has been transformative, allowing me to:
- Deepen my understanding of blockchain architecture and smart contracts
- Contribute meaningful code to production-ready dApps
- Collaborate with talented developers from around the world
- Solve complex technical challenges in decentralized systems
- Grow as a software engineer and open-source contributor

The skills and knowledge gained during GSoC 2025 will continue to benefit my career and future contributions to the blockchain ecosystem.

---

# Conclusion

My Google Summer of Code 2025 journey with AOSSIE resulted in two substantial contributions to the blockchain ecosystem:

## Bountiful Platform Achievements

- **18 Pull Requests** spanning 350+ hours of development
- Complete bounty lifecycle from creation to payout
- Comprehensive smart contract suite in ErgoScript
- Judge reputation system with on-chain verification
- Dispute resolution mechanism
- Cryptographic proof system using Merkle trees
- Modern, responsive UI built with SvelteKit
- CI/CD pipeline with GitHub Actions

## StablePay Dashboard Achievements

- Dynamic wallet connection with multi-wallet support
- Merchant dashboard infrastructure
- Foundation for theme system and transaction filtering
- Scalable architecture for future enhancements

The code, documentation, and deployed applications will continue to serve the blockchain community, enabling developers to earn fair compensation for their work and merchants to accept cryptocurrency payments seamlessly.

---

**Project Repositories:**
- Bountiful: https://github.com/StabilityNexus/Bountiful-BountyPlatform-Ergo
- StablePay Dashboard: https://github.com/DjedAlliance/StablePay-MerchantDashboard

**Contact:**
- Email: nidhis@iitbhilai.ac.in
- GitHub: [@Nidhicodes](https://github.com/Nidhicodes)
- Discord: 0xcryptic

Thank you for this incredible opportunity to contribute to the future of decentralized technology! 🚀

---

*Google Summer of Code 2025 - AOSSIE - Nidhi Singh*
