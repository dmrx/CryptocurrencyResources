---
layout: post
title: Bitcoin Blocks
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Bitcoin Blocks</strong></h1>
<p>This lecture talks about what bitcoin blocks are actually composed of in respect to the innards and what the code version may look like. If you&#8217;re wondering, it is <strong> transactions</strong> but it&#8217;s not that simple. The transaction are stored in an efficient fashion. They can be visualized pretty easily from a variety of sources.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">Why does bitcoin bundle transactions?</li>
<li style="text-align: left;">What are the two major data structures that the bitcoin block chain is composed with? Describe them.</li>
<li style="text-align: left;">Where can you observe block contents?</li>
<li style="text-align: left;">What is a coin base transaction</li>
</ul>
<h2>Why bundle transactions together?</h2>
<ul>
<li>single unit of work for miners</li>
<li>limit length of hash-chain of blocks which equals faster verification of history</li>
<li>too much overhead would be created if you did it per transaction</li>
<li>allow the hashed chain for blocks to be shorter because you only need one block for multiple transactions</li>
</ul>
<p>Bitcoin blockchain has two data structures: <strong>hash chain of blocks</strong> and a <strong>merkle tree</strong>.<!-- I will first describe these structures with words and then put in an infographic that will clear up any remaining confusion.--></p>
<p>First, the bitcoin block structure contains a hash chain of blocks. A <a href="http://www.deltadeltaandmoredeltas.com/cryptographichashfunction/">hash chain</a> is that list of blocks where each block also contains a reference to the block previous to it.</p>
<h3>A block contains three items:</h3>
<ol>
<li>block header</li>
<li>hash pointer to transaction data</li>
<li>hash pointer to the previous block in the sequence</li>
</ol>
<p>At this point, even though you don&#8217;t know what the hash of the transaction data completely refers to, this structure should sound just like a linked list. When I say hash of some transaction data, I&#8217;m referring to that second data structure called a <a href="https://en.wikipedia.org/wiki/Merkle_tree">merkle tree</a>. The merkle tree contains all the transactions included within the block. Merkle tree as you might guess looks like a tree specifically a binary tree. The tree contains all the transactions hashed in the leaves. Each node above that contains the hash of the two children that gets concatenated together. The root of the tree, the final node that combines the left and right children is the root hash. This is called the &#8220;merkle root&#8221;. The merkle root gets stamped on the block header.</p>
<p>I think of the Merkle tree as an efficient transaction storage tree that utilizes hash functions and allows one to verify if a transaction is within the block (tree) in just log(n) where <i>n</i> is the number of transactions in the block. Also, once the tree is computed, it&#8217;s easy to tell whether the data has been tampered with.</p>
<p>Right so now that we know what the structure looks like, what do you see if you looked at the written blocks. As I mentioned earlier, a block contains three components: block header, hash pointer to transaction data, and a hash pointer to the previous block in the sequence.</p>
<p><strong>Sample block header</strong><br />
<code><br />
"hash": "000001aad2",<br />
"ver"": 2.<br />
<strong>"prev_block": 00001a3",</strong><br />
"time": 139.<br />
"bits": 411900,<br />
"nonce": 459841,<br />
"mrkl_root": "89776..."<br />
<code></code></code></p>
<p><strong>all the transaction data</strong><br />
<code><br />
"mrkl_root": "89776...",<br />
"n_tx":354,<br />
"size" 181520,<br />
"tx": [<br />
]<br />
"mrkl_tree":[]<br />
}<br />
</code></p>
<p>If you go to <a href="https://blockchain.info/block/000000000000000001b8f7155494bd9976ed2cdf104d56f9de6123e0a4962800">blockchain.info</a>, you can easily see records of these blocks. There are quite a few places to view bitcoin blocks. I&#8217;ve listed a few more below.</p>
<ol>
<li><a href="https://blockexplorer.com/">Block Explorer</a></li>
<li><a href="https://insight.bitpay.com/">Insight</a></li>
<li><a href="http://blockr.io/">Blockr</a></li>
</ol>
<p>This <a href="https://www.cryptocoinsnews.com/block-parser-how-read-bitcoin-block-chain/">CryptoCoinNews article </a>site teaches you to code a quick Python script to write your own block parser. It&#8217;s sparse without any UI but it&#8217;ll get the job done. Definitely give kudos to <em><a href="https://github.com/tenthirtyone/blocktools">tenthirtyone</a>.</em></p>
<p><a href="https://blockchain.info/block/000000000000000001b8f7155494bd9976ed2cdf104d56f9de6123e0a4962800">Here&#8217;s the link to block that I&#8217;m going to explain further </a></p>
<p>You can see that this is block numbered 456842. As mentioned previous the header contains the hash. Also, it contains the previous block hash linked as well as the Merkle Root hash.</p>
<p><img alt="Block Header" src="https://i1.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/currentHash.png?resize=660%2C258" /></p>
<p>That&#8217;s just the beginning looking at this block since block chain pulls out all the components. The number of transactions is 202 transactions where the nonce was 3378386187. Remember the nonce was that small target value that the miner found which enabled them to write the next block.</p>
<p>When I looked at these there were a few values that were interesting specifically block reward and the first transaction listed.</p>
<p><img alt="" class="alignnone size-full wp-image-115" src="https://i2.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/blockreward.png?resize=660%2C52" /></p>
<h4>What is a block reward?</h4>
<p>A block reward is how much a miner gets getting the privilege to publish the next block. This value is $14,737.28. How was that value calculated? Currently the number of bitcoin a miner earns for publishing a block is 12 BTC. I looked at <a href="http://www.bitcoinblockhalf.com/">Bitcoin block half</a> which shows the current block reward and the next time the change is going to occur.</p>
<p><img alt="New Coin" src="https://i0.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/newlyCreatedCoin.png?resize=660%2C262" /></p>
<h4>Why does this transaction have the message &#8220;No Inputs(Newly Generated Coins&#8221;?</h4>
<p>Ok, that sounds like a dumb question. It clearly indicates that this is a newly generated coin, which not surprising is called a <strong>coinbase transaction</strong>.</p>
<h5>Unique characteristics of the <strong>coinbase transaction</strong></h5>
<ol>
<li>has a single input and single output</li>
<li>input doesn&#8217;t redeem a previous output and thus contains a null hash pointer</li>
<li>value is fixed and halves every 210,000 blocks</li>
<li>special arbitrary parameter where one can put anything</li>
</ol>