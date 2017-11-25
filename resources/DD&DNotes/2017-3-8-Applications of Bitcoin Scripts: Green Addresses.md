---
layout: post
title: Applications of Bitcoin Scripts: Green Addresses
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Applications: Green Addresses </strong></h1>
<p>This is a continuation of the Bitcoin Transaction Basics lecture. As mentioned before, I watched the entire third week in one sitting so some of my notes may reference previous posts. This part focuses on applications of Bitcoin scripts. There was quite a bit of material so I have broken down this part into 3 parts. This is the second part focusing on Green Addresses. Here&#8217;s a link to the <a href="http://www.deltadeltaandmoredeltas.com/escrow-transactions-using-multisig" target="_blank">first part.</a></p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a green address?</li>
<li style="text-align: left;">What problem does green addresses try to solve?</li>
<li style="text-align: left;">Why should this work?</li>
<li style="text-align: left;">Why is there some negative stigma with this?</li>
</ul>
<h4>What is the problem?</h4>
<p>Let&#8217;s start with what problem the green address is trying to solve. The goal was to try to do fast transactions for time-critical applications. Generally, bitcoin requires you to wait about 6 confirmations before knowing that your transaction has been incorporated into the blockchain. Thus, using green addresses is supposed to solve this as well as make sure that there are no double spending attacks.</p>
<p>My way of understanding green addresses was to think that the &#8220;green address&#8221; was more of a marker or reputation address which a third party holds for you. Also, I&#8217;ll walk through my example.</p>
<p>Say there is an ice cream seller (Ms. Icee) who accepts bitcoin. When the seller is online, most transactions work out well. However, she drives a truck around a neighborhood and at this point she isn&#8217;t connected to the blockchain. How can she still accept bitcoin? He will have made a deal with a respected organization (Mt Gox).</p>
<p>Suzie (prospective buyer) wants a chocolate eclair treat. She will tell Mt Gox who will withdraw from Suzie&#8217;s account using the &#8220;use green address&#8221; check point. Thus, the payment will be sent to the &#8220;green address&#8221; before forwarding it to Ms. Icee. An extra transaction to the special ECDSA keypair is made before forwarding it to the Ms. Icee. Ms. Icee can check with Mt. Gox and trust the payment because Mt. Gox is trustworthy.</p>
<p>This <strong>green address </strong> contains special trusted ECDSA keypairs that to indicate the origin of funds to a recipient. It is the Mt Gox controlled address that references Suzie. Everyone needs to trust Mt. Gox and Mt. Gox has to deliver on this.</p>
<h4>Negative Stigma</h4>
<p>However, Instawallet and Mount Gox fell apart because the transactions were compromised. While, I&#8217;m sure someone may try to implement this again, it at least is frowned upon <a href="https://en.bitcoin.it/wiki/Green_address">here.</a></p>