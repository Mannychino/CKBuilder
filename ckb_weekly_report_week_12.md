## CKB Builder Track Weekly Report - week 12
**Name:** Nwaji Victor
**Week** 05/09/2026


##  Key Learnings
The main lesson this week was that building CKB-Vault is not only about writing the Rust lock script. A usable blockchain project also needs a repeatable process for compiling the contract, running a local chain, deploying the binary, connecting through RPC, creating transactions, and inspecting the resulting Cells.
I developed a clearer understanding of how the different parts of the CKB development stack fit together. The Rust contract provides the on-chain rules, OffCKB provides the local blockchain environment, CKB RPC exposes the node to applications, and the TypeScript scripts act as the client that constructs and submits transactions.
This also helped separate two responsibilities in my mind. The Rust contract decides whether a Cell can be spent, while the TypeScript side is responsible for building a transaction that satisfies those rules.

## Development Environment
**Setting up the documentation and environment organization.**  
Most of the visible work this week was documentation and environment organization. GitHub commit 9846abc revised docs/installation.md and began turning the setup process into a reproducible development workflow.

**Generating Private keys for testing purpose**
Security warnings were also documented for the local OffCKB accounts. The generated private keys were treated strictly as development keys and not something that should ever be used with real CKB.
```bash
  export CKB_PRIVATE_KEY="private key"
export CKB_RPC_URL="Your CKB RPC URL"
export CKB_RPC_FALLBACK="YOUR_CKB_RPC_URL"
```
## Conclusion
By the end of this week, CKB-Vault had a clearer development process. The project was no longer just a collection of source files. There was now a defined path from source code to a contract running on a local blockchain.

## Reflection
This week showed me that environment setup is part of software engineering, not something separate from it. If another developer cannot reliably reproduce the build and deployment process, then the project is difficult to maintain regardless of whether the contract itself works.
It also made RPC easier to understand. I started seeing the CKB node similarly to a backend service: the blockchain node exposes an interface, and my application sends requests to it to read blockchain state or submit transactions.
