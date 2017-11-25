---
layout: post
title: Bitcoin Scripts
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Bitcoin Scripts</strong></h1>
<p>This is a continuation of the Bitcoin Transaction Basics lecture. I watched the entire third week in one sitting so some of my notes may reference previous posts. This part focuses on &#8220;Script&#8221; the aptly names bitcoin blockchain scripting language. It&#8217;s based on Forth which meant little to me but hopefully means more to others.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">Why are scripts used instead of just having a public key in transaction outputs?</li>
<li style="text-align: left;">How do you validate a transaction output?</li><li style="text-align: left;">What is the proof-of-burn script</li>
<li style="text-align: left;">What is the Pay-to-script hash?</li>
<li style="text-align: left;">Name at least four characteristics of &#8220;Script&#8221;.</li>
</ul>
<p>From the last post, &#8220;Each transaction output doesn&#8217;t specific a public key, instead it&#8217;s a script.&#8221; Know that the most import transaction type in Bitcoin is redeeming a previous transaction output by signing it with the correct key. Also, the inputs also contain scripts instead of signature as well.</p>
<p>Output: &#8220;Addresses&#8221; are really scripts<br />
Simple Script shown has 4 instructions and is called a Pay-to-PubkeyHash.<br />
<code><br />
OP_DUP<br />
OP_HASH160<br />
69e02...<br />
OP_EQUALVERFIY OP_CHECKSIG<br />
</code><br />
So the input address is also a script that gets combined with the output address<br />
Concat(in.scriptSign | out.scriptPubKey)<br />
​<br />
scriptPubKey &#8211; output script that public key by specifying address to which the public key hashes<br />
scriptSig &#8211; signature with that public key.<br />
Together, this lets you claim a public key.</p>
<p>To Verify: Concat script must execute completely with not errors</p>
<h4>Bitcoin scripting language(&#8220;Script&#8221;) History lesson</h4>
<p>h5&gt;Build for Bitcoin (inspired by Forth)</p>
<ul>
<li>simple and compact</li>
<li>support for cryptography (hash function)</li>
<li>stack-based</li>
<li>limits on time/memory</li>
<li>no looping</li>
<li>256 opcodes total(15 disabled, 75 reserved)</li>
<li>logic/datahandling</li>
<li>crypto CHECKMULTISIG</li>
<li>OP_CHECKMULTISIGN</li>
<li>verification requires t signatures</li>
</ul>
<p>Bitcoin script execution example<br />
This script basically has the sender of the coins specifying the recipient via their public key.</p>
<p><code><br />
OP_DUP OP_HASH160 &lt;pubKeyHash?&gt; OP_EQUALVERIFY OP_CHECKSIG<br />
</code></p>
<p>1,2 does data instructions ie just push it on the stack<br />
OP_DUP take the value on the top of the stack and duplicate<br />
OP_HASH160 taken the crpytographic hash of the top of the stack<br />
push the pubKeyHash? onto the stack<br />
Now we know what comes next, need to verfiy if they are equal and if equal they get consumed<br />
OP_CHECKSIG verify that the signature is valid, makes sure that the full transaction is valid</p>
<p>Steps in how the stack gets read:<br />
1. Just a data instruction to be pushed onto stack</p>
<p>2.Just a data instruction to be pushed onto stack</p>
<p>3. Next call OP_DUP means creates a copy of the top which was pubKey and place on stack</p>
<p>4. OP_HASH160 means hash that key to create hashed_pubKey<br />
5. Next you&#8217;re going to push on another intruction which is pubKeyHash<br />
&lt;pubKeyHash?&gt;</p>
<p>6.OP_EQUALVERIFY as you can infer means check if the top two instructions are equal<br />
&lt;pubKeyHash?&gt; == ?</p>
<p>7. Get the result and then does the signature verify by the instuction OP_CHECKSIG</p>
<p>8. Everything else gets taken off</p>
<p>It&#8217;s interesting that 99.9% scripts are just a simple signature script</p>
<h4>Proof of Burn script</h4>
<p>OP_RETURN<br />
script that can never be redeemed<br />
It&#8217;s provable that those costs have been destroyed<br />
OP_RETURN throws an error if ever reached<br />
The data comes after it will never be reached</p>
<h5>What&#8217;s the point of proof of burn</h5>
<p>Write arbitrary data into the block chain<br />
like putting your name or timestamp<br />
destroy a very small amount of currency into the block chain</p>
<p>AltCoins way to bootstrap other coins is by destroying bitcoin</p>
<p>Should senders specific scripts?<br />
If a consumer is ready to pay, what do they need to with bitcoin</p>
<p>Me -&gt; I&#8217;m ready to pay<br />
Company -&gt; Cool so we have this multisig which means you have to include a script requiring 2 of out 3 account managers to approve. Make sure it&#8217;s perfect or it won&#8217;t go through</p>
<p>Me -&gt; Yeah, no.</p>
<p>Instead sender can just send a has of the script that needs</p>
<h4>Pay to Script Hash instead</h4>
<p>Idea: use the hash of redemption script<br />
OP_CHECKSIG</p>
<p>OP_HASH160</p>
<p>OP_EQUAL</p>
<p>Can create a 2 step process<br />
traditional script had right has</p>
<p>redemption hash deserialized and a second check occurs</p>
<p>so you&#8217;re removing complexity from the sender and there is an efficiency gain (only need to put a hash) all the rest of the complexity in the script is pushed to the input script.</p>
<p>Since this was added after the fact, it looks kinda a screwy</p>
<p>FYI: This <a href="https://en.bitcoin.it/wiki/Script">site</a> has more information regarding he scripting language. Also this is the <a href="https://github.com/bitcoin/bitcoin">Github</a>.</p>