---
layout: post
title: Applications of Bitcoin Scripts: Escrow Transactions using MULTISIG
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Applications: Escrow Transactions</strong></h1>
<p>This is a continuation of the Bitcoin Transaction Basics lecture. As mentioned before, I watched the entire third week in one sitting so some of my notes may reference previous posts. This part focuses on applications of Bitcoin scripts. There was quite a bit of material so I have broken down this part into 3 parts. The first section will focus just on escrow transactions. The next two posts will cover <a href="http://www.deltadeltaandmoredeltas.com/green-addresses" target="_blank">Green Addresses</a> and Micropayments.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is an escrow transaction?</li>
<li style="text-align: left;">Why does escrow transactions appeal to people?</li>
<li style="text-align: left;">How does using bitcoin help achieve it?</li>
<li style="text-align: left;">Is this use case practical?</li>
<li style="text-align: left;">Name some companies that do MULTISIG transactions.</li>
</ul>
<h4>What is an escrow transaction?</h4>
<p>Escrow just means that when there is a trade between two people, there is a middle man who ensures both parties uphold their parts of the deal.</p>
<p>For example, say you want to buy a stuffed teddy bear from far far away. You pay the store owner and the store owner sends you the bear. How do you make sure that the store owners will actually give you the bear when they receive your money? How can the store owner make sure that they will actually receive money from you? Yes, you both could trust each other but that is unrealistic since you don&#8217;t know anything about each other. This is where the middle man comes in. Since they are in the business of trust and escrow then you have a better shot at trusting them to make sure the transaction takes place. Better yet, you don&#8217;t pay them until you&#8217;ve received your end of the deal.</p>
<p>Without the middle man, you give the money to the store owner. The store owner tells you he shipped the product.</p>
<h5>Scenario 1:</h5>
<p>You get the bear and all is well. Simple!</p>
<h5>Scenario 2:</h5>
<p>You wait 1 month. No teddy bear. You complain to the store owner who insists he sent the teddy bear. You wait 1 more month. Still no teddy bear. You&#8217;re angry and frustrated and still no teddy bear. You wait 1 more month. You find out that the store is no longer in business. You lost money and you have no teddy bear.</p>
<p>With the middle man involved, you give the money to the middle guy. The middle guy tells the store owner, I have the money. The store owner ships the stuffed teddy bear to me. I tell the middle man when I received the teddy bear. The middle man releases the money to the store owner. In this case, if you never receive the bear after 1 month, you can just cancel the transaction and get your money back.</p>
<p>With escrow is better for certain transactions!</p>
<h4>Where does bitcoin fit into this escrow situation?</h4>
<p>Same scenario. You want to buy a teddy bear from far far away. There is a special transaction called a MULTISIG.</p>
<h5>MULTISIG (think Multisignatures)</h5>
<p>You create a MULTISIG transaction that requires two of three people to sign in order to redeem the coins. Two of the people in the transactions are you and the store owner. The last in this middle man (Judge). The transaction sends the payment that you deposited only if two of the three sign it. The transaction gets put onto the block chain and then can be said to be &#8220;held in escrow&#8221;. The store owner can look to the blockchain and be convinced that you paid and decides to send the teddy bear.</p>
<h5>Scenario 1</h5>
<p>After, you say, &#8220;I got the goods&#8221;, and now the store owner and you can sign the transactions to redeem the escrowed funds. All is well and really the middle man did nothing since there was no need for them to sign anything.</p>
<h5>Scenario 2</h5>
<p>You claim &#8220;I never get the teddy bear&#8221;. Thus, you would never release the money to the store owner. The middle man has to step in and decide if the money should go back to you or to the store owner based on who they can deduce is right. If the middle person decides that you are lying and the store owner did send the bear, then the middle person and the store owner can sign the multisig to move the funds to the store owner. If the middle person decides that the store owner never sent the teddy bear, then the middle person and you can sign the multisig and move the funds back to you.</p>
<h4>Is it hard to implement?</h4>
<p>There is a CHECKMULTISIG instruction within the script language. This instruction to execute correctly says that it needs at least t out of the n public keys to be provided to be valid. In the case with the store owner, you need 2 of the three public keys.</p>
<p>Last time, I talked a bit about the Pay-to-script-hash script. The multisig is just a special type of the P2SH.</p>
<p>The <a href="http://cryptorials.io/how-to-create-and-use-a-multi-sig-bitcoin-address/">tutorial</a> from 2015 doesn&#8217;t work since the link to the actual tool to the site is expired.</p>
<h4>Is there anyone actually doing this?</h4>
<p>Yes!</p>
<p>1.<a href="https://escrowmybits.com" target="&quot;_blank">EscrowMyBits</a><br />
This site description is doing exactly what is described. There is even a judge program where people can sign up to be the judge.</p>
<p>2. Many Bitcoin Wallets use it, here&#8217;s just a few</p>
<ul>
<li><a href="https://onchain.io/" target="&quot;_blank">Onchain.io </a></li>
<li><a href="https://www.coinbase.com/multisig?locale=en" target="&quot;_blank">Coinbase MultiSig Vault</a></li>
<li><a href="https://www.bitgo.com/" target="&quot;_blank">BitGo </a></li>
<li><a href="BTC.com" target="&quot;_blank">Blocktrail </a></li>
<li><a href="https://en.bitcoin.it/wiki/Multisignature#Multisignature_Wallets" target="&quot;_blank"> Links to more companies </a></li>
</ul>