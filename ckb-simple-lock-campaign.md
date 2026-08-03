### The Build on CKB Campaign
- The campaign goal is to complete the Build a simple Lock tutorial and share an interesting reflection.
  **Proof of completion**
  - Deploying a custom Lock Script
  - Deploying a dApp frontend to transfer tokens from the lock script.
 
    **Step 1**:  Start the devnet with offckb node
    check if the node is running with offckb status
    - **Step 2**: Clone the repository and navigate to Simple Lock file.
    - **Step 3**: Build and deploy the script with pnpm install pnpm build and pnpm run deploy --network devnet
    - **Step 4**: Run the Dapp with cd frontend && pnpm i && pnpm run dev 
    **Note** Before you run the Dapp, Update the frontend script.json with script.json from the dployment file
    - **Step 5** Deposit some CKB for testing purpose. with offckb deposit --network devnet [address]
    - You can now begin testing by clicking the transfer button and modifying the preimage.
    - **Step 6** Enter the amount of ckb you want to transfer, enter the preimage and submit the transaction.

    ## You can check the following images for each progress
    -  ![image alt]()
   





