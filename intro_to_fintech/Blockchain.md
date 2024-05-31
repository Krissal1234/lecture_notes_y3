Blockchain is immutable becuase if you make a change, the entire blockchain needs to be remined



In a blockchain, tjhere begs the question, how do we know if the person sending money for instance has the balance for it. 
- Well the benefit of storing a previous has makes it simple to go backwards, so we just need to go back and check if this person has ever been sent that money.
-

Everybiody has a copy so if you mutate it goes invalid as it wont agree with the other copies of the blockchain (risk tampering)



Whats to stop somebody to add  a transaction that spends all the money of someone?
- In order to do this, private/public key pairs are usedy


Message signature is done by encrypting the message with private key, then the public key can be used to verify the signature

So lets say we make a transaction
- From |public key| to |receivers public key|
- we sign it with our private key to get the **message signature**

We can verify a transaction using a message signature


In transactions we will not see any names, only keys


![[Pasted image 20240521124141.png]]

This adds another dependancy, now not only teh blocks must be valid, by getting the hash to start with 0000, for instance. However, the signatures for each transaction must be valid too.

If a transaction is changed, the signature becomes invalid, and the person who changed it wont have the private key behind the signature to create a new signature

**In order to create a new address, private key, is go back and come up with a new private key, you dont have to go to a centralised authority to derive a new key pair**


### Basic Concept

- **Blockchain Technology**: Think of it as a digital ledger that records transactions. Everyone in the network can see and verify these transactions, but no single person controls it. This makes it very secure and transparent.

### Current System (Centralized Repository)

- **How it Works**: Imagine you want to send a package, but instead of sending it directly, you have to send it through several middlemen. Each middleman checks the package before passing it on to the next one. This is slow, inefficient, and expensive because each middleman charges a fee.
- **Diagram**:
    - You (the participant) want to interact with the depository (where your asset is kept).
    - You can't directly access the depository. You need to go through several other participants (middlemen) first.
    - This makes the process slow, inefficient, and costly.

### Blockchain System (Shared Repository)

- **How it Works**: Now, imagine you can send the package directly to the recipient without any middlemen. This is faster, cheaper, and more efficient.
- **Diagram**:
    - All participants (like banks, suppliers, and trading platforms) can directly interact with the depository.
    - No need for middlemen, making the process faster and cheaper.

### Key Points

- **Centralized Repository (Current System)**:
    - **Disconnected Participants**: Most participants can't directly access the asset depository.
    - **Slow and Costly**: Transactions take longer and cost more because of the need for intermediaries.
- **Shared Repository (Blockchain System)**:
    - **Direct Access**: Participants can interact directly with the depository.
    - **Faster and Cheaper**: Eliminates the need for intermediaries, speeding up transactions and reducing costs.

### Real-World Example

- **Current System Example**: Sending money internationally. You might use your bank, which then interacts with several other banks before the money reaches the recipient’s bank. This process can take days and incurs fees at each step.
- **Blockchain System Example**: Using a cryptocurrency like Bitcoin. You send Bitcoin directly to the recipient without involving any banks. The transaction is faster and the fees are much lower.
### From notes, how blockchain works

All transactions are hashed. the hashes are stored in a Merkle Tree. The tree produces a single hash for all the transacteions. This is called the Merkle root
![[Pasted image 20240521131146.png]]
The header is hashed only, it contains the merkle root

This POW hash ensures that if someone tampers with a block by changing/deleting/adding a transaction then the Merkle root changes, in turn teh PoW hash of that block changes too. Since the PoW hash is used as a pointer then the chain is broken

![[Pasted image 20240521131433.png]]

![[Pasted image 20240521131456.png]]
### Merkle Trees

- A type of Binary Hash tree
- Every leaf node is labelled with a data item and every non-lleaf node is labelled with the cryptographic hash of the labels of its child nodes.
- The merkle root will change if any of the data items is changed
![[Pasted image 20240521131643.png]]![[Pasted image 20240521131657.png]]

### How mining works
Mining is required to sustain the blockchain P2P network

- Miners earn money by mining blocks

- Steps:
	- Broadcast nodes create transactions of any type
	- these are sent to the Relay nodes for broadcasting
	- Full nodes (miners) then:
		- first validate the transactions
		- Build a new block from the transaction received
		- If they successfully mine the block they broadcast it to the network and the block is added to the blockchain
		- Then they get tokens in return
	-

![[Pasted image 20240521131950.png]]
![[Pasted image 20240521132047.png]]![[Pasted image 20240521132214.png]]

PoW
is a consensus mechanism that requires participants to perform computational work
- The purpose behind this is to:
	- ensure the security and integrity of the blockchain
	- prevents spam and Denial of service attacks
	- requires significant computational effort, making tampering costly and impractical

![[Pasted image 20240521132348.png]]

### Why Do Forks Happen?

- Forks can happen if two miners (individuals who verify transactions and add them to the blockchain) solve the proof-of-work problem at the same time.
- The proof-of-work problem involves finding a hash (a cryptographic signature) with a required number of leading zeros.
- When two miners find valid hashes simultaneously, they each create a new block and broadcast it to the network.

### What Happens During a Fork?

1. **Simultaneous Block Creation**:
    
    - Imagine the blockchain as a single line of blocks.
    - Two miners add their new blocks (let’s call them Block A and Block B) to the chain at the same time.
    - This creates two different paths, or forks, in the blockchain: one path with Block A and one path with Block B.
2. **Branches Form**:
    
    - Nodes (computers in the network) now have two different versions of the blockchain.
    - Some nodes add new blocks to the chain that includes Block A, while others add blocks to the chain with Block B.
3. **Resolving the Fork**:
    
    - Eventually, one of these chains will get longer faster. This can happen because more miners start adding blocks to one chain over the other.
    - The network follows a rule to resolve this: **the longest chain wins**.
    - The longest chain is considered the valid chain because it has the most proof-of-work done.
    - Nodes will then abandon the shorter chain and adopt the longer one.

### Why Does the Longest Chain Win?

- The longest chain represents the most work done to create it, making it the most secure and reliable.
- This rule ensures the blockchain remains a single, consistent ledger.

### Diagram Explanation:

- The green block is the common starting point before the fork.
- The black and purple blocks represent two different chains created by the fork.
- As miners continue to add blocks, one chain (the black one in this example) becomes longer.
- The network eventually discards the shorter chain (the purple blocks).

### Conclusion:

- Forks are a natural part of blockchain due to the decentralized nature of mining.
- The blockchain protocol ensures that forks are resolved quickly and that the blockchain remains a single, ordered sequence of blocks.

### Example for Better Understanding:

- Imagine a queue at a store where two cashiers open their tills at the same time.
- Customers split and form two lines.
- If one cashier processes customers faster, their line will move quicker.
- Eventually, all customers will join the faster-moving line, and the slower cashier's line will become empty.
- The blockchain works similarly, where the network agrees to follow the longest chain of blocks, ensuring everyone uses the same ledger.


![[Pasted image 20240521134809.png]]![[Pasted image 20240521134838.png]]

### Relates to Byzantines Generals problem
![[Pasted image 20240521134916.png]]

this problem describes the difficulty decentralised parties have in arriving at concensus without relying ona  trusted central party
- Basically, where no membors can verify the identity of other members, how can members collectively agree on certain truths
![[Pasted image 20240521135048.png]]![[Pasted image 20240521135123.png]]![[Pasted image 20240521135230.png]]


![[Pasted image 20240521135328.png]]


#### Proof of Work Vs Proof of Stake

![[Pasted image 20240521135448.png]]

![[Pasted image 20240521135617.png]]![[Pasted image 20240521135721.png]]


### What is Fiat currency?
- Fiat currency is government issued currency that is not backed by a physical commodity, like gold or silver. The value of the fiat money is derived from the relationship between supply and demand and the stability of the issuing government, rather than the worth of the commodity backing it
- Fiat currencies are underwritten by a central bank
- A danger to fiat currency is the government printing too much of it resulting in hyperinflatinon

![[Pasted image 20240521140037.png]]![[Pasted image 20240521140127.png]]

![[Pasted image 20240521140156.png]]![[Pasted image 20240521140323.png]]![[Pasted image 20240521140405.png]]![[Pasted image 20240521140434.png]]


##### Governments do not like bitcoin since transactions cannot be traced and taxed

![[Pasted image 20240521140731.png]]