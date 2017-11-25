---
layout: post
title: Digital Signatures
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2 style="text-align: center;"><strong>Digital Signatures</strong></h2>
<p>These are my notes of the second lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a digital signature?</li>
<li style="text-align: left;">What are some of the requirements?</li>
<li style="text-align: left;">What are some practical implementations details?</li>
</ul>
<h4>Signature</h4>
<p>only you can sign, but anyone can verify it<br />
signature is tied to a particular document (can&#8217;t cut and paste to another doc)</p>
<p>If you had a digital signatures then this identity theft crime described below would not be possible:<br />
The scenario works as follows, a person is called and is asked a question that guarantees that they&#8217;ll say the word &#8220;Yes&#8221;. The caller (criminal) will record the person answering &#8220;Yes&#8221;. Then the criminal will use the voice recording of the confirmation for different electronic bank verifiers. This concept of cut and paste in my example is using a voice recording out of context to commit a crime. With a digital signature, theoretically one cannot take the instance of the signature out of context and use it for other, potentially nefarious, purposes.</p>
<h4>API for Digital Signatures</h4>
<p>(sk, pk) := generateKeys(keysize)<br />
sk: secret signing key<br />
pk: public verification key</p>
<p>sig:= sign(sk, message)</p>
<p>isValid := verify(pk, message, sig)</p>
<p>These different functions hit the key idea of what is a signature. You generate the key with some size (256 bits) and get two outputs: a secret key and public verify key. Next you can now sign messages which people can verify by using the public verify key and the signature. This signature is tied to a specific document (msg) in this case as well. Thus the generateKeys and sign use randomized algorithms</p>
<h4>Requirements for a Digital Signatures</h4>
<ul>
<li>able to verify valid signatures</li>
<li>unable to forge signature</li>
</ul>
<p>&#8220;valid signatures verify&#8221; &#8211; verify(pk, msg, sign(sk, msg)) == true<br />
&#8220;can&#8217;t forge signatures&#8221;<br />
adversary who:<br />
knows pk (public key)<br />
gets to see signatures on other messages of his choice then he can&#8217;t produce a verifiable signature on another message</p>
<p>Game we play with an adversary</p>
<p>Challenger (TV judge)<br />
Attacker claims that he can forge signatures</p>
<p>1. (sk, pk) generateKey<br />
2. Judge gets the secret key, the attacker gets the public key<br />
3. The attacker can get signatures on other document. He will see if he can use these the get the signature for this particular document.<br />
4. Lastly the attacker thinks he has the document, then he sends a message and a signature. Thus the challenger can now run isValid to determine is it true.<br />
5. This should not work!</p>
<h4>Practical Mentions</h4>
<p>1. Algorithms are randomized so you need a good source of randomness<br />
2. Limit on message size so instead use hash(message) to keep the message less than 256 bits<br />
3. fun trick: sign a hash pointer meaning signature &#8220;covers the whole structure&#8221;<br />
If you sign a hash pointer than the entire data structure is protected. So the entire contents of the block chain is protected.</p>
<p>Bitcoin uses ECDSA standard (Elliptic Curve Digital Signature Algorithm)</p>
<p>relies on hairy math&#8230;<br />
good randomness is essential because if you foul this up in generateKeys() or sign() then you probably leaked the private key so your &#8220;digital signature&#8221; is no longer secure.</p>