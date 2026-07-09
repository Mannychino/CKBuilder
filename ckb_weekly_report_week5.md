#CKB Builder Track Weekly report - week 5
**Name:** Nwaji Victor
**week** 07/07/2026

### Course Completed
- script (lockscript and typescript)
- code_hash
- Hash_type
- Data Hash and Type Hash
- script args
- introduction to transaction

## key learning
- How script is not the actual program itself, it is a reference to the executable code that lives in code cell as a Risc-V binary
- the three major fields of script (code_hash, args and hash_type).
- code_hash: which program should be executed, args: Hexstring: simply inputs to the program, Hash_type: Tells the ckb where to look
  
- ## Lockscript:  is a Script attached to a Cell that defines the rules for who is allowed to spend that Cell.
  I also get to understand how the unlocking process works
  Spend Cell
      │
      ▼
Read Lock Script
      │
      ▼
Find signature verification program
      │
      ▼
Load signature from Witness
      │
      ▼
Compare against args (public key hash)
      │
      ▼
Valid?
   │         │
  Yes       No
   │         │
Spend     Reject

A Lock Script is a Script stored inside a Cell that defines its ownership rules. It references a signature verification program through code_hash and stores the owner's public key hash in args.

- **Typescript:** A programmable rulebook attached to a cell that validate the cell state is allowed to change from input version to its output version during a transaction.
- Typescript protect correctness
- Different assets (such as xUDTs, NFTs DAOs and custom  applications ) use different typescript because each asset has its own state transition rules.
- also understond that both typescript and lockscript have the same field.
- (code_hash, args, hash_type)

  ## Practical progress
  ** setup node**










