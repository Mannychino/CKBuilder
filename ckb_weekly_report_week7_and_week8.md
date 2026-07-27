
#CKB Builder Track Weekly Report - week 7 and 8
**Name:** Nwaji Victor
**Week** 22/07/2026


##  Key Learnings
This week focused on reinforcing my understanding of the core concepts of the Nervos CKB blockchain while gaining hands-on experience with the official development tools and workflow.
### Core CKB Concepts
I spent most of the week revisiting and strengthening my understanding of:

* **Cells** and the Cell Model.
* **Lock Scripts** and **Type Scripts**, including their responsibilities and differences.
* **CKB Transactions**, focusing on how transactions consume existing Cells and create new ones.
* The complete lifecycle of a transaction, from construction and signing to verification and inclusion on-chain.

Through transaction analysis, I gained a much clearer understanding of how a simple CKB transfer works internally.


## 🛠 Development Environment

To create a more stable development environment, I migrated my workflow from **Windows** to **WSL (Windows Subsystem for Linux)**.
During the setup process, I successfully installed and configured the core CKB development tools, including:
* Node.js (LTS)
* pnpm
* Rust & Cargo
* `offckb`
* `ckb-cli`
* `ckb-debugger`

This setup provides a much smoother development experience and aligns with the official CKB development workflow.

##  Practical Work

### Simple Lock Project and CCC playground

I set up and explored the **Simple Lock** project from the official Nervos documentation. I used the project as a reference to understand how a real CKB dApp is structured.

Through this project, I learned:

* The overall structure of a CKB application.
* The CKB development workflow:

  * Build
  * Compile
  * Deploy
  * Fund
  * Interact
  * Verify
* How JavaScript/TypeScript smart contracts are compiled into executable CKB bytecode.
* The role of **`ckb-debugger`** in the contract compilation process.


### Working with `ckb-cli`

I also spent time becoming familiar with the official **CKB CLI**.

Some of the operations I practiced include:

* Querying live Cells.
* Inspecting transactions.
* Checking wallet balances.
* Reading on-chain transaction data.
* Understanding how developers manually interact with a CKB node through RPC.

This helped me understand how the CLI complements SDKs such as CCC during development and debugging.
### Exploring the CCC SDK

I successfully ran several CKB example projects and became more familiar with the **CCC SDK**.

This gave me a better understanding of how frontend applications communicate with the blockchain, construct transactions, and interact with CKB nodes.


### Wallet Setup

To prepare for testing real-world dApps, I installed the **JoyID** browser wallet.

This will allow me to:

* Connect to CKB dApps.
* Test applications built with the CCC SDK.
* Understand how browser wallets integrate with the CKB ecosystem.
* Explore the relationship between wallets, lock scripts, transaction signing, and on-chain interactions.

## Reflection
This week marked an important milestone in my CKB learning journey. I moved beyond studying individual concepts and focused on understanding how they work together in a real development environment.
By combining theoretical knowledge with hands-on practice, I now have a much stronger understanding of:
* The CKB Cell Model.
* Transaction structure and lifecycle.
* The purpose of Lock Scripts and Type Scripts.
* The official CKB development toolchain.
* The end-to-end workflow for building and testing CKB applications.
* Using the CCC SDK and CKB CLI in practical development.

With this foundation in place, my next goal is to dive deeper into the more CKB Project, create my first dapp.

## Images
![image One]()
  









