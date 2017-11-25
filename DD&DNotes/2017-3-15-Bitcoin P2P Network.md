---
layout: post
title: Bitcoin P2P Network
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Bitcoin P2P Network</strong></h1>
<p>This lecture focused on the bitcoin peer-to-peer (p2p) network. While this lecture just talked about the current network and its implementation which I will discuss,</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What are characteristics of the blockchain network?</li>
<li style="text-align: left;">How do you as an individual connect to the blockchain network?</li>
<li style="text-align: left;">What is a full node and what is a SPV?</li>
<li style="text-align: left;">What is the size of the network?</li>
</ul>
<h2>What is the blockchain network and how can people join this network?</h2>
<p>The Bitcoin P2P network is quite similar to other peer-to-peer networks. I only know a few p2p networks outside of Bitorrent which is Gnutella and e2dk. I remember that there were many issues with Gnutella regarding scalability and message propagation. Similar to other peer-to-peer networks, it has the properties that all the nodes are equal and there is no hierarchy. It uses TCP (Transmissiong Control Protocol) with a random topology. Anyone can join the network and leave the network as well. Leaving the network is easy since if the network doesn&#8217;t hear from the node for three hours, it is just assumed that it is no longer online and stops sending messages to it.</p>
<p>Again, I&#8217;m talking about the Bitcoin P2P network and as I&#8217;ll talk about later this notion of equality does not stand true for other side bitcoin networks.</p>
<h3>Key Characteristics</h3>
<ul>
<li>ad-hoc protocol (runs on TCP port 8333)</li>
<li>ad-hoc network with random topology (random nodes peering)</li>
<li>all nodes are equal (no central/master)</li>
<li>new nodes can join at any time (anyone can download and get started)</li>
<li>forget non-responding nodes after 3 hours</li>
</ul>
<h4>What does it mean that anyone can join at anytime?</h4>
<p>Well anyone can download something like <a href="https://bitcoin.org/en/download">Bitcoin Core</a> or use npm to install <a href="https://bitcore.io/guides/full-node/">Bitcore </a>and become a full node. As with any peer-to-peer network, pay attention to security, bandwidth, and actual space concerns.</p>
<h3>How does a new node connect to the network?</h3>
<p>Simple answer would be just connect to one node and then more will follow. Though, there are a few more steps then just that.</p>
<ol>
<li>Connect to a <strong>seed node</strong> with a message like, &#8220;Hello World! I&#8217;m ready to Bitcoin&#8221;. Seed nodes are hard coded IP addresses that one an use to connect to another active node. Instead of using the IP addresses, some program with use DNS seeds, which let you look up the IP addresses instead of just providing one. A few DNS seed names are <i>bitseed.xf2.org</i> or <i>seed.bitcoin.sipa.be</i></li>
<li>To first connect, send a <i>version</i> message and receive a <i>version</i> message back. Then send a <i>verack</i> to confirm the connection.</li>
<li>Send the messages <i>getaddr </i> and <i>addr </i> to the seedNode</li>
<li>Next you connect to the nodes that seedNode sends you</li>
<li>Repeat with the new nodes to be better connected.</li>
</ol>
<h3>What happens in the network?</h3>
<p>Transactions that one node hears are shared across the entire network. This is <a href="https://en.wikipedia.org/wiki/Gossip_protocol"><strong>Transaction propagation (flooding) </strong> or a gossip protocol</a>. It is a simple gossip Protocol where the network is just sending the message to every node it knows. At certain short time periods, a message gets sent to random targets in a pairwise fashion and each time, the node is responsible to update its view of the blockchain and determine whether to send the transaction outwards. Each node has its own list of pending transactions and must decide to forward or not based on a certain set of criteria. Also, like a breadth first search, it has a check to see whether it has seen a certain transaction before to prevent message from being sent forever. According to <a href="http://bitcoin.stackexchange.com/questions/40843/how-long-does-it-take-to-propagate-a-new-broadcasted-message-in-the-bitmessage">bitcoin.stackexchange</a>, it takes about 15 seconds for a message to be propagated.</p>
<p>There are a set of checks to determine whether the transaction should be propagated. Note that these checks are not enforced. They can be ignored if certain nodes have different incentives or are malicious. One check is to just make sure that the transaction is valid within the blockchain. A few of those checks are for syntactic correctness, size in bytes is less than the MAX_BLOCK_SIZE as well as the size of the output must be legal monetary range. Then, it checks whether the transaction has been seen before which it can look up into the pending transactions list. Also, it needs to check that this transaction has not been incorporated in another block or has already been spent. <a href="https://en.bitcoin.it/wiki/Protocol_rules">This site</a> has the documented protocol rules.</p>
<h3>What are some checks done to see if the node should propagate the message?</h3>
<ul>
<li>Transaction valid with current block chain</li>
<li>default script matches a whitelist (avoid unusual scripts)</li>
<li>won&#8217;t relay by default (Why not)</li>
<li>haven&#8217;t seen before (avoid infinite loops)</li>
<li>doesn&#8217;t conflict with others transactions previously relayed (avoid double-spends)</li>
<li><a href="https://en.bitcoin.it/wiki/Protocol_rules">Documented protocol rules</a></li>
</ul>
<p>It is possible that the nodes will end up with different set of pending transactions or a different ordering of the transaction events. This is called a <strong>race condition in bitcoin</strong>. Because, only one person is defining the next block, that person who is mining will break up the race condition by publishing. This usually creates a clear set of actions on how to deal with the race condition meaning that one chain may get dropped because it would be a double spend after this block has been published. Nodes will usually accept the transaction that they have received first. A similar algorithm is used for block propagation as well where more information is found <a href="https://en.bitcoin.it/wiki/Protocol_rules">here</a>. One thought you may have is what happens to these transactions or blocks that don&#8217;t get put on the main block chain. They are called <strong>orphan transaction and orphan blocks</strong> respectfully. An orphan block does not have a parent on the longest block chain. From <a href="https://blockchain.info/charts/n-orphaned-blocks?timespan=60days&amp;showDataPoints=false&amp;daysAverageString=1&amp;show_header=true&amp;scale=0&amp;address=">blockchain info</a>, one can see there are about 2-3 orphans blocks created per week.</p>
<h4>Race conditions: Transaction or blocks may conflict</h4>
<ul>
<li>default behavior: accept what you hear first</li>
<li>network positions matters then</li>
<li>miners have freedom to implement their own logic which could exacerbate these race conditions</li>
</ul>
<h4>Now, that we know what the network is doing, what is the size of the network?</h4>
<p>While, not clear how to measure it, there are between 1,000 &#8211; 10,000 fully validating nodes. A fully validating node is one that it permanently connected, stores the entire block chain, and is actively hearing and forwarding every node/transaction. They also need to track the unspent transaction output (UTXO). These are all transaction that have not been put into the blockchain. However, there are some nodes that connect in and out of the network maybe just to complete a transaction or check some status of a transactions. In July 2014, the size of the block chain was 20 GB. Now in March 2017, it&#8217;s almost 100 GB. Also, while in Jul 2014, the UTXO was only 20 MB. In July 2015, it is 650 MB.</p>
<p>The lecturer, Joseph, mentioned that that the number of full nodes are decreasing. It makes sense since as time passes, to store the chain involves more space and RAM. Unless one is miner, or part of some large organization where you are actively getting some benefit for maintaining the full node, it doesn&#8217;t seem reasonable to continue doing. I admit there are people who will continue holding the nodes because they believe in bitcoin and for those people, that&#8217;s awesome. When people have clients running on their phones, or PCs, likely it is just a <strong>lightweight node.</strong> People also refer to these nodes as <strong>Simple Payment Verification (SPV) client</strong>. Bitcoin wallet programs tend to incorporate SPV nodes. A lightweight node just stores a subset of the transactions sent that may be needed to verify certain transactions. These lightweight nodes only work because they are trusting the fully-validating nodes to do their job. There has been much discuss on the internet regarding how many full nodes are enough and who should run a full node.</p>