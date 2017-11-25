---
layout: post
title: Consensus without Identities
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<p>These are my notes of the eighth lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017. While the lecture is lengthy and I had to watch it a few time to grasp the concepts, I thought it was interesting.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is bitcoin&#8217;s stance on node identity? Why?</li>
<li style="text-align: left;">What is a Sybil attack?</li>
<li style="text-align: left;">What is implicit consensus?</li>
<li style="text-align: left;">What are some attacks discussed that this consensus protocol protects against?</li>
<li style="text-align: left;">What is an orphan block?</li>
<li style="text-align: left;">What is a zero-confirmation transaction and how to prevent it?</li>
</ul>
<p>One major point was that bitcoin nodes do not have persistent long-term identities. Because of this, the consensus protocol attributes deviate from what is in the distributed systems consensus protocols. So, while we know that bitcoin is different, why exactly do we care? One thought is that because of this deviation, does this mean the existing algorithms are not compatible and thus something new have to be invented? Why are identities useful for distributed consensus protocols?</p>
<p>Below are the specific examples provided in the lecture:<br />
Pragmatic: some protocols need node identification (id) such as a protocol could say use the lowest ranked ID to do .<br />
Security: assume less than 50% malicious nodes for this protocol to work.<br />
Prevent from a <strong>Sybil Attack</strong> An adversary makes multiple nodes and uses them to break the system.</p>
<p>Why don&#8217;t Bitcoin nodes have identities?</p>
<ol>
<li>Since Bitcoin is a P2P system, no central body to assign identities to nodes</li>
<li>Pseudo-anonymity is actually an inherent gol of bitcoin</li>
</ol>
<p>So instead of that, Arvind suggested something weaker in that the system is able to pick a random node in the system as well as determine who is the owner thus making the all Sybils get a single token. With this procedure then something called <strong>implicit consensus</strong> can occur.</p>
<h4>Implicit Consensus (AKA Simplified Bitcoin Consensus algorithm)</h4>
<p>It&#8217;s a procedure of adding new blocks to the blockchain in consensus.</p>
<ol>
<li>Random node is selected and make it</li>
<li>proposed the next block in the chain</li>
<li>Other nodes accept or reject the block by determining whether or not to build on top of it</li>
<li>If accept, then this block gets added. If reject, they ignore the block and build over the current chain they have.</li>
<li>Nodes acceptance means adding the block&#8217;s hash in the next block they create</li>
</ol>
<h5>Why does this work? or how can a malicious adversary subvert the process?</h5>
<ul>
<li>Stealing Bitcoin &#8211; not if the underlying crypto is good</li>
<li>Denial of Service Attack &#8211; not unless all other nodes are malicious</li>
<li>Double-spend attack &#8211; add the heuristic that only add to the longest block</li>
</ul>
<p>Can Alice simple steal Bitcoins belonging to another user at a different address that she doesn&#8217;t control?<br />
Example:<br />
It is not Alice&#8217;s turn to propose the next block in this chain.<br />
She can&#8217;t steal other bitcoins because she can&#8217;t forge their signatures and thus if the underlying crypto is solid, one cannot simple steal Bitcoins</p>
<p>If she hates a node Bob, she can choose not to accept any blocks proposed by Bob. So she&#8217;s denying service to Bob.</p>
<p>Thus if Bob&#8217;s block doesn&#8217;t make it into the next block Alice proposes, he will just wait another block until an honest node gets the chance to propose.</p>
<p>Arvind claims this is nothing more than a little annoyance. I guess in my mind it was larger. First with this little annoyance, I see it as a delay since you&#8217;re waiting for the next honest node. The next honest node could take a very long time.</p>
<p>The last one Arvind talks about is the double spending attack.</p>
<p>Alice is a customer of a merchant and Bob is the seller.<br />
Alice goes to Bob&#8217;s website and buys for it in Bitcoins.<br />
She creates a Bitcoin transaction from her address to Bob&#8217;s address.<br />
Thus it gets broadcasted to the network</p>
<p>C_A -&gt; B</p>
<p>transaction<br />
signed by A<br />
pay to pk_B: H()</p>
<p>This transaction should have existed from a previous transaction. Thus there&#8217;s a pointer to that previous block.</p>
<p>Let&#8217;s say Alice is now proposing a transaction, decides to ignore the bock with Bob&#8217;s stuff and create a new transaction</p>
<p>transaction<br />
signed by A<br />
pay to pk_A: H()</p>
<p>Will they both end up in the long term consensus chain</p>
<p>There is an idea that the honest node will extend the longest valid branch. From the facts of the transaction, both leafs have the same number of transactions. They have the same length.</p>
<p>There is a heuristic where you choose the node that you received first. Thus there is a chance that the other block would get chosen, so what happens with Bob.</p>
<p>The chain with Bob meant that Alice got free software and Bob did not get any payment. The remainder block is called an <strong>orphan</strong> block.</p>
<p>Thus this would be a successful double spend.<br />
<strong>Zero-confirmation transaction</strong> Bob would send over the software without waiting to see if Alice&#8217;s transaction actually made it into the blockchain. It&#8217;s like giving someone a product with only seeing that they have the money in their hand and that they hadn&#8217;t actually given it to you.</p>
<p>However, instead Bob should be more careful. He should wait for more confirmations before sending the software. Because he knows that the longer chain gets chosen, then he&#8217;s in the clear if he sees that his transaction has more blocks</p>
<p>Double spend probability decreases exponentially with # of confirmation<br />
Most common heuristic: 6 confirmations</p>
<h4>Recap</h4>
<ul>
<li>protection against invalid transactions is cryptographic but enforced by consensus</li>
<li>Protection against double-spending is purely by consensus</li>
<li>You&#8217;re never 100% sure a transaction is in the consensus branch. Guarantee is probabilistic. 1- (1/2)^6 = .9844</li>
</ul>
<p>What can a malicious node do?<br />
Ignore the longest valid branch rule when proposing a new block.</p>