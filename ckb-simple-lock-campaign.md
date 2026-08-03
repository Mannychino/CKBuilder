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
    -  ![Offckb Node](https://github.com/Mannychino/CKBuilder/blob/d543615e1bd2ebcf95383a95da4363c52f809b53/Screenshot%20(27).png)
    -  ![Deploy script](https://github.com/Mannychino/CKBuilder/blob/b9a6b9c30bb2627334df3c1dad835f6b5e4fdb08/Screenshot%20(16).png)
    -  ![Deposit CKB](https://github.com/Mannychino/CKBuilder/blob/498bded61dc2837d4718f01d4d350dee56f86461/Screenshot%20(29).png)
    -  ![w0rking lock-script](https://github.com/Mannychino/CKBuilder/blob/d4f7f5af850fd4d3606ce91199356f6561b5566f/Screenshot%20(30).png)
   





