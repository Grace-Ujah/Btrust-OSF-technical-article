# Decentralization in Bitcoin
Before Bitcoin, many attempts to create digital money failed mainly because they relied on a trusted central point of authority for maintenance, authority and verification. This central point was a problem because it could be attacked or manipulated by malicious actors.
    Bitcoin solves this problem by distributing the job of maintenance and verification to a peer-2-peer(p2p) network of independent nodes.

    
But how does it really work? To understand it, we have to look at 2 key components: the nodes and the p2p network that connects them
What is a node in Bitcoin?


A node is a computer running the Bitcoin Network(Most times these computers have people operating them). It connects to other nodes on the network to share and receive information about transactions and blocks while implementing the bitcoin P2P protocol.


When a node is run for the first time, it connects to other nodes and downloads a full copy of the blockchain at that point in time. So that it can start receiving and validating new transactions and blocks being sent around the network. It validates these information by checking them against a set of rules to ensure they are valid before propagating them to other nodes.


#  How do nodes communicate with other nodes?


Every node connects directly to other nodes on the network, and this is how the peer-2-peer network is formed.
After a node is initiated,it uses DNS seeds which tells the new node to discover the addresses of other nodes on the network.
To connect a known peer, it starts off with something called the handshake which involves sharing information about their versions to see if they match and if they do, they both send a verack(version acknowledgement) and go on with communicating. After a connection is made the new node sends an addr message containing it’s IP address to its new connection so that they can send it to their own peers 

#  What you need to run a node


Alot of diskspace; 2TB is recommended, the current blockchain size is 872.59GB, and about 100GB is added every year
RAM; 2GB in recommendations, the current mempool. It is used to store latest txns in the mempool
Bandwith; 2+ TB/month is recommended. A node is constantly sending and receiving data from other nodes on the network and needs enough bandwidth to cover it


#  Why should you run a node?


Running your own node means you can verify your own information
It provides privacy as you don’t have to share your transactions with third parties
To support and make the network more robust because you replicate the blockchain and propagate information, improving decentralization. By default, your node only makes outbound connections(taking info from other nodes) to about 8 other node, to support the network you must enable inbound connections(giving info to other nodes).
For development, if you are a bitcoin developer

#  What are the different types of nodes


Full nodes: A full node receives a full copy of the blockchain. Therefore it can tell if a new block or transaction it receives is valid or not. It is an active participant in the network.
     Types of full node;
Archival nodes: they keep the full history of the blockchain, it can help a new node replicate the entire blockchain too
Pruned nodes: this node does not keep the full copy of the blockchain. After receiving a copy of the full blockchain, it deletes older blocks further down the chain in order to save disk space. Therefore it cannot serve new nodes.
Mining node: this node adds blocks to the blockchain by doing a specified amount of work. There are also non-full node miners, they mine by joining a mining pool.
Lightweight client: they basically read blocks and transactions from other full nodes, they can only verify a block or transaction is in the blockchain and cannot confirm that the information is valid. They minimize bandwidth space, trading off privacy and ability to verify information.
SPV: simple payment verification is a common type of lightweight client. It only receives the blockheaders of the blockchain, it allows them to keep up with what the longest chain looks like. An SPV operates trusting the assumption that a full node would not lie to it as doing that has no economic benefit for the full node.
In conclusion, nodes are the backbone of Bitcoin’s decentralization, while SPV clients offer convenience for everyday users, a full node remains the gold standard for independent verification, while also improving privacy and contributing to the robustness and decentralization of the network

