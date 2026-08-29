# How Bitcoin Actually Works: 


First off,


Before Bitcoin, digital money relied entirely on trusted mediators like banks or clearing houses, this setup had problems like double-spending, transactions being reversed, high transaction costs and a database that could be tampered with by hackers 
So, how does Bitcoin provide solutions to these problems?


# Tracking ownership without balances


There is no summed balance in Bitcoin. It is just records of money assigned to an address that has not been spent. The network calls these UTXOs (Unspent Transaction Outputs).
To make a transaction; let's say Owner 0 has some Bitcoin and wants to spend it. To do that, he has to prove he actually owns that value by providing a signature that matches the record of unspent money assigned to him. If the signature matches, Owner 0 can spend it by putting in the address of the recipient (Owner 1). This address is generated from Owner 1's public key. When Owner 1 decides to spend that Bitcoin, he will do the exact same thing: provide a signature that matches his address. Once a transaction is signed, it gets broadcast to the network as an unconfirmed transaction.


# Building a block

This is where the blockchain comes in to actually confirm everything. Transactions don't just jump straight onto the blockchain. 
First, a mining node picks a batch of these unconfirmed transactions to fill up a block (up to Bitcoin's size limit). To make a block, the miner creates a Block Header using six  pieces of data:


1.) Version number: The current software version of the Bitcoin protocol.<br>
2.) Previous blockhash: The hash of the block that came right before this one.<br>
3.) Merkle root: A single 32-byte hash that mathematically summarizes every single transaction included in this block. (If you change one character in a transaction, this root changes completely).<br>
4.) Timestamp: The current time in seconds since 1970.<br>
5.) Bits: A code that tells the computer the current difficulty target, basically how hard it is to mine the block.<br>
6.) Nonce (number used once): A starting number that begins at 0. This is the only variable the miner can change manually.<br>


# Mining: the guessing game


Right now, the block header is invalid. To make the network accept it, the miner has to solve a mathematical puzzle. The rule is simple: the final SHA-256 hash of the block header must be a number smaller than the Bits (Difficulty Target). In plain English, the hash has to start with a specific number of zeros. Because cryptographic hashes are completely unpredictable, you can't just calculate a winning hash. You have to guess. The miner hashes the header with the nonce at 0. It doesn't work. So they change the nonce to 1 and hash it again. Then 2, then 3, this takes alot of computational power to run. Mining rigs do this trillions of times a second. The exact millisecond a miner hits a nonce that creates a hash with enough leading zeros, the block is successfully made. The miner immediately shouts this winning nonce out to the network. Other nodes check the math once, see it works, and add the block to their ledger.


# Connecting the chain


This brings us to the climax: how separate blocks turn into a Blockchain, look back at the second item in the block header: the Previous Blockhash. When a miner creates Block 101, they are forced to take the exact cryptographic fingerprint of Block 100 and paste it directly inside Block 101's header. Because of this, Block 102 depends on Block 101 which depends on Block 100, all the way back to the very first block in 2009. They are mathematically welded together.


# Why you can't rewrite history


This interlocking structure is exactly why you can't cheat the system like you can with a traditional bank database. It turns rewriting history into a completely losing game. Imagine an attacker wants to go back and alter an old transaction inside Block 50. The moment they change even one digit:The Merkle Root of Block 50 changes. Because the root changed, the total Hash of Block 50 changes. Since Block 51 contains the old hash of Block 50, Block 51 becomes completely invalid. This instantly breaks Block 52, Block 53, and every single block up to the present day. To make the network accept this fake history, the attacker can't just edit a line. They have to re-mine Block 50 from scratch to find a new valid nonce. But while they are wasting time trying to redo the math for Block 50, the entire honest network is already moving forward, adding new blocks to the tip of the chain.
Bitcoin nodes are hardcoded to always follow the longest chain, the path with the most accumulated math work. To successfully pull off the fraud, a single hacker would have to out-compute the rest of the planet combined to catch up and build a longer chain. It is physically and financially impossible. Any energy they waste trying to redo old blocks is completely lost, leaving the ledger perfectly safe. 

