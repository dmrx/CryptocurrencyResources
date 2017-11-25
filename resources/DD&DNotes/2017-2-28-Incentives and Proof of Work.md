---
layout: post
title: Incentives and Proof of Work
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<p>These are my notes of the ninth lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017. The lecture answered quite a bit of my questions regarding mining. Prior to this lecture, I knew that people mined by doing some heavy computational. Now, after learning about the background regarding incentives, it actually seems more reasonable. I was most shocked to realize that there will be only <strong>21 million bitcoin</strong> create ever unless people change the rules. </p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">High level, how does incentives help?</li>
<li style="text-align: left;">What are block rewards and how does the reward gained change?</li>
<li style="text-align: left;">What are transaction fees and how do they change?</li>
<li style="text-align: left;">What is PoW and PoS  and not Prisoner of War and Point of Service?</li>
<li style="text-align: left;">How frequently are block created?</li>
<li style="text-align: left;">What is a nonce? How is it used?</li>
</ul>
<p>In the previous section looked at the consensus algorithm.</p>
<p>This lecture discussed a second part of Bitcoin&#8217;s decentralization called incentive engineering. What does this incentive engineering mean besides sounding like fancy name for treats?</p>
<p>Previously, it was discussed that there was a assumption that at least 50% of the nodes were honest and that one is able to pick a random node. Also, we would know if there was a Sybil attack as each of the nodes created by the Sybil would still be tracked to only a single user.</p>
<p>Assumption of honesty is problematic especially if there is financial incentive to subvert the system. Since nodes don&#8217;t have identities, one is unable to penalize the group that creates the malicious blocks. </p>
<p><strong>Can we reward the blocks on the long standing chain?</strong> Yes. Use BitCoins to incentive the nodes that created these blocks</p>
<h4>Two Incentive Mechanisms in Bitcoin</h4>
<h5>Incentive 1: Block Reward</h5>
<p>Simply, you get bitcoin for creating a block. The amount of bitcoin you get changes over time. Actually according to < href="http://www.bitcoinblockhalf.com/">BitcoinBlockHalf</a>. The coin reward is currently 12 and it will drop to 6 in 2020.</p>
<p>The block creator only gets to collect the reward only if the block ends up on the long-term consensus branch! Thus one is incentivized to behave honestly and to agree.</p>
<p>There is finite supply of bitcoin: 21 million<br />
Block reward is how new bitcoins are created<br />
Runs out in 2140. No new bitcoins unless the rules will change</p>
<h5>Incentive 2: Transaction Fees</h5>
<p>The second way is via transaction fees. This mechanism made more sense to me given that when you trade at least on financial markets you have to pay some amount for the processing. Thus the nodes who are doing this service can choose to take some amount for doing the transaction. From looking at things like Ethereum with gas, this is used as well and there exists a market value to see what the transaction price should be set as. If you give more than your transaction will be picked up faster. </p>
<h4>Remaining problems</h4><ul>
<li>How to pick a random node?</li>
<li>How to avoid a free-for-all due to reward</li>
<li>How do you avoid Sybil attacks? We made an assumption earlier</li>
</ul>
<p>Then he started talking about something called Proof of Work. That peaked my interested since almost every bitcoin blog/youtube channel talks about this versus Proof of Stake. </p>
<h4>Proof of Work</h4>
<p>This is supposed to answer how to select a random node. The node will be selected in proportion to a resource that nobody should be able to monopolize on it. </p>
<p><strong>Proof of Work</strong> &#8211; resource for giving nodes power is computing power<br />
<strong>Proof of Stake</strong> &#8211; resource for giving nodes power is currency ownership</p>
<p>My thought was, wouldn&#8217;t someone be able to monopolize on ownership? Like is the actual answer, more is power. Well first let&#8217;s talk about what proof of work means.  </p>
<p><strong>select nodes based on computing power?</strong></p>
<ol>
<li>Select nodes in proportion to computing power</li>
<li>Let nodes compete for right to create block</li>
<li>Make it moderately hard to create new identities<br />
(Attacks on identity creation and on the Sybil attack)</li>
</ol>
<p>Let&#8217;s look at a more concrete example. I agree it sounds vague and I&#8217;m lost. Though looking at the next slide that just says hash puzzle and has the words nonce&#8230; this does not look that illuminating.</p>
<p>Nonce &#8211; specific number (Again, according to Merriam-Webster: the one, particular or present occasion)</p>
<p>So bitcoin achieves Proof-of-Work using hash puzzles. I&#8217;ll talk more about the hash puzzle further down. </p>
<p>To create a block to add to the block chain, you need to find &#8220;nonce&#8221; such that H(nonce | prev_hash | tx| tx&#8230;|tx) is very small. </p>
<p> (nonce | prev_hash | list of trxn that comprise the block)</p>
<p>Then take the hash of this whole, long string.</p>
<p>Then the hash if correct, should be a very small number . By very small, I mean that it falls within a certain target space in relationship to the output space of the hash. </p>
<p>If the hash function is secure, the only way to succeed to try enough nonces until you get lucky. The reason for the nonce is that you want to make it moderately difficult. </p>
<p>This is the computational puzzle that the node is required to create a new block.</p>
<p>Proof of Work Properties:</p>
<ol>
<li>Difficult to compute<br />
Aug 2014: about 10^20 hashes/block<br />
only some nodes other to compete &#8211; miners</li>
<li>Parameterizable Cost<br />
Nodes automatically re-calculate the target every two weeks<br />
average time between blocks = 10 minutes</li>
<li>Easy to verify &#8211; once you find the nonce, everyone else can check. Thus no need to have centralization since other miners will verify another miner.</li>
</ol>
<p>What this means is that if you&#8217;re a miner, and you&#8217;ve put in some capital, over a two week period, there should be more blocks found. Thus you constantly need to put in more hardware investment  to find more blocks.</p>
<p>Prob(Alice wins next block) = fraction of global hash power she controls.</p>
<p>If blocks came close together, there would be less efficient. We like putting hundreds of transactions into the block.</p>
<h5>Key Security Assumption</h5>
<ul>
<li>attacks infeasible if majority of miners weighted by hash power follow the protocol (honest)</li>
<li>
if the majority are honest, because of the competition of competing for block then you know they will come from an honest node</li>
</ul>
<h5>Solving hash puzzles is probabilistic</h5>
<p>Need to try them one by one to hope one succeeds</p>
<p>Bernouilli Trials<br />
Poisson Process should shows this exponential distribution</p>
<p>for a individual miner:<br />
mean time to find block = 10 min/fraction of hash power</p>
<p>Proof of work is a way to </p>
<ul>
<li>Select nodes in proportion to computing power</li>
<li>Let nodes compete for the &#8220;right&#8221; to create blocks</li>
<li></li>
</ul>
<p>A block in the block chain was found at time t. What is the probability that the next block was found at or before t+10 min? Assume that the total hash power of the network stays constant.</p>
<p>More than 50%</p>