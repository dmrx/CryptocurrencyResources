---
layout: post
title: Cryptographic Hash Function
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2 style="text-align: center;"><strong>Cryptographic Hash Function</strong></h2>
<p>These are my notes of the first lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a cryptographic hash function?</li>
<li style="text-align: left;">What are the security properties?</li>
<li style="text-align: left;">What are the applications of some of these properties?</li>
<li style="text-align: left;">What does SHA-256 do at a simple level?</li>
</ul>
<h4>Hash Function</h4>
<ul>
<li>takes any string as input</li>
<li>fixed size output (256 bit bitcoin uses)</li>
<li>efficiently computable (can figure out output in a reasonable amount of time)</li>
</ul>
<h4>Security Properties</h4>
<ul>
<li>collision-free</li>
<li>hiding</li>
<li>puzzle-friendly</li>
</ul>
<h5><strong>Collision-free</strong></h5>
<p>Math definition &#8211; nobody can find x and y where x != y and H(x) = H(y)</p>
<p>in words:<br />
nobody can find two different input strings so that if you apply the hash function to them, they have the same output.</p>
<p>the idea that nobody can find really means it&#8217;s really really really hard to find it&#8230;.</p>
<p>Note that there has to be a collisions<br />
since you&#8217;re going from a much larger input space <em>t</em> a fixed output space (2^256).</p>
<h5><strong>Hiding</strong></h5>
<p>Given H(x), it is infeasible to find x.</p>
<p>If r is chosen from a probability distribution that has min-entropy, then given H(r | x), it is infeasible to find x</p>
<p>High min-entropy means that the distribution is &#8220;very spread out&#8221; so that no particular value is chosen more than negligible probability.</p>
<p>in words: if you are given the hashed version of x then you will be unable to find x</p>
<h5><strong>Puzzle Friendly</strong></h5>
<p>for every possible output value y,<br />
if k is chosen from a distribution with a high min entropy (super spread out) then it is infeasible to find x such that H(k|x) = y.</p>
<p>If someone wants to target a certain hash function, get some value of y, if part of the input is chosen in a random way, it&#8217;s difficult to find another value to target the hash function value.</p>
<p>Given a &#8220;puzzle ID&#8221; id ( from high min-entropy distribution) and a target set Y:<br />
Try to find a &#8220;solution&#8221; x such that H(id|x) \in Y.</p>
<p><em>id | x means id concatenated x</em></p>
<h4>Application of having something <strong>collision-free</strong></h4>
<p>Hash becomes a message digest meaning that you can use the has as a replacement of the msg<br />
You can use H(x) and H(y) as smaller forms of the input string.</p>
<p>So if H(x) = H(y) then x = y.<br />
Technically H(x) is only 256 bits while the x can be of some large arbitrary length</p>
<h4>Application of <strong>puzzle friendly</strong></h4>
<p>Puzzle friendly property implies that no solving strategy is much better than trying random values of x</p>
<h4>Application of the <strong> hiding property</strong></h4>
<p>In words, the idea is that you want to create a secret message that you can put in a public envelope.</p>
<h4><strong>Commitment API &#8211; to help explain public envelope example<br />
</strong></h4>
<p>Want to &#8220;seal a value in an envelope&#8221; and &#8220;open the envelope&#8221; later</p>
<p>Commit to a value, reveal it later</p>
<p>(com, key) := commit(msg)<br />
match := verify(com, key, msg)</p>
<p>To seal msg in envelope:<br />
(com, key) := commit(msg) &#8212; then publish com</p>
<p>To open envelope:<br />
publish key, msg<br />
anyone can use verify(com, key, msg) to check validity</p>
<p>Want two security properties:<br />
Hiding: given com, infeasible to find msg;<br />
Binding: infeasible to find msg != msg&#8217; such that<br />
verify(commit(msg, msg&#8217;) == true</p>
<p>commit(msg) := (H(key | msg), key) where key is 256 bit<br />
verify(com, key, msg) := (H(key|msg) == com)</p>
<h4>More about the Security Properties</h4>
<p>key is a randomly generated 256 bit value</p>
<p>Hiding: Given H(key | msg) infeasible to find mg<br />
Binding: Infeasible to find msg != msg&#8217; such that<br />
H(key | msg) == H(key | msg&#8217;)</p>
<p>Basically can&#8217;t find two different messages where you committed to one and verified with another one.</p>
<p>So you use the hash function in both commit and verify</p>
<p>What hash function will we use? <strong>SHA-256</strong></p>
<h5><strong>Step by Step of what SHA-256 does</strong></h5>
<ol>
<li>You have an input message of an arbitrary length</li>
<li>You also have a 256 bit value called IV (Initialization Vector <a href="http://You also have a 256 bit value called IV (Initialization Vector) (https://en.wikipedia.org/wiki/Initialization_vector)">(https://en.wikipedia.org/wiki/Initialization_vector)</a></li>
<li>The input string gets broken up into 512 bit blocks and we&#8217;ll reference them as block_1, block_2, block_3, and block_n will be the last block. The last block will also contain padding where the last 64 bits is the length of the input message and prior to that is a 1{0*}.</li>
<li>The 256 bit value and block_1 come together as inputs to a compression function (c) which basically squashes the 768 bits back into 256 bits.</li>
<li>Next the output of c gets mashed with block_2 and to the compression function and out pops a 256 bit value.</li>
<li>This continues along the entire length of the message where the last output is Voila, the hash.</li>
</ol>