---
layout: post
title: Bitcoin Transactions Basics
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Bitcoin Transactions</strong></h1>
<p>Honestly, initially, this lecture sounded intimidating. He&#8217;s like &#8220;we&#8217;re going to talk low level, real scripts, details and structure of bitcoin scripts in a precise way&#8221;. I had flashbacks of x86 machine code taunting me. Don&#8217;t be afraid though, it was well presented and well paced.</p>
<p>Also if you watch this lecture, count how many times the word &#8220;real&#8221; gets used?</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What arguments makes transaction based ledger more suitable than account based for bitcoin?</li>
<li style="text-align: left;">What are the components of a transaction?</li>
<li style="text-align: left;">Explain the reason for a change address.</li>
</ul>
<h4>Bitcoin Consensus gives us:</h4>
<ol>
<li>Append only ledger</li>
<li>Decentralized consensus</li>
<li>Miners to validate transactions (making sure transactions are well-formed)</li>
</ol>
<p>Assuming a currency exists to motivate miners!</p>
<p>He started out with this chart of what an account-based ledger (not Bitcoin) looked like before showing the bitcoin based ledger. The issues with this account-based ledger is that everyone needs to keep track of the account balances.</p>
<h4>Transaction Based Ledger (Bitcoin)</h4>
<table>
<tbody>
<tr>
<th>Transaction</th>
<th>Input</th>
<th>Output</th>
<th>Signed</th>
</tr>
<tr>
<td>1</td>
<td>0</td>
<td>25 -&gt;Alice</td>
<td>no one</td>
</tr>
<tr>
<td>2</td>
<td>1[0]</td>
<td>17 -&gt;Bob,8 -&gt; Alice</td>
<td>signed(Alice)</td>
</tr>
<tr>
<td>3</td>
<td>2[0]</td>
<td>8 -&gt; Carol,9-&gt; Bob</td>
<td>signed by Bob</td>
</tr>
<tr>
<td>4</td>
<td>2[1]</td>
<td>6 -&gt; David,2 -&gt; Alice</td>
<td>signed by Alice</td>
</tr>
</tbody>
</table>
<p>2[1] mean transaction 2 output 1</p>
<p>This is all implemented with hash pointers which have been covered in week 1 as well as building upon it constantly. Thus by the time transaction 4 occurs, there is now a long chain. Transaction specific the number of inputs and number of accounts and thus keep track of the state.</p>
<p>For these transactions it&#8217;s important to note that when Alice gives 17 coin to Bob, she also needs to give 8 coin back to herself.</p>
<p><strong>Change Address</strong> &#8211; because coins are immutable, the entirety of a transaction output must be consumed by another transactions. The left over amount that has the potential for being given back to the original input still has a transaction to receive the coin.</p>
<p><strong>Efficient Verification</strong> This new ledger means that you do not have to go up the entire change. You only need to scan the block chain between a reference transaction (input) and the latest block.</p>
<h5>Join Payments instead of doing 2 transactions</h5>
<p>&nbsp;</p>
<table style="height: 157px;" width="581">
<tbody>
<tr>
<th>Transaction</th>
<th>Input</th>
<th>Output</th>
<th>Signed</th>
</tr>
<tr>
<td>2</td>
<td>1[0]</td>
<td>17 -&gt;Bob, 8 -&gt; Alice</td>
<td>signed(Alice)</td>
</tr>
<tr>
<td>3</td>
<td>2[1]</td>
<td>6 -&gt; Alice, 2-&gt; Bob</td>
<td>signed(Alice)</td>
</tr>
<tr>
<td>4</td>
<td>3[0], 3[1]</td>
<td>8 -&gt; David</td>
<td>signed by Alice, Bob</td>
</tr>
</tbody>
</table>
<p>There seems to be quite a few issues on the video which are mentioned below. I have changed the examples to reflect these inconsistencies.<br />
https://www.coursera.org/learn/cryptocurrency/discussions/weeks/3/threads/ngwguLVDEeatew7zqUaXxg</p>
<h2><strong>Bitcoin transaction representation</strong></h2>
<p><code><br />
{<br />
"hash": "5a42...",<br />
"ver":1,<br />
"vin_sz":2,<br />
"vout_sz":1,<br />
"lock_time":0,<br />
"size":404,<br />
"in": [{<br />
"prev_out":{"hash":"3be4",<br />
"n":0},<br />
"scriptSign":"3044"<br />
}],<br />
"out":[{<br />
"value":"10.122",<br />
"scriptPubKey":"OP_DUP OP_HASH160 69e... OP_EQUALVERIFY OP_CHECKSIG"}]}]}<br />
</code><br />
<strong>3 parts</strong></p>
<ul>
<li>Meta Data &#8211; Housekeeping that has size of trxn, # of input, # of output, and has of entire trxn<br />
<code><br />
"hash": "5a42...",<br />
"ver":1,<br />
"vin_sz":2,<br />
"vout_sz":1,<br />
"lock_time":0,<br />
"size":404<br />
</code></li>
<li>Inputs &#8211; array of previous trxn (hash form)<br />
prevTrans<br />
Signatures</li>
<li>Outputs &#8211; contain the value and the sum of all output<br />
value<br />
Recipient Address? but its really a script</li>
</ul>