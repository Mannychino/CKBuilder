# Weekly Report — CKB-Vault Development
## Date: 15-8-2026

## Overview
This week, I focused on **CKB-Vault** project and building the foundation of a vault-style smart contract on **Nervos CKB**.
The main goal was not simply to write a contract, but to understand how a CKB smart contract is structured, compiled, deployed, and tested. I worked through the CKB Cell Model, lock scripts, RISC-V contract compilation, CKB testing infrastructure, and the challenges of separating the contract's on-chain environment from its native Rust testing environment.
The project is being developed using **Rust and CKB-STD**, with **CKB Testtool** used to simulate transactions and verify the lock script.
A major milestone this week was getting the `vault-lock` contract to successfully compile into a RISC-V executable and passing its automated transaction test.

---

# 1. Project Goal
CKB-Vault is being developed as a vault-style application on Nervos CKB.
The initial contract is called:
vault-lock
The purpose of this contract is to serve as the foundation for controlling access to CKB cells through a custom **Lock Script** .
Rather than using the standard wallet lock directly, the project explores how a custom lock script can define the rules under which a Cell can be spent.
The project therefore provides a practical way to built a project with what i learnt so far:
* CKB Cells
* Lock Scripts
* Script arguments
* Witnesses
* Transaction validation
* Cell consumption
* RISC-V smart contracts
* Contract testing
* CKB development tooling

#  CKB Concepts Applied
One of the most important parts of this project was connecting the theoretical CKB concepts I had previously studied with an actual implementation.
## Cell Model
The project uses the CKB Cell Model
It then retrieves the script arguments:
# Script Arguments
The project currently demonstrates how arguments can be passed into a CKB Lock Script.
The test constructs the lock script with:
rust
let lock_script = context
    .build_script(&out_point, Bytes::from(vec![42]))
    .expect("failed to build lock script");
The value:
```
text
42
```
is therefore supplied as the script argument.
Inside the contract, those arguments are retrieved using:
``
rust
let args = script.args().raw_data();
``
This establishes the basic relationship:

Transaction
      ↓
Lock Script
      ↓
Script Arguments
      ↓
Contract Logic

# Cargo Configuration
The project uses:
```toml
[dependencies]
ckb-std = "1.1"

[dev-dependencies]
ckb-testtool = "1.1.1"
```
The project also defines:
```toml
[features]
library = []
native-simulator = ["library", "ckb-std/native-simulator"]
```
The `library` feature allows the contract code to be compiled as a normal Rust library for testing.

The `native-simulator` feature enables CKB's native simulation functionality.


# Major Compilation Problem

One of the biggest technical problems encountered was running:
```
bash
cargo test --test vault_lock,  without correctly separating the contract binary from the native test environment.
The linker initially produced:
duplicate symbol: _start
```
# Correct Build Target
The CKB contract must be compiled for:
```text
riscv64imac-unknown-none-elf
```
instead of the normal host target:
```text
x86_64-unknown-linux-gnu
```


# RISC-V Contract Verification
The generated contract was inspected using:

```bash
file target/riscv64imac-unknown-none-elf/release/vault-lock
```

The result confirmed:

```text
ELF 64-bit LSB executable
UCB RISC-V
RVC
soft-float ABI
statically linked
```

This confirmed that the contract was actually compiled for the CKB RISC-V environment rather than the local x86-64 Linux environment.

The ELF header was also inspected using:

```bash
riscv64-unknown-elf-readelf -h target/riscv64imac-unknown-none-elf/release/vault-lock
```

The output confirmed:

```text
Machine: RISC-V
Type: EXEC
Entry point address: 0x1521c
Flags: RVC, soft-float ABI
```

This was an important milestone because it verified that the contract was now a valid RISC-V executable suitable for CKB execution.

---

---

# 11. Successful Contract Build

Eventually the contract successfully produced:

```text
target/riscv64imac-unknown-none-elf/release/vault-lock
```

This gave the project a real compiled CKB contract binary that could be loaded by the test environment.

# CKB Testtool Integration
The next major stage was testing the contract.

for the project, i used:

```text
ckb-testtool = 1.1.1
```

The test creates a simulated CKB environment:

```rust
let mut context = Context::default();
```

The compiled contract is then loaded from:

```text
target/riscv64imac-unknown-none-elf/release/vault-lock
```

and deployed into the test environment:

```rust
let out_point = context.deploy_cell(contract_bin.into());
```


# 13. Creating the Lock Script

The test constructs the lock script from the deployed contract:

```rust
let lock_script = context
    .build_script(&out_point, Bytes::from(vec![42]))
    .expect("failed to build lock script");
```

This produces a lock script containing:

```text
Code Hash
Hash Type
Args = [42]
```

The lock script is then attached to the input Cell and output Cell.

---

# 14. Simulated Transaction

The test creates an input Cell:

```text
Capacity: 1000 CKB
Lock: Vault Lock
Data: empty
```

Then it creates an output Cell:

```text
Capacity: 1000 CKB
Lock: Vault Lock
Data: empty
```

The transaction therefore represents:

```text
Input Cell
   │
   │ Vault Lock
   ▼
Transaction
   │
   ▼
Output Cell
   │
   │ Vault Lock
   ▼
New Cell
```

The transaction is completed with:

```rust
let tx = context.complete_tx(tx);
```

and then verified using:

rust
context
    .verify_tx(&tx, 10_000_000)
    .expect("transaction should pass");


and the test passed.

# GitHub Integration

The project has now been added to GitHub:

**CKB-Vault**

The repository is:

`https://github.com/Mannychino/CKB-Vault`

# Current Features

At the current stage, the project supports:

### Custom Vault Lock Script

A custom CKB lock script has been implemented.

### Script Arguments

The contract can load and inspect its script arguments.

### RISC-V Compilation: The contract successfully compiles into a RISC-V executable.
 **Cell Deployment in Tests** The contract can be deployed into `ckb-testtool`.
**Transaction Simulation** A transaction can be constructed using Cells locked by the Vault Lock script.

### Transaction Verification

The transaction successfully passes CKB transaction verification.

### Automated Testing

The project has a working integration test:

text
test_vault_lock




# 19. Current Limitations

The Vault Lock contract is still at an early stage.

Currently:
* The lock script does not yet implement the final vault authorization rules.
* The contract currently returns success after loading the script arguments.
* There is no vault owner/manager authorization mechanism yet.
* There is no withdrawal policy yet.
* There is no multi-user vault logic yet.
* There is no time-lock functionality yet.
* There is no production deployment yet.
* There is no frontend interaction yet.
The current implementation should therefore be considered the **foundation of the Vault Lock system**, rather than the finished vault.

---

# 20. What I Learned
This project significantly improved my understanding of the relationship between CKB's architecture and actual smart-contract development.
The most important lessons were:

### 1. CKB contracts are RISC-V programs
They are not ordinary Linux applications.
They must be compiled for:

text
riscv64imac-unknown-none-elf

### 2. Lock Scripts control spending
The Lock Script determines whether a Cell can be consumed by a transaction.
### 3. Script arguments provide contract-specific information
The contract can read:

rust
script.args()

and use those arguments when validating a transaction.

### 4. Testing happens in a different environment

The native Rust test environment and the RISC-V CKB execution environment are different.

This distinction caused several of the initial linker problems.

### 5. The compiled contract is part of the test

The test does not simply call the Rust function directly.

It deploys the compiled contract binary and executes it through `ckb-testtool`.

### 6. Deployment creates an OutPoint

The test uses:

rust
let out_point = context.deploy_cell(contract_bin.into());


That OutPoint represents the deployed contract Cell and is then used to construct the Lock Script.

### 7. Toolchain configuration matters

The RISC-V build required the correct:

* Rust target
* Clang
* LLVM AR
* RUSTFLAGS
* CKB STD configuration

A smart contract can be logically correct while still failing because the compilation environment is incorrect.


# 23. Reflection

This week's work was particularly valuable because the project moved beyond simply reading about CKB and into actually building against the CKB execution model.

The most difficult part was not writing the initial contract logic. The biggest challenge was understanding why the same Rust project behaves differently when compiled for:


x86-64 Linux


versus:

```text
RISC-V CKB
```

Working through the linker errors, missing dependencies, RISC-V build configuration, LLVM tooling, contract binary generation, and `ckb-testtool` integration provided a much deeper understanding of how CKB smart contracts actually operate.

The successful test:

text
1 passed; 0 failed


represents more than just a passing unit test.

It confirms that the project now has a working pipeline from:

text
Rust Source Code
        ↓
CKB RISC-V Contract
        ↓
Compiled Contract Binary
        ↓
Deployment Cell
        ↓
Lock Script
        ↓
Transaction
        ↓
CKB Verification


This gives the CKB-Vault project a solid technical foundation for implementing the actual vault authorization system in the next stage.


# Summary

The major accomplishment this week was establishing a working **Vault Lock smart-contract foundation on Nervos CKB**.

The project can now compile a custom Rust lock script into a RISC-V executable, deploy that executable into a simulated CKB environment, construct Cells using the custom lock script, create a transaction, and successfully verify that transaction.

The next phase will focus on transforming this working technical foundation into an actual vault mechanism with meaningful authorization and spending rules.
 
