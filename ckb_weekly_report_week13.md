## Key Learnings
This period was more focused on understanding the system than producing major repository changes. The important learning was how CKB transactions, Cells, lock scripts, and deployment references relate to one another.
A Cell is not simply an account balance. A transaction consumes existing Cells and creates new ones. The Vault therefore has to be understood as a Cell whose spending rules are controlled by the vault-lock script.
Another important idea was that deploying a contract and using that contract are separate operations. Once the Rust binary is deployed, transactions need the correct script information and Cell dependency so that CKB knows where to load the contract code.
## Development Environment
The same WSL2, Rust, OffCKB, CKB CLI, and TypeScript environment remained in use. Much of the work involved becoming more comfortable moving between these tools instead of treating each one as an independent system.
The project structure also became more meaningful. The Rust contract lived under contracts/vault-lock, deployment information lived under the deployment directory, and the TypeScript scripts acted as the off-chain transaction layer.
## Practices Done
There were no GitHub commits during this week, so there is no major implementation change that can be directly attributed to this period from the repository history.
The practical work was mainly learning and troubleshooting the existing workflow: understanding transactions, inspecting Cells, following deployment references, and understanding why client-side scripts need accurate contract metadata.
## Conclusion
There was no large code milestone during this week, but the conceptual model of CKB became stronger. That knowledge was necessary for the later work on the frontend, deployment flow, and timelock security.
Reflection
One lesson from this week is that progress should not only be measured by whether code was written. However, if the work cannot be seen in GitHub, it becomes harder to evaluate later.
Going forward, learning that leads to a concrete decision should ideally leave some trace in the repository, such as a small document, test, issue, or focused commit.
