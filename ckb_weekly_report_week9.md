## CKB Builder Track Weekly Report - week 9
**Name:** Nwaji Victor
**Week** 07/08/2026


##  Key Learnings
* This week i focused on learning how to write a onchain logic for my project.
* i also participated in the build a simple lock script task.
* Dive deep into script (A binary executable that be executed on chain)
* continued learning about ccc and how to use them for signer, connect wallet and creating a transaction









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
