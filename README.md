# blockchain
A blockchain is a decentralized, distributed digital ledger that securely records transactions across a network of computers. In C++, a blockchain is typically built using object-oriented programming (OOP) structures, where each "Block" is represented as an instance of a class or struct.
Blockchain
a digital ledger in which transactions made in bitcoin or another cryptocurrency are recorded chronologically and publicly.

In more general terms, it’s a public database where new data are stored in a container called a block and are added to an immutable chain (hence blockchain) with data added in the past. In the case of Bitcoin and other cryptocurrencies, these data are groups of transactions. But, the data can be of any type, of course.

Blockchain technology has given rise to new, fully digital currencies like Bitcoin and Litecoin that aren’t issued or managed by a central authority. This brings new freedom to individuals who believe that today’s banking systems are a scam or subject to failure. Blockchain has also revolutionized distributed computing in the form of technologies like Ethereum, which has introduced interesting concepts like smart contracts.

In this article, I’ll make a simple blockchain in less than 50 lines of Python 2 code. It’ll be called SnakeCoin.

We’ll start by first defining what our blocks will look like. In blockchain, each block is stored with a timestamp and, optionally, an index. In SnakeCoin, we’re going to store both. And to help ensure integrity throughout the blockchain, each block will have a self-identifying hash. Like Bitcoin, each block’s hash will be a cryptographic hash of the block’s index, timestamp, data, and the hash of the previous block’s hash. Oh, and the data can be anything you want.


Awesome! We have our block structure, but we’re creating a blockchain. We need to start adding blocks to the actual chain. As I mentioned earlier, each block requires information from the previous block. But with that being said, a question arises: how does the first block in the blockchain get there? Well, the first block, or genesis block, is a special block. In many cases, it’s added manually or has unique logic allowing it to be added.

We’ll create a function that simply returns a genesis block to make things easy. This block is of index 0, and it has an arbitrary data value and an arbitrary value in the “previous hash” parameter.


Now that we’re able to create a genesis block, we need a function that will generate succeeding blocks in the blockchain. This function will take the previous block in the chain as a parameter, create the data for the block to be generated, and return the new block with its appropriate data. When new blocks hash information from previous blocks, the integrity of the blockchain increases with each new block. If we didn’t do this, it would be easier for an outside party to “change the past” and replace our chain with an entirely new one of their own. This chain of hashes acts as cryptographic proof and helps ensure that once a block is added to the blockchain it cannot be replaced or removed.


That’s the majority of the hard work. Now, we can create our blockchain! In our case, the blockchain itself is a simple Python list. The first element of the list is the genesis block. And of course, we need to add the succeeding blocks. Because SnakeCoin is the tiniest blockchain, we’ll only add 20 new blocks. We can do this with a for loop.


Let’s test what we’ve made so far.

Press enter or click to view image in full size

Don’t worry. It goes up to 20.
There we go! Our blockchain works. If you want to see more information in the console, you could edit the complete source file and print each block’s timestamp or data.

That’s about all that SnakeCoin has to offer. To make SnakeCoin scale to the size of today’s production blockchains, we’d have to add more features like a server layer to track changes to the chain on multiple machines and a proof-of-work algorithm to limit the amount of blocks added in a given time period.

If you’d like to get more technical, you can view the original Bitcoin whitepaper here. Best of luck and happy hacking!
