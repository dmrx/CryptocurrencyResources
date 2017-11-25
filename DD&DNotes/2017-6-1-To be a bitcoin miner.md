---
layout: post
title: To be a bitcoin miner
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Bitcoin Miners<br />
</strong></h1>
<p>Week 5! I&#8217;m curious if what bitcoin miners face is similar to what other digital currency miners face. With bitcoin, miners are required to store and broadcast the blockchain, validate new transactions, and they have the ability to vote by hash power on consensus. That being said, my favorite part of the lecture was just understanding some of the miner lingo.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">Who are the miners?</li>
<li style="text-align: left;">How do they operate?</li>
<li style="text-align: left;">What&#8217;s the business model like for miners?</li>
<li style="text-align: left;">What impact are miners having on the environment</li>
</ul>
<p>Also, as I&#8217;ve mentioned in previous posts, trying to mine bitcoin is likely not going to be profitable easily. It requires quite a bit of hardware and people have had their AWS accounts hacked so that people could mine bitcoin. Hmmm&#8230;. The price tag for the specific hardware is pretty pricey. Other cryptocurrencies may have more potential.</p>
<h4>How to be a bitcoin miner. Only 6 <strong>EASY</strong> steps</h4>
<ol>
<li>Join the network, listen for transactions &#8211; validate all proposed transactions</li>
<li>Listen for new blocks, maintain block chain</li>
<li>Assemble a new valid block</li>
<li>Find the nonce to make your block valid &#8211; Hard work trying to find that special number&#8230;</li>
<li>Hope and pray everybody accepts your new block</li>
<li>Profit. Repeat&#8230;</li>
</ol>
<p><strong> Who benefits from these steps</strong><br />
Steps 1-3 are useful to the bitcoin network because they are needed to maintain and thus this is where you provide!<br />
4-6 incentive aspect, meaning this is where you gain!</p>
<p>The first two steps are handled by software that you download. In the first step, the node is listening to transactions in the network and then validates it based on a strict list of rules. In the second list, you&#8217;re listening for new blocks that have already been added to make sure that you&#8217;re validating each transaction in the block and checking that the block contains a valid nonce. The next steps where you start to build a candidate block to write to the blockchain is where things get interesting. Now, you&#8217;re setting yourself up to make a contribution to the blockchain and at the same time receive some incentives for the work. Once you have assembled this block, you now need to find the nonce to make your block valid.</p>
<p>I have discussed that earlier <a href="http://www.deltadeltaandmoredeltas.com/mining-bootstrapping-and-recap/">here</a> where I spoke about hashed linked lists where each block is composed of a Merkle tree of transactions.<br />
2. Then keep trying to find a nonce</p>
<p>Parameter in the coinbase transaction:<br />
after you exhaust nonce in the block header 32 bit number<br />
then try a new nonce after incrementing the coinbase.</p>
<h3>Setting the mining difficult</h3>
<p>Every two weeks, computed:</p>
<p>next_difficulty = previous_difficulty * 2 weeks/(time to mine last 2016 blocks)</p>
<p>expected number of blocks in 2 weeks at 10 minute node</p>
<p>so over time the mining difficulty gets worse even though there is a target to make new blocks every 10 minutes</p>
<p>Time to find a block is interesting because previously it used to go from 10 min down to 5 minutes but now its from 10 min only to 8 min. Thus, this suggests that the improvement seen in those two weeks is not as much.</p>