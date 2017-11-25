---
layout: post
title: Mining, Bootstrapping, and recap
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<p>These are my notes of the tenth lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What do you have to think about if you&#8217;re a miner?</li>
<li style="text-align: left;">What is hash rate?</li>
<li style="text-align: left;">What is bootstrapping?</li>
<li style="text-align: left;">What are some attacks on bitcoin?</li>
<li style="text-align: left;">Define and discuss the different types of consensus?</li>
</ul>
<p>Economics question, is it profitable for a miner to mine?<br />
The generic internet article seems to say &#8220;It depends&#8221;. I don&#8217;t think it is from reading various online posts. But before I rush into it without real proof, what exactly would be considered a profit in bitcoin.</p>
<p>The positive gains in bitcoin come from the block reward (~12 BTC) and transaction fees. This is only worthwhile if it it greater than the negative losses (costs). The losses come form all hardware (fixed costs) and operations (variable costs).</p>
<p>If mining reward (block reward + Tx fees) &gt; hardware + electricity cost -&gt; You profit!<br />
It&#8217;s not so simple because reward depends on the rate at which the miners find block whih is linked toward their hash rate to the total global hash rate.</p>
<p><strong>Hash Rate</strong> &#8211; is the speed at which a computer is completing an operation in the Bitcoin code. A higher hash rate is better when mining as it increases your opportunity of finding the next block and receiving the reward.<br />
~bitcoinsimplified.org/definitions/</p>
<p>Also, the costs will be variable depending on the Bitcoin exchange rate as well as differences other fiat currencies. Also miners technically don&#8217;t have to add the block to the larger chain, they could have a another strategy that is not being captured.</p>
<h4>Recap Section of Key Topics</h4>
<p><strong>Satoshi</strong> &#8211; smallest denomination 1e-8 BTC</p>
<p>Prior to this recap I&#8217;m jotted down my thoughts with how I understand/what I remembered.</p>
<p>Identities: they&#8217;re hard and not fixed in bitcoin. We did talk about public keys being identities in week 1 but that seems not to hold since bitcoin has pseudoanonymous nodes</p>
<p>Transactions: combined together to form a block<br />
Single transaction is signed by the one person. Then the transaction does something like transfer the coin to another. The transaction also contains a hash of the history of the previous transactions of that coin.</p>
<p>P2p: Bitcoin is a peer to peer network. When you try to determine consensus regarding the ledger, there is not specialized nodes, everyone is able to participate.</p>
<p>Block chain and consensus: The history of transactions of data structure of a hash pointer is a block chain. Consensus is what allows a block to be added on the distributed ledger</p>
<p>Hash Puzzle Mining: This is how bitcoins are created<br />
The H(nonce | prev_hash | tx | tx &#8230; )) The hash of the concatenation must be less than some target value to be considered a valid coin that gets created.</p>
<h4>Recap</h4>
<p>Identity: no real world identity required, can just create a psudoanonymous<br />
Transactions: messages that broadcast to the Bitcoin P2P network that are instructions to transfer a coin from one address to another</p>
<p>Coin &#8211; chain of transactions</p>
<p>P2P &#8211; goal to propagate all new transactions to all the new Bitcoin peer nodes, it tries its best effort<br />
The security comes from the blockchain and the consensus protocol</p>
<p>Blockchain &#8211; transaction achieves a lot of confirmations and while it will never be 100% you have a high confidence<br />
Orphan blocks &#8211;<br />
Alice 100x computing power to Bob<br />
Bob will find 1% of blocks Alice finds</p>
<p>Miners &#8211; equal benefit to the cost if they want to maintain their job</p>
<p>How deeply does distributed consensus play into bitcoin? exchange rate of the currency. ownership of coin. creation of blockchain.</p>
<p>Bitcoin has three types of consensus</p>
<ul>
<ul>
<li>value</li>
<li>state</li>
<li>rules</li>
</ul>
</ul>
<h4>Bootstrapping</h4>
<p>Bitcoin is a bootstrapped. Bootstrapping is how to get the cryptocurrency started and working/ creating a healthy mining ecosystem.</p>
<p>health of mining ecosystem -&gt;<br />
prerequisite for create largely honest bitcoin network<br />
people will only mine if the value of bitcoin is high while expenditure in dollars<br />
security of blockchain &#8211; we want to blockchain to be secure to be viable, then an adversary can&#8217;t overwhelm the process and that requires healthy ecosystem<br />
-&gt;<br />
value of the currency: if users want to buy Bitcoin trust in the security of the Bitcoin</p>
<p>Thus, there is a circular interplay meaning how does this system get started? Right, so Arvind is really really excited about this which you can tell by the fluctuations of his voice.</p>
<p>Anyway, what was time like before the dinosaurs&#8230; before bitcoin became bitcoin. This process has to be done by every altcoin. I didn&#8217;t feel like I understood the response. I got that he felt it was amazing but exactly how bootstrapping happens, I&#8217;m at a loss.</p>
<h4>Potential Attacks</h4>
<h5>What would happen if consensus failed and there was a malicious node that contained 51%</h5>
<p>steal coins from existing address?<br />
Let&#8217;s say the 51% creates an invalid block</p>
<p>Suppress these transactions<br />
from the blockchain<br />
from the P2P network</p>
<p>Change the block reward<br />
Destroy confidence in Bitcoin</p>
<h5>Can someone steal coins from existing address?</h5>
<p>Creates an invalid block with an invalid trxn. While teh attacker can pretend, other honest nodes probably won&#8217;t accept it.</p>
<p>Thus there will be a fork in the chain. With the POV from the attacker trying to sell the node. He can tell that even if its the longest branch its not correct.</p>
<p>Subverting consensus is not enough and thus not possible</p>
<h5>Can the attacker suppress some transactions?</h5>
<p>Let&#8217;s say the the 51% suppresses everything Carol does. However, the p2p network does not depend on the block chain, thus the peer to peer network will receive the broadcast and notice that Carol&#8217;s blocks are just not getting published</p>
<p>A 51% attacker can potentially:</p>
<p>Make it unprofitable for other miners to mine<br />
Change the block reward<br />
Suppress transactions from the blockchain</p>
<h5>Can the 51% attacker change the block reward</h5>
<p>No, because the attacker does not contain the Bitcoin software that the honest nodes are using</p>
<h5>What about them destroying confidence in bitcoin?</h5>
<p>behavior of not extending the longest chain<br />
then the value of the currency will fall</p>
<p>This is possible and likely if this were happen. Apparently this is the main possible threat.<br />
It&#8217;s interesting because in my opinion it reminds me of trust in the dollar versus being backed by gold or not.</p>