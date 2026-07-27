#CKB Builder Track Weekly Report - week 7 and 8
**Name:** Nwaji Victor
**Week** 22/07/2026

### Course completed
- Review of Previous courses and Exercises
- 

  ## Key Learning
  This weeks, i spent the most revising what i've learnt so far, this reandes from Cells, scripts and transaction.
  - How a simple transaction like send CKB invokes the consumption and creation of new cells, the roles of lock_scripts and type_script and the various transaction stages it has to complete before it is verified.
- change my environment from windows to linux (WSL), with this, it will be easy for me to interact with CKB cli
- Installed CKB cli which i use it for checking balances, querying Cells,  inspecting transactions, deploying scripts manually and debugging

## Practical coursess
- This week practical works include setting up the Simple Lock project from the official repo
- Review the source code of the simple lock project and use the project as a point of reference to learn
  - How to use the ckb-cli to read transaction
  - The use of CKB debugging to check for errors
  - How the CKB development workflow goes from build, compile, deploy, fund, interact and verify.

  -I also took time to run CKB projects. with this i was able to learn more about ccc SDK and how to build with it. 

  
**- The Transaction structure**
  Transaction {
    version,
    cell_deps,
    header_deps,
    inputs,
    outputs,
    outputs_data,
    witnesses
} and the purpose of each field.

**- Different Transaction state**
- Pending Transaction
- Confirming Transaction
- Confirmed Transaction
- Conflicting Transaction
- Conflitive Transaction
- Reverted Transaction
- Abandoned Transaction.   
which state are stored locally and which are stored onchain.

**Cell_deps** How cell_deps allow script in the Transaction to reference or point to Live cell. 
structure of cell_deps 
   cell_deps[
     out_point
     dep_type
     ] 
     and their purposes.

**header_deps**. it list all Block header that that Transaction script can have access during execution.
**inputs** It lists all the cells that were consumed, Also each structure of inputs is of type CellInput, this references a previously created output cell.
i also learnt about the other strutures of transaction and the functions there play in consuming and creating new cells.

##My reflection
- This week has taught me why CKB is different from other blockchain in terms of processing data and the philosophy behind the design. 
CKB is more keen on building a well secured blockchain but it own way. It could have been built like any other public blockchain which uses account model.
