#CKB Builder Track Weekly Report - week 6
**Name:** Nwaji Victor
**Week** 15/07/2026

### Course completed
- Transaction
- Transaction field
- cell_deps
- header_deps
- inputs
- outputs
- Block
- uncle blocks

  ## Key Learning
- Learnt what Transaction means in CKB. (The consumption of old cell and the creation of New cell).
  
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
