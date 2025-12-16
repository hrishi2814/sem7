### Ethereum Virtual Machine (EVM)

**Definition**  
The **Ethereum Virtual Machine (EVM)** is a **decentralized, global computation engine** that executes **smart contracts** on the Ethereum blockchain. It ensures that smart contract code runs **identically on every Ethereum node**, maintaining consistency and trust in the network.

---

## Purpose of EVM

The main purpose of the EVM is to:

- Execute smart contracts securely
    
- Maintain deterministic execution across all nodes
    
- Provide a sandboxed environment isolated from the host system
    

---

## How EVM Works

1. **Smart Contract Deployment**
    
    - Smart contracts are compiled (for example from Solidity) into **EVM bytecode**.
        
    - Bytecode is stored on the blockchain.
        
2. **Transaction Execution**
    
    - When a transaction calls a contract, EVM executes the bytecode.
        
    - Each operation consumes **gas**.
        
3. **State Update**
    
    - If execution succeeds, Ethereum’s global state is updated.
        
    - If gas runs out or execution fails, state changes are reverted.
        

---

## Key Components of EVM

### 1. Stack

- Stack-based architecture
    
- Operates on 256-bit words
    
- Stores temporary values during execution
    

---

### 2. Memory

- Temporary and volatile
    
- Used only during contract execution
    

---

### 3. Storage

- Persistent and stored on the blockchain
    
- Holds contract variables
    
- Expensive in terms of gas
    

---

### 4. Opcodes

- Low-level instructions executed by the EVM
    
- Examples: ADD, MUL, JUMP, CALL
    

---

## Gas Mechanism

- Gas measures computational effort
    
- Prevents infinite loops and spam
    
- Users pay gas fees in **Ether (ETH)**
    

---

## Features of EVM

- Deterministic execution
    
- Turing-complete
    
- Isolated execution environment
    
- Platform independent
    

---

## Importance of EVM

- Enables decentralized applications (dApps)
    
- Supports token standards (ERC-20, ERC-721)
    
- Allows cross-chain compatibility among EVM-based blockchains
    

---

## Limitations

- Scalability issues
    
- High gas costs
    
- Limited execution speed
    

---

## Conclusion

The Ethereum Virtual Machine is the **core execution layer of Ethereum**, enabling secure and consistent smart contract execution. It plays a vital role in powering **DeFi, NFTs, and Web3 applications**, making Ethereum a programmable blockchain platform.

This note is **ideal for a 5–6 mark exam answer**.