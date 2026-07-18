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
**inputs** It lists all the cells that were consumed, Also each structure of inputs is of type CellInput, this references a previously created output cell.
i also learnt about the other strutures of transaction and the functions there play in consuming and creating new cells.

##My reflection
- This week has taught me why CKB is different from other blockchain in terms of processing data and the philosophy behind the design. 
CKB is more keen on building a well secured blockchain but it own way. It could have been built like any other public blockchain which uses account model.


