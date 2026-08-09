## CKB Builder Track Weekly Report - week 9
**Name:** Nwaji Victor
**Week** 07/08/2026
## Course completed 
This week, I began moving from understanding these concepts theoretically to writing and testing actual on-chain logic.
The main focus was learning how CKB Scripts work in practice, participating in the Simple Lock Script exercise, continuing my exploration of CCC, and starting the implementation of my own project, CKB-Vault.


##  Key Learnings
* This week i focused on learning how to write a onchain logic for my project.
  One of my main objectives this week was to understand how to move from simply understanding CKB Scripts to actually writing an on-chain Script.
I learned that a Script on CKB is essentially a program executed by CKB-VM during transaction validation. Rather than thinking of a smart contract purely as a program that stores state, I am beginning to understand CKB Scripts as validation logic that determines whether a proposed state transition is valid.


  2. Participating in the Simple Lock Script Exercise
I participated in the Simple Lock Script task from the CKB documentation.
The objective was to follow the tutorial, get the Script running, deploy it to the development environment, test the transaction flow, and reflect on the experience.
  
  3. Diving Deeper Into Scripts
This week I spent more time understanding what a Script actually is.
A Script is not simply a piece of application code sitting on a server. It is a binary executable that is executed by CKB-VM as part of transaction validation.
This distinction helped me understand why CKB development has a different architecture from traditional Web2 applications.

4. Continuing to Learn CCC

I also continued learning about CCC (CKBers' Common Chain) and how it can be used from the application side.
In particular, I explored how CCC can help with:

Wallet connection
Signers
Transaction construction
Sending transactions
Working with CKB assets

This helped me understand the separation between the frontend and the on-chain Script.
The frontend does not enforce the rules of the vault. Instead, the frontend constructs a transaction and asks the user to sign it, while the CKB Script ultimately determines whether the transaction satisfies the required rules.

  ##Practical Exercise
    1. Simple Lock Script
I participated in the Simple Lock Script exercise. 
The goal was to successfully run the tutorial, understand the process, report the outcome, and reflect on the difficulties encountered.
*This exercise gave me practical experience with the CKB Script development workflow and exposed me to the relationship between Scripts, transactions, deployment, wallets, and the CKB development environment.


### 2. Started CKB-Vault
I started designing and implementing a project called CKB-Vault.
* CKB-Vault is a proposed decentralized time-locked vault for securing CKB assets on Nervos.
### The initial MVP is intentionally simple:
* The vault supports CKB only.
* CKB is represented using Shannon as the working unit.
* Each vault contains one type of asset.
* A vault uses one lock policy.
* The vault's lock policy is immutable after creation.
* Users can create a vault and deposit CKB.
* The vault should prevent spending before the configured unlock condition.
* The lock should be enforced on-chain rather than by the frontend.
The project gives me a practical reason to explore CKB Scripts instead of learning them in isolation.

### Exploring Time-Lock Logic

While designing CKB-Vault, I began investigating how the unlock condition should be represented.
One idea I explored was using Script arguments to represent the unlock condition and having a custom lock Script enforce it.
This led me deeper into CKB's transaction validation model and concepts such as transaction inputs, Script arguments, and since.
Rather than treating the unlock time as something controlled by the frontend, the goal is for the blockchain itself to enforce the condition.
This is still an area I am actively experimenting with and will continue developing in the next stage of the project.

### Reflection
This week was different because I finally started building with those concepts.
The Simple Lock exercise showed me what the theory looks like when it becomes a real transaction. Starting CKB-Vault then gave me a larger problem to apply the knowledge to.
One of the biggest lessons so far is that learning CKB cannot stop at understanding terminology. Concepts such as Cells, Scripts, transactions, and capacity only really become clear when I use them to build something.
CKB-Vault is therefore more than just a project for me. It is becoming a learning environment where I can progressively explore the architecture of Nervos.
I also realize that I still have a lot to learn. I need to become more comfortable with CKB-VM, Script execution, transaction validation, time-lock mechanisms, CCC, and eventually more advanced CKB technologies.
However, compared with where I started, I now have a much clearer mental model of how CKB works.









