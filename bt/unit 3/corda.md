## Corda (in detail)

### Definition

**Corda** is an **open-source distributed ledger platform** developed by **R3**, designed specifically for **business and financial applications**. Unlike public blockchains, Corda focuses on **privacy, legal enforceability, and direct peer-to-peer transactions**.

---

## Core Idea of Corda

Traditional blockchains broadcast every transaction to all nodes.  
Corda **does NOT do this**.

👉 In Corda, **only the parties involved in a transaction receive and store that transaction**.

This makes Corda highly suitable for **banks, financial institutions, and enterprises**.

---

## Key Components of Corda

### 1. Nodes

- Each participant runs a **Corda node**.
    
- A node stores:
    
    - Its own transactions
        
    - Relevant transaction states
        
- Nodes communicate **directly** with each other.
    

---

### 2. States

- A **state** represents a shared fact or agreement (for example, a loan agreement).
    
- States are **immutable**.
    
- Any change creates a **new state**, not a modification.
    

---

### 3. Transactions

- Transactions **consume old states** and **produce new states**.
    
- Must be:
    
    - Cryptographically signed
        
    - Verified against contract rules
        

---

### 4. Contracts

- Contracts define **rules** that transactions must follow.
    
- Written in **Kotlin or Java**.
    
- Ensure business logic correctness, for example:
    
    - Required signatures
        
    - Valid state transitions
        

---

### 5. Flows

- **Flows** define how nodes communicate.
    
- Handle:
    
    - Message exchange
        
    - Transaction building
        
    - Signing and verification
        
- Written in **Kotlin or Java**.
    

---

### 6. Notary

- Prevents **double spending**.
    
- Verifies that input states have not already been consumed.
    
- Can be:
    
    - Centralized
        
    - Distributed (BFT-based)
        

---

## Consensus in Corda

Corda separates consensus into **two parts**:

1. **Validity Consensus**
    
    - Ensures transactions follow contract rules.
        
2. **Uniqueness Consensus**
    
    - Ensures states are used only once (handled by notaries).
        

This is different from blockchains like Bitcoin where both are combined.

---

## Privacy Model

- No global ledger
    
- Transactions are shared **only with involved parties and the notary**
    
- Supports **confidential identities**
    

---

## Smart Contracts in Corda

- Smart contracts are **not Turing-complete scripts** like Ethereum
    
- They are **deterministic JVM code**
    
- This avoids unpredictable behavior and improves security
    

---

## Features of Corda

- Permissioned network
    
- High privacy
    
- No cryptocurrency required
    
- High scalability
    
- Legal prose can be linked to contracts
    

---

## Use Cases

- Banking and finance
    
- Trade finance
    
- Insurance
    
- Supply chain agreements
    
- Inter-bank settlements
    

---

## Comparison with Blockchain

|Aspect|Corda|Traditional Blockchain|
|---|---|---|
|Ledger|Shared only among parties|Fully replicated|
|Privacy|High|Low|
|Cryptocurrency|Not mandatory|Usually required|
|Consensus|Notary-based|PoW / PoS|
|Use Case|Enterprise & finance|Public systems|

---

## Advantages

- Strong privacy
    
- Efficient transactions
    
- Enterprise-friendly
    
- Legal compatibility
    

---

## Limitations

- Not fully decentralized
    
- Smaller ecosystem compared to Ethereum
    
- Requires trusted notary services
    

---

## Conclusion

Corda is a **permissioned distributed ledger platform** optimized for **enterprise and financial use cases**, emphasizing **privacy, legal enforceability, and efficiency**, making it fundamentally different from public blockchains.

This is a **perfect 8–10 mark answer**.  
If you want, I can **shorten it to exactly 8 marks** or give you a **one-page exam format**.