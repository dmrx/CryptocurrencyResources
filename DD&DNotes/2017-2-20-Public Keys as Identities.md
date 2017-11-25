---
layout: post
title: Public Keys as Identities
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2 style="text-align: center;"><strong>Public Keys as Identities</strong></h2>
<p>These are my notes of the third lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017. This was a fairly brief lecture. A simple idea explained: digital signatures enables the use of public keys as identities.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What does &#8220;Public Keys as Identities&#8221; even mean?</li>
<li style="text-align: left;">How do you create an identity in this context?</li>
</ul>
<h4>Public Key == an Identity</h4>
<p>Having a public key as an identity means that you can use the public key being used as a reference to some individual or body. Digital signatures enables this because one has the ability to verify the validity of a message based on the public key, message, and signature.</p>
<p>Thus, if you see signature such that verify(pk, msg, signature) [think of it as pk says, &#8220;[msg]&#8221;]</p>
<p>So in more concrete terms, there&#8217;s a public key named Alex and a msg &#8220;Hi&#8221;. Alex says, &#8220;Hi&#8221;<br />
to &#8220;speak for&#8221; ok, you must know matching secure key (key)</p>
<p>Basically no one else can verbally speak for another person unless they&#8217;re that person or if you&#8217;re rich and famous then you have someone who tweets for you with your permission.</p>
<h4>How to make a new identity</h4>
<p>create a new, random key-pair (sk, pk) by just calling a function generateKeys()</p>
<p>pk is the public &#8220;name&#8221; (implement this with Hash(pk))<br />
sk lets you &#8220;speak for&#8221; identity</p>
<p>So you control the identity, because only you know sk and since pk &#8220;looks random&#8221;, nobody knows who you are</p>
<p>One can use a new identity each time they create a message if they want. The downside is that it is possible at some point someone can group all these transactions together if they&#8217;re over a certain period of time.</p>
<h5>Decentralized identity management</h5>
<p>anybody can make a new identity<br />
no central point of coordination</p>
<p>In common terms, there would be no need for a Social Security office required.<br />
Bitcoin address -&gt; public key/hash(public key)</p>
<h5>Privacy?</h5>
<ul>
<li>addresses not directly connected to real-world</li>
<li>observer can link together an address&#8217;s activity over time, make inferences</li>
</ul>