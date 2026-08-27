## CKB Builder Track Weekly Report - week 7 and 8
**Name:** Nwaji Victor
**Week** 22/08/2026


##  Key Learnings
This week focused on the CKB_Vault project. The CKB-Vault project is a learning and development project focused on understanding the Nervos CKB blockchain at a deeper level by building a custom vault smart contract. 
**Project Goal** The end goal of this project is for user to connect their wallet (joyID/ccc), create vault cell, Deposit CKB, Set Time-lock policy, wait for the Time-Lock period to elapse, unlock cell, spend cell. 
### Core CKB Concepts
I spent most of the week building the project's:  
* Core vault-lock with rust.
* Migrating the project from CKB Testtool to CKB devnet.
* Setting up the devnet environment.
* compiling the  contract for: `risc64imac-unknown-none-elf`

## 🛠 Development Environment
The project uses an OffCKB local development network, after successfully launching the devnet, i checked if it is accessible through the local RPC and also carrry out some connection test with TypeScript using CCC.
The local RPC endpoint is:
``
http://127.0.0.1:8114
``
The connection test produced:
``
Connected to CKB devnet!
Tip block: 9562
``
and later:
``
Connected to CKB devnet!
Tip block: 11845
``
This confirmed that the TypeScript application could communicate with the local CKB node.


##  Practical Work

### Contract Deployment
The vault-lock contract has already been deployed to the local OffCKB devnet.
The currently recorded deployment information is:
```
codeHash:
0x6c4c1c2174b32852799498439844ff66100fba73d10b4b8941f800b14d50496b
hashType:
data2
```
The latest deployment generated the following Cell Dependency:
```
txHash:
0x2f7577de9ac8cb93e89f06a82c387ef8634b81bc2830d09577fccca48cf17b01
index:
0
depType:
code
```
This deployment information is important because the vault transaction must reference the deployed contract through its cellDep.


## Making use of the Devnet Funding Account

OffCKB provides pre-funded development accounts, with the accounts i was able to make use of the one of the account (Account 0) as the funding source of the vault transaction.


The account's lock script is:

codeHash:
0x9bd7e06f3ecf4be0f2fcd2188b23f1b9fcc88e5d4b65a8637b17723bbda3cce8

hashType:
type

args:
0x8e42b1999f265a0078503c4acec4d5e134534297

The corresponding development address is:

ckt1qzda0cr08m85hc8jlnfp3zer7xulejywt49kt2rr0vthywaa50xwsqvwg2cen8extgq8s5puft8vf40px3f599cytcyd8

This account is being used as the funding source for the vault transaction.


Conclusion

The CKB-Vault project has progressed from basic contract development into actual transaction engineering.

The most significant achievement so far is that the complete pipeline from Rust contract → deployment → TypeScript → CCC → signer → transaction construction is now working.

The remaining issue is isolated to funding-cell selection and OutPoint resolution.

Once that is corrected, the next major milestone will be successfully creating and inspecting a real vault Cell on the OffCKB devnet.
