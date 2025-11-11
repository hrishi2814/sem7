
## 🪙 Practical 1: Installation of Metamask and Study Spending Ether per Transaction

### What is a blockchain?

A blockchain is a **distributed, immutable digital ledger**. It consists of a growing list of records, called "blocks," that are securely linked together using cryptography. Each block contains a hash of the previous block, creating a "chain."

### What is cryptocurrency?

A digital or virtual currency that uses cryptography for security. It operates on a decentralized network (a blockchain), meaning it's not controlled by any central authority like a bank or government (e.g., Bitcoin, Ether).

### What is Ethereum?

Ethereum is a decentralized, open-source blockchain platform with **smart contract** functionality. It's often described as a "global, programmable computer" that allows developers to build and deploy decentralized applications (dApps).

### What is Metamask?

Metamask is a popular **non-custodial** cryptocurrency wallet that runs as a browser extension or mobile app. It allows users to store and manage their crypto assets (like Ether) and interact with the Ethereum blockchain and its dApps.

### What are crypto wallets?

A crypto wallet is a piece of software (or hardware) that stores your **public and private keys**. It does _not_ store your actual coins (which live on the blockchain). It just holds the "keys" that give you access to them, allowing you to send and receive transactions.

### What is the difference between custodial and non-custodial wallets?

- **Custodial:** A third party (like a centralized exchange, e.g., Coinbase, Binance) holds your private keys for you. This is convenient but relies on trusting the third party.
    
- **Non-Custodial:** _You_ have sole control and responsibility for your private keys (and the 12-word seed phrase). Metamask is non-custodial. The motto is: **"Not your keys, not your crypto."**
    

### What is a public key and private key in cryptocurrency?

They are a core part of **asymmetric cryptography**.

![Image of asymmetric cryptography key pair](https://encrypted-tbn0.gstatic.com/licensed-image?q=tbn:ANd9GcTWGnh7WopJK18RUt2qljfp8eFr4ii8rgPe9ZAMkILzqI2BMCNBCjkbatDd9FWprt6M4SSwyZ2xa3_mkxpGHCVs4dmDbpSy5C_fTNDN6_jsmDXA-Qs)

Shutterstock

- **Private Key:** A secret, complex password (e.g., `8f...e9`). It proves you own your funds and is used to _sign_ (authorize) transactions. **It must be kept secret.**
    
- **Public Key:** Derived from your private key. It can be shared publicly and is used to _verify_ your signature.
    

### What is a wallet address?

A shorter, more user-friendly string of characters (e.g., `0xAbC...123`) that is derived from your public key. This is the address you share with others to **receive** funds.

### How does Metamask connect to the Ethereum blockchain?

Metamask doesn't run a full Ethereum node itself. It connects to one using **RPC (Remote Procedure Call)**. By default, it uses services like Infura or Alchemy, which run full nodes and broadcast Metamask's transaction requests to the rest of the network.

### What is “Gas” in Ethereum?

Gas is the **computational fee** required to perform any operation on the Ethereum network. Every operation (from a simple transfer to a complex smart contract function) has a "gas cost," representing the amount of computational effort needed.

### What is Ether?

Ether (ETH) is the **native cryptocurrency** of the Ethereum platform. Its primary purpose is to **pay for gas fees**, thus incentivizing validators to secure the network and process transactions.

### How is Gas fee calculated?

The total transaction fee is calculated as:

Total Fee = Gas Limit $\times$ Gas Price (per unit)

- Gas Limit: The maximum amount of gas you are willing to
    
    spend on a transaction (e.g., 21,000 for a simple transfer).
    
- **Gas Price:** The cost per unit of gas, determined by network congestion (measured in 'Gwei').
    

### Why does every transaction cost Ether?

1. **To Prevent Spam:** If transactions were free, the network would be overloaded with spam.
    
2. **To Incentivize Validators:** The gas fees are paid to the network validators (in Proof-of-Stake) who spend resources to process transactions and secure the blockchain.
    

### What are the test networks available in Ethereum?

Test networks (or "testnets") are clones of the Ethereum network that use "fake" Ether (with no real-world value). They are used by developers to test smart contracts and dApps safely.

- **Sepolia:** The current, recommended testnet for application development.
    
- **Goerli:** A popular testnet that is being deprecated.
    

### How do you fund your test wallet using a faucet?

A "faucet" is a website that gives out free test Ether for a specific testnet. You find a faucet for your chosen network (e.g., "Sepolia faucet"), enter your public wallet address, and the faucet will send you a small amount of test ETH.

### What is the difference between a real and test network?

- **Real Network (Mainnet):** This is the live, public Ethereum blockchain. The Ether (ETH) used here has **real monetary value**.
    
- **Test Network (Testnet):** A risk-free sandbox for testing. The "Ether" here is **worthless** and is obtained for free from faucets.
    

### What is blockchain explorer (Etherscan) used for?

A blockchain explorer (like Etherscan.io) is a website that allows you to **view, search, and analyze all public data** on the blockchain. You can use it to look up:

- Transactions (by their hash)
    
- Wallet addresses (to see balance and history)
    
- Smart contracts (to read their code and interact with them)
    

### How can you view your transaction on Etherscan?

When you make a transaction, Metamask will show you a **"Transaction Hash" (txid)**. You can copy this hash and paste it into the search bar on Etherscan (or the testnet version, e.g., `sepolia.etherscan.io`) to see its status (pending, confirmed, or failed).

### What factors affect Gas prices?

**Network Congestion.** Gas prices work on a supply-and-demand basis. When many people are trying to make transactions at the same time (e.g., during a popular NFT mint), the demand for block space is high, and users "bid" against each other, driving the gas price up.

### Why is it important to understand transaction fees before deploying smart contracts?

Deploying a smart contract is a transaction, and it's a very **large and expensive** one because it involves storing a lot of code on the blockchain. You must estimate this cost (using a testnet) to ensure you have enough _real_ Ether to pay for the deployment on Mainnet.

---

## 🪙 Practical 2: Create Your Own Wallet Using Metamask for Crypto Transactions

### What is the purpose of a cryptocurrency wallet?

Its primary purpose is to **securely store your private keys**. From this, it allows you to manage your assets, sign transactions, and interact with blockchain applications (dApps).

### What are the types of cryptocurrency wallets?

- **Hot Wallets:** Connected to the internet.
    
    - _Software Wallets:_ Desktop, mobile (e.g., Trust Wallet), or browser extensions (e.g., Metamask).
        
- **Cold Wallets:** Kept offline, away from internet-based threats.
    
    - _Hardware Wallets:_ Physical devices (e.g., Ledger, Trezor) that store keys offline.
        
    - _Paper Wallets:_ A piece of paper with your private key printed on it.
        

### Explain the process of creating a new wallet in Metamask.

1. Install the Metamask browser extension.
    
2. Click "Create a new wallet."
    
3. Create a strong **password**. This password _only_ encrypts your wallet on _this_ specific device.
    
4. Metamask will reveal your 12-word **Secret Recovery Phrase (Seed Phrase)**.
    
5. **Crucially, write this phrase down on paper** and store it somewhere safe and offline.
    
6. Metamask will ask you to confirm the phrase to ensure you've saved it.
    
7. Your wallet is now ready.
    

### What is a seed phrase?

A **seed phrase** (or Secret Recovery Phrase) is a list of 12 or 24 words that acts as the **master key** to your entire wallet. It can be used to recover all your accounts and private keys on any new device.

### What is the importance of securely storing your seed phrase?

- If you lose your password _and_ your seed phrase, your funds are **lost forever**.
    
- If **anyone else** gets your seed phrase, they have **total control** of your wallet and can steal all your funds.
    
- **Never store it digitally** (in a text file, email, cloud drive, or as a screenshot).
    

### How are public and private keys generated?

Your 12-word **seed phrase** is used as the "seed" for a standard algorithm (BIP-39) that generates a **master private key**. This master key is then used to mathematically derive a virtually infinite number of individual private keys and their corresponding public keys/addresses.

### What happens if you lose your private key?

If you lose your private key (or more accurately, your seed phrase), you lose access to all funds associated with it. **There is no "forgot password" or customer support.** The funds are permanently inaccessible.

### How are transactions signed in blockchain?

When you want to send a transaction, your wallet software uses your **private key** to create a unique **digital signature** for that specific transaction message. The network can then use your public key to verify that the signature is valid and that it _must_ have come from you, all without you ever revealing your private key.

### What is the role of asymmetric cryptography in digital wallets?

It's the core technology. The public/private key pair allows you to:

1. **Prove Ownership (Authentication):** By signing transactions with your private key.
    
2. **Maintain Privacy:** By receiving funds to your public address without revealing your private key.
    

### Explain the working of a blockchain transaction from sender to receiver.

1. **Sender (You):** You create a transaction (e.g., "send 0.1 ETH to address 0x...").
    
2. **Sign:** Your wallet (Metamask) uses your **private key** to sign this transaction.
    
3. **Broadcast:** Your wallet sends the _signed_ transaction to an Ethereum node (e.g., via Infura).
    
4. **Mempool:** The node validates the transaction and puts it in the **mempool** (a "waiting room" with other pending transactions).
    
5. **Validation:** A **validator** picks your transaction from the mempool (prioritizing those with higher gas fees).
    
6. **Block Inclusion:** The validator includes your transaction in a new **block**.
    
7. **Confirmation:** The new block is broadcast and added to the blockchain. The receiver's balance is now updated.
    

### What is the difference between Metamask and Binance Wallet?

Both are non-custodial wallets. **Metamask** is the original and most widely supported wallet for Ethereum and all EVM-compatible chains. **Binance Wallet** (or Trust Wallet, which Binance owns) is heavily integrated with the Binance ecosystem, particularly the Binance Smart Chain (BSC).

### What is a smart contract address?

It's an address on the blockchain, just like a wallet address. However, instead of being controlled by a private key, it's controlled by **code** (the smart contract) that is stored at that address. You interact with the contract by sending transactions to its address.

### What is the difference between wallet address and smart contract address?

- **Wallet Address (Externally Owned Account - EOA):** Controlled by a private key held by a user. Can initiate transactions.
    
- **Smart Contract Address:** Controlled by its own code. _Cannot_ initiate transactions on its own; it can only _react_ to transactions sent to it.
    

### What is nonce in Ethereum transactions?

A "nonce" (number used once) is a counter, specific to each wallet, that starts at 0. Every transaction you send must have the next sequential nonce (0, 1, 2, 3...). This **prevents double-spending** and ensures that transactions from your wallet are processed in the order you sent them.

### What are pending, confirmed, and failed transactions?

- **Pending:** Your transaction is in the mempool, waiting to be picked up by a validator.
    
- **Confirmed:** Your transaction has been included in a block and is now permanently part of the blockchain.
    
- **Failed:** The transaction was included in a block, but it encountered an error (e.g., you ran out of gas, or a `require()` statement in a smart contract failed). **You still pay the gas fees for a failed transaction.**
    

### What are the common errors during wallet setup or transaction?

- **Wallet Setup:** Not backing up the seed phrase.
    
- **Transaction:** "Insufficient funds" (not enough ETH to pay for the transaction + gas), "Transaction reverted" (a smart contract error), or setting a "Gas limit" that is too low.
    

### How can you import an existing wallet in Metamask?

You can use the "Import Account" option in Metamask. You can import using:

1. **Your 12-word Seed Phrase:** This will restore your _entire_ wallet and all its accounts.
    
2. **A single Private Key:** This will import _only_ the specific account associated with that key.
    

### Explain hot wallets vs cold wallets.

- **Hot Wallet:** **Connected to the internet** (e.g., Metamask, a mobile wallet). Convenient for daily use but vulnerable to online attacks (phishing, malware).
    
- **Cold Wallet:** **Not connected to the internet** (e.g., a Ledger or Trezor hardware wallet). Used for long-term, secure storage. Transactions must be physically confirmed on the device.
    

### What are the security concerns in using browser-based wallets?

1. **Phishing Attacks:** Fake websites that look identical to real dApps, tricking you into signing a malicious transaction or revealing your seed phrase.
    
2. **Malicious Approvals:** Tricking you into signing a transaction that gives a smart contract "approval" to spend all your tokens.
    
3. **Browser/Computer Malware:** A compromised computer could have a keylogger or malware that steals your wallet password or data.
    

### What are gas limit and gas price parameters?

- **Gas Limit:** The _maximum_ amount of gas you're willing to use. Set to prevent a buggy contract from draining all your ETH. (e.g., 21,000 for a transfer).
    
- **Gas Price (or "Max fee per gas"):** The _amount_ (in Gwei) you're willing to pay _per unit_ of gas. A higher price = a bigger "tip" = your transaction gets confirmed faster.
    

---

## 🏦 Practical 3: Smart Contract for Bank Account (Deposit, Withdraw, Balance)

### What is Solidity?

Solidity is a **high-level, statically-typed, object-oriented** programming language specifically designed for writing **smart contracts**. It's the primary language for the Ethereum blockchain (and other EVM-compatible chains) and its syntax is heavily influenced by C++, Python, and JavaScript.

### What is a Smart Contract?

A smart contract is a **self-executing program** whose terms of agreement are written directly into code. It runs on the blockchain, making it immutable (unchangeable after deployment), transparent, and autonomous.

### What is the EVM (Ethereum Virtual Machine)?

The EVM is the **runtime environment** for smart contracts on Ethereum. It's the "global computer" that executes the contract's code (in a form called bytecode). Every node in the Ethereum network runs the EVM to validate transactions and maintain the blockchain's state.

### What are the types of Ethereum networks?

- **Mainnet:** The live, public blockchain with real Ether.
    
- **Testnets:** Public networks for testing (e.g., Sepolia, Goerli).
    
- **Private Networks:** Used by a single organization for internal development.
    
- **Consortium Networks:** A private network shared by a _group_ of trusted organizations.
    

### Explain how a smart contract works.

1. **Write:** A developer writes the contract in Solidity.
    
2. **Compile:** The Solidity code is compiled into **EVM bytecode**.
    
3. **Deploy:** The bytecode is sent (in a transaction) to the blockchain, where it's stored at a new, permanent **contract address**.
    
4. **Execute:** Anyone can now "call" the contract's functions by sending a transaction to its address, which triggers the EVM to execute the code.
    

### What is the purpose of deploying contracts on a test network?

To test the contract's functionality, security, and gas consumption in a **live, realistic environment** without **spending real money**. Since contracts are immutable, any bug deployed to Mainnet is permanent and could be catastrophic.

### What are the basic data types in Solidity?

- `uint` (or `uint256`): Unsigned (non-negative) integer. The most common type for money.
    
- `int`: Signed integer (can be negative).
    
- `bool`: `true` or `false`.
    
- `address`: Holds a 20-byte Ethereum address (e.g., `0x...`).
    
- `bytes`, `string`
    

### What is the purpose of the public, private, and view keywords?

These are **visibility and state modifiers**:

- **`public`:** The function can be called by anyone, either from outside the blockchain (externally) or by other functions inside the contract.
    
- **`private`:** The function can _only_ be called by other functions _inside_ the same contract.
    
- **`internal`:** Like `private`, but also accessible by contracts that _inherit_ from this one.
    
- **`external`:** The function can _only_ be called from outside the contract (not by other functions in the same contract).
    
- **`view`:** A function that _reads_ data from the blockchain but **does not modify** it. (e.TEST_CASE_ERROR: Internal)
    
- **`pure`:** A function that **does not even read** from the blockchain (e.g., just performs a calculation on its inputs).
    

### Explain the concept of constructor in a smart contract.

The `constructor` is a special function that runs **only once**, at the exact moment the contract is **deployed**. It's used to set initial values, such as the `owner` of the contract.

### What is msg.sender and msg.value in Solidity?

These are **global variables** available in every function:

- **`msg.sender`:** The **address** of the wallet or contract that _called_ the current function. This is the primary tool for authentication.
    
- **`msg.value`:** The **amount of Ether** (measured in Wei) that was sent along with the function call.
    

### How do you handle deposits in a smart contract?

You create a `public payable` function (e.g., `function deposit() public payable { ... }`). Inside the function, you update a `mapping` to credit the `msg.sender`'s balance with the `msg.value` they sent.

### How do you prevent unauthorized withdrawals?

By using the `require()` function to check conditions. For a `withdraw` function, you would add:

1. `require(balances[msg.sender] >= _amount, "Insufficient balance");` (Checks if they have enough to withdraw).
    
2. You also might have owner-only functions: `require(msg.sender == owner, "Not the owner");`
    

### What is a fallback function in Solidity?

A special, unnamed function that is executed if someone sends a transaction to the contract but:

1. Calls a function that **doesn't exist**.
    
2. Sends Ether directly to the contract _without_ data, and there is no `receive()` function.
    

### What is payable keyword?

A modifier that must be added to any function that is designed to **receive Ether**. If a function is _not_ marked `payable`, any transaction that tries to send Ether to it will be rejected.

### What is require() function and when do we use it?

require(condition, "Error message") is the primary way to handle errors.

It checks if a condition is true.

- **If true,** the function continues.
    
- If false, the function stops, all state changes are reverted (undone), and an error message is returned.
    
    It's used to validate inputs, check permissions, and check balances.
    

### What is the difference between call, delegatecall, and send functions?

These are low-level ways for contracts to interact.

- **`send`:** (Deprecated) A basic way to send Ether. Has a fixed gas limit and is no longer recommended.
    
- **`call`:** The modern, recommended way to send Ether or call functions on other contracts. It's flexible and forwards all available gas.
    
- **`delegatecall`:** A powerful and dangerous function. It calls another contract's code, but executes that code in the **context** (i.e., using the _storage_ and `msg.sender`) of the _calling_ contract. This is used for "library" and "proxy" patterns.
    

### What is Gas estimation and why is it important?

Gas estimation is the process of a wallet or tool (like Remix) "dry-running" a transaction to **estimate how much gas** it will cost to execute. This is shown to the user _before_ they sign, so they know the total cost of their transaction.

### How do you check transaction hash and contract address after deployment?

When you deploy a contract (e.g., in Remix), the console will log the **transaction hash** of the deployment. Once that transaction is confirmed, you can look it up on Etherscan, which will show the **"Contract Address"** that was created.

### What are possible security issues in a banking smart contract?

1. **Reentrancy:** (See below).
    
2. **Integer Overflow/Underflow:** An `uint` wrapping around from 0 to its maximum value, or vice-versa (less of an issue in Solidity 0.8+).
    
3. **Improper Access Control:** Forgetting to check `msg.sender`, allowing anyone to call sensitive functions.
    

### How can you prevent reentrancy attacks?

A reentrancy attack is when an attacker's contract calls your withdraw function, and your contract sends them Ether before updating their balance. The attacker's contract then re-enters your withdraw function, draining the contract.

Prevention (Checks-Effects-Interactions Pattern):

1. **Checks:** `require()` all conditions (e.g., sufficient balance).
    
2. **Effects:** **Update the balance in storage _first_** (e.g., `balances[msg.sender] -= _amount`).
    
3. **Interactions:** **Send the Ether _last_** (e.g., using `call`).
    

---

## 🎓 Practical 4: Student Data Smart Contract (Structures, Arrays, Fallback)

### What is a structure in Solidity?

A struct is a custom, complex data type that allows you to group several variables together. It's like creating your own "object" template.

struct Student { uint id; string name; uint grade; }

### How do you declare and use arrays in Solidity?

- **Fixed-size:** `uint[10] public grades;` (An array that holds exactly 10 `uint`s).
    
- **Dynamic-size:** `uint[] public grades;` (An array that can grow).
    
- **Usage:** You can add to a dynamic array with `.push()`, e.g., `grades.push(95);`.
    

### What is a mapping in Solidity and when is it used?

A mapping is a hash table or dictionary. It stores data as key-value pairs.

mapping(KeyType => ValueType) public myMap;

It's the most common and gas-efficient way to look up data by an ID.

Example: mapping(uint => Student) public students; This lets you instantly find a Student struct by their uint ID.

### What is a fallback function?

(See P3). A "catch-all" function `fallback() external payable { ... }` that runs when a non-existent function is called.

### What is the difference between fallback and receive functions?

- **`receive() external payable { ... }`**
    
    - This function is _only_ for **receiving plain Ether**.
        
    - It's triggered _only_ if the transaction has **no data (no function call)**.
        
- **`fallback() external payable { ... }`**
    
    - This is the general "catch-all."
        
    - It's triggered if:
        
        1. A function is called that doesn't exist.
            
        2. Ether is sent _without_ data, AND there is **no `receive()` function**.
            

### How do you deploy a smart contract on a test network?

1. **In Remix:** Open the "Deploy & Run Transactions" tab.
    
2. **Environment:** Change the environment from "Remix VM" to **"Injected Web3"**.
    
3. **Wallet:** This will prompt Remix to connect to your **Metamask**.
    
4. **Network:** Make sure your Metamask is set to the **Sepolia** testnet.
    
5. **Deploy:** Click the "Deploy" button. Metamask will pop up, asking you to confirm the deployment transaction and pay the (test) gas fees.
    

### What is the concept of Gas used per function call?

- **Modifying State:** Any function that _writes or changes_ data on the blockchain (e.g., `addStudent()`, `deposit()`) **costs gas**.
    
- **Reading State:** Any function marked `view` or `pure` that _only reads_ data is **free** if called _externally_ (e.g., from a website), but costs a small amount of gas if called _internally_ by another contract.
    

### How does Solidity handle memory and storage?

- **`storage`:** This is the **permanent** data storage on the blockchain. State variables (those declared at the top of the contract) are in `storage`. It is **very expensive** to write to.
    
- **`memory`:** This is a **temporary** data location, like RAM. It is erased after the function call ends. Function arguments and local variables are often in `memory`. It is much cheaper.
    
- **`calldata`:** A special, read-only location for external function arguments. Even cheaper than `memory`.
    

### What are events in Solidity and why are they used?

An event is a way for a smart contract to log that something happened in a cheap, accessible way.

event StudentAdded(uint indexed id, string name);

- **Purpose:** dApps (front-ends) cannot easily read data _from_ a contract. Instead, they "listen" for these events to update their UI (e.g., "A new student was just added!").
    

### What is the purpose of emit keyword?

The emit keyword is used to trigger or "fire" an event.

emit StudentAdded(newId, "Alice");

### What is inheritance in Solidity?

A contract can "inherit" all the functions and state variables from another contract using the is keyword.

contract MyContract is Ownable { ... }

This is used to import standard, reusable code, such as OpenZeppelin's Ownable contract (which provides an owner and onlyOwner modifier).

### How can multiple students be stored and accessed in a contract?

The best way is to use a `mapping` for efficient lookup and an `array` to keep track of all IDs.

Solidity

```
struct Student { ... }
mapping(uint => Student) public students; // For lookup: students[5]
uint[] public studentIds; // For iteration
```

### How to modify and update structure data in Solidity?

You access the struct in its mapping and modify its fields directly.

students[_id].name = "New Name";

students[_id].grade = 90;

### What is ABI (Application Binary Interface)?

The ABI is a **JSON file** that acts as the "user manual" for a smart contract. It defines all the functions, arguments, and events. Front-end applications (like a website) read the ABI to know how to properly format a transaction to call a function in the compiled bytecode.

### What is Remix IDE?

Remix is a powerful, **browser-based** Integrated Development Environment (IDE) for Solidity. It allows you to **write, compile, debug, and deploy** smart contracts all from your web browser, making it the perfect tool for learning.

### How can you interact with your contract after deployment?

1. **In Remix:** After deploying, a UI for your contract appears in the "Deploy & Run" tab, with buttons for all your `public` functions.
    
2. **On Etherscan:** You can use the "Contract" -> "Write Contract" tab on Etherscan to call functions.
    
3. **Via a dApp:** Build a front-end (e.g., in React) that uses a library like `ethers.js` to connect to Metamask and call your contract's functions.
    

### What are constructors and destructors in Solidity?

- **`constructor`:** (See P3) A special function that runs once at deployment.
    
- **"Destructor":** Solidity does _not_ have traditional destructors. There is a function `selfdestruct(address payable recipient)` which destroys the contract and sends its remaining ETH to the `recipient`, but it is complex, dangerous, and generally discouraged.
    

### What happens when fallback function is not implemented?

If a contract does not have a `fallback` or `receive` function, any attempt to send Ether directly to the contract (without calling a function) will **fail**.

### What is the difference between contract and interface?

- **`contract`:** A full smart contract with state variables and function implementations (code).
    
- **`interface`:** A "skeleton" of a contract. It _only_ defines the function signatures (name, inputs, outputs) but has **no code**. It's used to tell your contract _how_ to interact with _another_ contract that is already deployed.
    

### How can you estimate gas usage and transaction fee in Remix?

Remix does this automatically. When you compile your contract, the "Deploy" tab will show a "Gas" estimation. Furthermore, when you call a function, the debug console will tell you the exact `gas used` for that transaction.

---

## 🧾 Practical 5: Survey Report on Types of Blockchains and Real-Time Use Cases

### What is a centralized system?

A system where a **single authority or entity** (like a company, bank, or government) has complete control over the data and operations. Example: A traditional bank database.

### What is a decentralized system?

A system where control, data, and power are **distributed** among many participants (nodes). There is no single owner or single point of failure. Example: The Bitcoin network.

### What are the limitations of centralized systems?

1. **Single Point of Failure:** If the central server goes down, the entire system stops working.
    
2. **Censorship:** The central authority can block users or transactions.
    
3. **Lack of Transparency:** Users must trust the central authority not to misuse or alter data.
    
4. **Security Risk:** The central server is a prime target for hackers.
    

### What are the layers of a blockchain?

A common model includes:

1. **Layer 0 (Network):** The physical computers (nodes), internet, and P2P connections.
    
2. **Layer 1 (Protocol):** The core blockchain itself (e.g., Ethereum, Bitcoin) and its **Consensus Algorithm** (e.g., PoW, PoS).
    
3. **Layer 2 (Scaling):** "Off-chain" solutions that sit _on top_ of Layer 1 to make it faster and cheaper (e.g., Polygon, Optimism).
    
4. **Layer 3 (Application):** The dApps and smart contracts that users interact with.
    

### What are public, private, and consortium blockchains?

- **Public:** Anyone can join, read data, and participate in consensus (e.g., Bitcoin, Ethereum).
    
- **Private:** Controlled by a **single organization**. Permissions to read and write are restricted. Highly centralized.
    
- **Consortium (or Federated):** Governed by a **pre-selected group of organizations** (e.g., a group of banks). It's a "semi-private" decentralized solution.
    

### Give examples of public blockchains.

- **Bitcoin**
    
- **Ethereum**
    
- **Solana**
    
- **Cardano**
    

### What is Hyperledger?

Hyperledger is an open-source project hosted by the Linux Foundation. It's a "greenhouse" for building **enterprise-grade, private/consortium** blockchain frameworks. The most popular one is **Hyperledger Fabric**.

### What is Corda and R3?

- **R3:** The enterprise software company that created...
    
- **Corda:** An open-source DLT (Distributed Ledger Technology) platform. It's not a "traditional" blockchain; it's designed for businesses (especially finance) and shares data only on a "need-to-know" basis between participants, rather than broadcasting everything to everyone.
    

### What is a consensus algorithm?

A consensus algorithm (or mechanism) is the set of **rules** that a blockchain uses to get all its distributed nodes to **agree** on the state of the ledger and which new blocks are valid.

### Explain Proof of Work (PoW).

Used by Bitcoin. **"Miners"** compete to solve an extremely complex mathematical puzzle. The first miner to find the solution gets to "mine" (add) the next block to the chain and is rewarded with new coins. It's highly secure but uses an enormous amount of energy.

### Explain Proof of Stake (PoS).

Used by modern Ethereum. **"Validators"** lock up (or "stake") their own coins as collateral. The network then randomly chooses a validator to propose the next block. If they act honestly, they get a reward. If they act maliciously, their staked coins are "slashed" (taken away). It's vastly more energy-efficient.

### What is Byzantine Fault Tolerance (BFT)?

The property of a system that allows it to continue operating correctly (i.e., reach consensus) **even if some of its nodes (up to a certain limit) fail or act maliciously** (i.e., are "Byzantine").

### What is Proof of Burn (PoB)?

A consensus mechanism where miners "burn" (destroy) coins by sending them to an unspendable address. This "proves" their commitment (like spending on electricity in PoW) and earns them the right to mine.

### What is Proof of Elapsed Time (PoET)?

A consensus algorithm (used by Hyperledger Sawtooth) that uses a trusted CPU (Intel SGX) to generate a random "wait time" for each node. The node whose timer goes off first wins the right to create the next block. It's efficient but relies on trusted hardware.

### Compare PoW and PoS.

|**Feature**|**Proof of Work (PoW)**|**Proof of Stake (PoS)**|
|---|---|---|
|**Who?**|Miners|Validators|
|**How?**|Solving a complex puzzle (uses "work")|Locking up coins as collateral (uses "stake")|
|**Energy**|Extremely high|Very low (99.9%+ more efficient)|
|**Security**|Very secure (cost to attack is high)|Very secure (cost to attack is high)|
|**Example**|Bitcoin|Ethereum, Cardano|

### What is Ethereum used for?

- **DeFi (Decentralized Finance):** Lending, borrowing, and trading without a bank.
    
- **NFTs (Non-Fungible Tokens):** Proving ownership of digital art, collectibles, and more.
    
- **DAOs (Decentralized Autonomous Org):** "On-chain" organizations governed by code and token-holder votes.
    
- **Gaming:** In-game items as NFTs.
    

### Explain how blockchain is used in banking and finance.

- **Cross-Border Payments:** Making international settlements faster (minutes vs. days) and cheaper.
    
- **Trade Finance:** Creating a transparent, shared ledger for all parties in a supply chain (e.g., Maersk's TradeLens).
    
- **Tokenization:** Representing real-world assets (like stocks, bonds, or real estate) as tokens on a blockchain, making them easier to trade.
    

### Explain how blockchain can help in healthcare systems.

- **Secure Patient Records:** Creating a patient-controlled record that can be securely and instantly shared between different hospitals or doctors (with the patient's permission).
    
- **Drug Traceability:** Tracking a drug's serial number on a blockchain from the manufacturer to the pharmacy to fight counterfeiting.
    

### What are some limitations or challenges of blockchain adoption?

1. **Scalability:** Public blockchains (like Ethereum) can be slow and expensive during peak times.
    
2. **User Experience (UX):** Using wallets, managing keys, and paying for gas is still too complex for the average person.
    
3. **Regulatory Uncertainty:** Many governments are still deciding how to regulate cryptocurrency and blockchain.
    
4. **Energy Consumption:** A major concern for PoW-based chains (like Bitcoin).
    

### What is the future scope of blockchain technology?

- **Interoperability:** "Bridges" that allow different blockchains to communicate and share data seamlessly.
    
- **Tokenization of "Everything":** Representing all types of assets (from your house to a stock) on-chain.
    
- **Decentralized Identity (DID):** Giving you control over your own digital identity, rather than relying on companies like Google or Facebook.
    
- **Integration with AI and IoT:** Using blockchain to secure data from IoT devices or to create transparent AI models.