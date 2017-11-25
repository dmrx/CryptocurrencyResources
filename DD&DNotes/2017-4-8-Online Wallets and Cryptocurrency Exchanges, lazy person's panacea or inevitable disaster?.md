---
layout: post
title: Online Wallets and Cryptocurrency Exchanges, lazy person's panacea or inevitable disaster?
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2>Online Wallets, lazy person&#8217;s panacea or inevitable disaster?</h2>
<p>Before I begin talking about this lecture, I want to say that I feel like a hypocrite. My prior posts have talked so much about protecting your keys and trying to keep your keys disconnected from the internet. This lecture discusses on types of online cryptocurrency wallets and exchanges. Thankfully this lecture stayed consistent with the rest of the previous lectures in discussing the risks associated with storing bitcoin via this mechanism. My takeaway from all these lectures are you should keep the bulk of your cryptocurrency secured and only put coin online when you are making a transaction. This is not like the stock markets where there is a centralization and regulation in place as well as it&#8217;s difficult to shoot yourself in the foot. By that I mean, it&#8217;s difficult to accidentally transfer all your money to another person because you accidentally typed the wrong key.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is an online wallet?</li>
<li style="text-align: left;">What are the pros and cons of online wallets?</li>
<li style="text-align: left;">What is a bitcoin exchange?</li>
<li style="text-align: left;">Why doesn&#8217;t a transaction get put on the blockchain when there is specific type of trade at a bitcoin exchange?</li>
<li style="text-align: left;">Explain briefly how it works.</li>
<li style="text-align: left;">How does multi-signatures improve the system?</li>
</ul>
<h2>Online Wallet- &#8220;like a local wallet but in the cloud&#8221;</h2>
<p>That&#8217;s the tagline regarding the online wallet which is true. You manage the wallet except the information is stored on the cloud and thus you would access it through your computer or mobile app. I liken in more to internet banking. Some people may be thinking that&#8217;s amazing. This is super convenient and not tied to one location. Others may be worried about browser security and the fact there is trust with the app. Two popular sites listed in the lecture are <a href="http://coinbase.com" target="_blank">Coinbase</a> and <a href="https://blockchain.info/" target="_blank">Blockchain.info</a>.</p>
<h3>Trade-offs</h3>
<ul>
<li>convenient: nothing to install, works on multiple devices</li>
<li>but security worries if site is malicious or compromised</li>
</ul>
<p>Now instead of online wallets, there is another online service provided. The lecture spends quite a bit of time likening a Bitcoin exchange to a bank. I&#8217;m not a fan of this metaphor and would have rather they describe this process like a <strong><a href="http://www.investopedia.com/terms/f/foreign-exchange.asp" target="_blank">forex exchange</a></strong>. You deposit money into the bank and the bank promises to give you back your money. The bank takes your money and reinvests. Banks just a fraction of their total investment in cash on hand called<strong> fractional reserve</strong> so that customers can withdraw money when required. Why is this like a bitcoin exchange?</p>
<h2>Bitcoin Exchanges</h2>
<p>With a bitcoin exchange, you deposit your fiat currency of bitcoin and the exchange promises that it will return you back your money. With the money in their system, you have the ability to make and receive bitcoin payments by potentially buying another cryptocurrency or transferring money to another person. They work with trading bitcoin where one customers wants to buy bitcoin with dollars where another person may want to sell bitcoin for dollars. If these parties prices match up then a transaction will occur!</p>
<p>So now they&#8217;ll work like a generic exchange. However, there are interesting consequences to doing these deals on the exchanges given what gets written to the blockchain. If you buy BTC at the exchange by spending dollars and you buy BTC from a seller on the same exchange, this does not get written to the blockchain. The exchange did not have to go the the blockchain to accomplish this deal. The bitcoin and cash associated with the deal are still kept at the exchange. The only thing that has change is now that the bank has to give you BTC and your remaining balance back. Now you get a way to connect the BTC economy to fiat allowing for easy transfers back and forth. There are risks involved which I&#8217;ll describe below.</p>
<p><strong>What are some of the types of risk involved that both bitcoin exchanges and banks share?</strong></p>
<h3>Fiat Risk</h3>
<p>This is the fear of a <a href="https://en.wikipedia.org/wiki/Bank_run" target="_blank">bank runs</a>. A bank run occurs when all the clients want to withdraw all their money and the bank runs out of cash to give back. Now you have a bunch of angry people they can&#8217;t give you money back</p>
<h3>Trust Risk</h3>
<p>The second risk involves that the bank/exchange is run by crooks or unsavory characters. Their goal is not the allow you to lend money but instead your money.</p>
<h3>Cyber Attack</h3>
<p>Cyber attacks post a risk to any industry nowadays so it&#8217;s no surprise that exchanges and banks have to be wary of this.</p>
<h3>Exchanges: Pros and Cons</h3>
<ul>
<li>pro: connect BTC economy to fiat currency economic easy to transfer value back and forth</li>
<li>con: risk, same kinds of risks as banks ie fiat, trust, and cyber</li>
</ul>
<h3><strong>Some Troubling Stats:</strong></h3>
<p><strong>45%</strong> of Bitcoin exchanges end up closing Apr 2013 &#8211; Ian Steadman</p>
<p>Mt. Gox largest bitcoin exchange Japanese company that ended up declaring bankruptcy as well as they faced losing clients&#8217; bitcoins</p>
<p>OK, if banks and bitcoin exchanges face similar risks, what are they doing to prevent this? Why don&#8217;t banks have such a high rate of closing?</p>
<h3><strong>Bank Regulations</strong></h3>
<p>As much as people complain about bank regulation and how it is preventing trade, there is definitely merit to it. Many banks have a <strong>minimum reserve requirement</strong>. This means that while banks are allowed to take clients money and reinvest it, they need to maintain some amount in their coffers. This amount is usually some fraction of their deposits. This page contains values from the <a href="https://www.federalreserve.gov/monetarypolicy/reservereq.htm" target="_blank">Federal Reserve Bank</a>. I&#8217;d keep a ballpark answer of like 3 &#8211; 10% as a value to think about. Additionally, there are regulations in place in to control how much risk a bank takes on. Ensure that the risk is balanced or hedged in some way. This ensures that the banks assets are more secure. Governments helps banks by providing insurance.  Governments are also known to save banks by acting as lenders. This was seen during the Financial Crisis.</p>
<h3>Opportunities to manage risk by Bitcoin Exchanges</h3>
<p><strong>Proof of Reserve</strong></p>
<p>Bitcoin can prove and share with clients it has a fractional reserve again using some cryptographic tools. This should make depositers feel more protected because the exchange is effectively saying we have some percentage of bitcoin stored in house. Some exchanges even have 100% which means that they would be able to give back all money at any time. They can even prove this publishing valid payment-to-self of this amount. The clients can be given a signed challenge string to confirm this. It&#8217;s interesting that Ed, the lecturer mentions that bitcoin exchanges may under claim. Say they have at least some amount instead of giving the full amount. Perhaps the exchange may have a reserve that they do not want to share.</p>
<p><strong>Proof of Liabilities</strong></p>
<p>A liability is what the you are responsible for. In the context of exchanges, this means how many demand deposits are help. The lecturer prevents a scheme involving Merkly Trees to solve this. The Merkle Tree contains a leaf corresponding to each user and essentially each depositer can ensure they are in the tree and what the total deposits are. This can be done is O(logn) time as with every other binary tree presented in this courser.</p>
<p>Each proof reveals quite a bit of private information since it reveals the addresses used by exchanges. This is why proof of reserve according to the lecture is rare.</p>
<p><a href="http://www.jbonneau.com/doc/DBBCB15-CCS-provisions.pdf" target="_blank"><strong>Proof of Solvency</strong></a></p>
<p>This allows exchanges to reveal that they can manage and settle each customer&#8217;s account without revealing total liabilities, reserves, or addresses. It is called <strong>Provisions</strong> and I&#8217;ve listed a link to the <a href="http://www.jbonneau.com/doc/DBBCB15-CCS-provisions.pdf" target="_blank">paper</a>.</p>
<p>Which of these risks of Bitcoin exchanges that are NOT risks of maintaining one&#8217;s own hot and cold wallet?<br />
Ponzi schemes:<br />
Bank Runs</p>