---
layout: post
title: Transaction Fees
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Transaction Fees<br />
</strong></h1>
<p>I can&#8217;t believe I&#8217;m still on week four! There are only two more lectures left for this week: Transaction Fees and Currency Exchange Markets. If you just want to simple gist of this lecture. &#8220;Whenever there is a transaction, there is likely a fee. So pay up!&#8221; Also, at this point, I know more about the Ethereum fees rather than bitcoin. I&#8217;ll try to comment more about the Ethereum fee structure soon.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a bitcoin transaction fee?</li>
<li style="text-align: left;">Who gets the transaction fee as a reward?</li>
<li style="text-align: left;">Why does the transaction fee exist at all?</li>
<li style="text-align: left;">How is this fee calculated?</li>
<li style="text-align: left;">Is there a way to send a transaction with no fee?</li>
<li style="text-align: left;">Random thought experiment.</li>
</ul>
<h3>Fees, fees, fees</h3>
<p>We started the lecture by going over what is a transaction fee as defined by bitcoin. <strong>Transaction fee</strong> is the total value of coins that go into a transaction minus the total value of coins outputted. Well, to be honest that doesn&#8217;t tell me very much. I&#8217;ve gathered from this that the total coins outputted must be less than the coins inputted else the transaction cost would be negative or zero which does not make sense. This feed is given to the miner who includes the transaction into their block.</p>
<h3>Why do fees exist?</h3>
<p>Basic answer is &#8220;there is no such thing as a free lunch&#8221;. Every Economics teacher (and actually random math/comp sci teachers) has quoted that phrase to me. I&#8217;m sure you have heard it as well. Where&#8217;s the <strong>lunch</strong>?</p>
<p><img alt="no free lunch" class="aligncenter size-full wp-image-154" src="https://i0.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/04/sandwich.jpg?resize=400%2C300" /></p>
<p>Your transaction, of course. Why should someone put it into the blockchain for free? There are costs incurred to relay your transactions. A miner&#8217;s block is slightly larger to include your transaction. As with many things in bitcoin, you have the power to choose your own fee. You can choose no fee or pay a higher amount to further incentive miners to incorporate your transaction. If you choose to pay no fee, have no fear (maybe). According to<a href="https://en.bitcoin.it/wiki/Free_transaction_relay_policy"> bitcoin.it</a>, there is a <strong>&#8220;Free transaction relay policy&#8221;</strong> in place. To be a part of this, the node must be connected to Lightfoot Hosting&#8217;s node, which relays indiscriminately. The site linked contains the exact instruction though.</p>
<p>Side note: I tried looking up Lightfoot Hosting. There is a place Lightfoot, Virginia as well as there is a host service. That is all I can comment about for now.</p>
<p><strong>Breakdown of costs to relay transaction</strong></p>
<ul>
<li>peer to peer network</li>
<li>miners to record transaction</li>
<li>fee to just run a node</li>
</ul>
<p>I&#8217;m sure the numbers listed in the video are outdated but I&#8221;ll throw them up anyway as well as get an updated list.</p>
<p><strong>Current consensus feeds (2015)</strong><br />
<strong>No fee if</strong></p>
<ul>
<li><strong>transaction has less than 1000 bytes</strong></li>
<li><strong>all outputs are .1 BTC or larger</strong></li>
<li><strong>large enough priority</strong></li>
</ul>
<p><strong>Priority </strong> defined to be (sum of input age * input value) / (transaction size) or basically the longer a transaction is unspent the more it ages and increases the priority.</p>
<p>Otherwise the default fee is .0001 BTC per 1000 bytes. Just for from stats, most transactions are approximately 400 bytes: 148 bytes per input, 34 bytes for each output and ten bytes for other information.</p>
<p><strong>Now fast forward to April 2017:</strong></p>
<p>I have not seen information contradicting the free transaction so I&#8217;ll say for now they are still in place.</p>
<p>The cheapest fee is 220 Satoshis/byte so an average fee with a transaction size of 226 bytes is 50,000 Satoshis. Remember a Satoshi is 1.e- BTC. This information I got from <a href="https://bitcoinfees.github.io/">bitcoinfees</a>.</p>
<p>Per <a href="https://www.reddit.com/r/Bitcoin/comments/5om9yo/what_is_the_current_average_transaction_fee_in/">reddit</a> , they post the price at  $.15 and remember bitcoin is around $1000. Yes it&#8217;s higher than that today almost $1300.</p>
<p>There is a <a href="https://bitcoinfees.github.io/">bitcoinfees</a> website that seems to be up to date as well as one at <a href="https://statoshi.info/dashboard/db/fee-estimates">satoshi.info</a>.</p>
<p>Again, not all of this is set in stone. The lecture makes this sound like guidelines. It is up to the miners to follow or not follow this.</p>
<h3>Random Though Experiment</h3>
<p>One thought experiment I had was what happens when the reward to mine a block goes to zero. Will the transaction cost have to some minimum amount to ensure that the transaction can still be persisted into the blockchain? My conclusion is that this time point in the future is so far in the future that perhaps new technology will be in place. Things like Raiden lightning may impact this if they become an intermediary layer for the actual blockchain. Another thought was if the bitcoin reward is decreasing logarithmic then perhaps the transaction fee would rise and stabilize to some transaction fee. There will definitely be a time at which the transaction fee will be greater than the reward.</p>