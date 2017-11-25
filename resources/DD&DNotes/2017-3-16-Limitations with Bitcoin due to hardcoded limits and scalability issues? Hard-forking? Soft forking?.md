---
layout: post
title: Limitations with Bitcoin due to hardcoded limits and scalability issues? Hard-forking? Soft forking?
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Limitations with Bitcoin due to hard-coded limits and scalability issues? Hard-forking? Soft forking?</strong></h1>
<p>This lecture, admittedly seemed dry. After the excitement of talking about the block chain and all the potential it has, this lecture brought us back to reality. It explained where some of the shortcomings are and what would be required to make these changes, ie hard-fork. Also, we discussed how pay-to-script-hash was a successful soft fork change.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What are these hard-coded limits?</li>
<li style="text-align: left;">What is a hard-fork?</li>
<li style="text-align: left;">What are some of the challenges faced with hard-forking?</li>
<li style="text-align: left;">What is a soft-fork?</li>
</ul>
<h3>What are these hard-coded limits in Bitcoin?</h3>
<p>Most of these limits I&#8217;ve already talked about. First, there is a 10 minute time interval between block creation. The below table indicates that other cryptocurrencies now have much shorter time intervals. Ethereum has on average 14 &#8211; 17 sec. Even, Litecoin which was launched in 2011 uses only 2.5 minutes. Another drawback is that there can only be 1 million bytes in a block. There can only be 20,000 signature operations per block. There are 100 million satoshis per bitcoin. The bitcoin mining reward is completely fixed. Lastly, only 21 million bitcoin will be created.</p>
<p>There are some throughout limits that are worth looking at as well. First that there is 1 million bytes per block and a block is created every 10 minutes. Also, each transaction have at least 250 bytes meaning that the network can only handle 7 transactions per second. That&#8217;s not very fast. Credit card companies handle significantly more such as Visa (10,000/sec) or Paypal (100/sec).</p>
<p>Other limits refer to the choice of cryptographic algorithm. There is only ECDSA/P256 signature algorithm used and at least the lecturer mentioned that cryptoprimitive might break by 2040. I discussed earlier this year that <a href="http://www.deltadeltaandmoredeltas.com/sha-1-collision-by-google-and-cwi/">SHA-1</a> has been broken. Thus that future may already be upon us.</p>
<table>
<tbody>
<tr>
<th>Cryptocurrency Name</th>
<th>Symbol</th>
<th>Creation Year</th>
<th>Time Between Blocks</th>
<th>CryptoMechan</th>
</tr>
</tbody>
<tbody>
<tr>
<td>Bitcoin</td>
<td>BTC</td>
<td>2009</td>
<td>10 min</td>
<td>SHA-256</td>
</tr>
<tr>
<td>Ethereum</td>
<td>ETH</td>
<td>2015</td>
<td>10 &#8211; 20 sec</td>
<td><a href="https://github.com/ethereum/wiki/wiki/Ethash">Ethash</a></td>
</tr>
<tr>
<td>Dash</td>
<td>DASH</td>
<td>2014</td>
<td>2 &#8211; 3 min</td>
<td><a href="https://www.dash.org/x11/">X11</a></td>
</tr>
<tr>
<td>Monero</td>
<td>XMR</td>
<td>2014</td>
<td>1 &#8211; 2 min</td>
<td><a href="https://en.wikipedia.org/wiki/CryptoNote">Cryptonote</a></td>
</tr>
<tr>
<td>Ripple</td>
<td>XRP</td>
<td>2011</td>
<td>&#8211;</td>
<td><a href="https://ripple.com/dev-blog/curves-with-a-twist/">ECDSA?</a></td>
</tr>
<tr>
<td>Litecoin</td>
<td>LTC</td>
<td>2011</td>
<td>2 &#8211; 3 min</td>
<td><a href="https://en.wikipedia.org/wiki/Scrypt">scrypt</a></td>
<td></td>
</tr>
</tbody>
</table>
<h3>How do changes occur to Bitcoin? Hard-fork? Soft-fork?</h3>
<p>A <strong>hard-fork change</strong> means that there would be a change to the Bitcoin protocol and all the software would need to be upgraded. What makes it &#8220;hard&#8221; is that the new version of the software may validate previously rejected blocks. At this point, if some nodes on the network upgrade and others do not, then potentially there may be two longest branches where one would be with the upgraded software and one with the older software. Thus the block chain will <strong>split</strong>. Every node would be segmented into one or the other version and the branches would not be joined. This is unacceptable according to the lecturer.</p>
<p>On the other hand, a <strong>soft fork</strong> makes validation rules stricter. So the hard fork was widening the requirements where soft fork is restricting it. This means that previously valid transactions are now going to be considered no longer valid. Will there be a risk of the block chain splitting as before?</p>
<p>The new version gets introduced with the soft forking change. The nodes with the new software enforce tighter rules and if the majority of the nodes switch to the new software, then the network will actively be enforcing these new rules. Once that occurs, there will be a single block chain. Let&#8217;s say that there are old miners who are mining invalid blocks because they are putting in some transactions that previous were valid but are now invalid. Their blocks will keep getting rejected and they will realize they need to upgrade their software.</p>
<h3>Soft fork example: Pay-to-script-hash</h3>
<p>Pay-to-script-hash was not present in the original version of the Bitcoin protocol. The change made it such that original pay-to-script-hashes which were previously correct were now going to be invalid. The pay-to-script-hashes in the old system would just hash one data value and check if the hash matches the specified value in the output script. The new change would do a verification to make sure the previous value of the hash also was a valid script.</p>
<h3>Proposed hard fork changes</h3>
<p>Hard fork changes as mentioned are difficult. To add new opcodes to Bitcoin, changing the hard-coded limits on block and transaction size would require a hard fork. Even some bug fixes aren&#8217;t fixed because of this issue. If you look at some new cryptocurrencies, you can see that they fixed some of the perceived issues with bitcoin.</p>