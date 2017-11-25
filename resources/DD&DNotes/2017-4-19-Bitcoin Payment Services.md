---
layout: post
title: Bitcoin Payment Services
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<p>This lecture focused on the merchant point of view for how they would interact with bitcoin. Many major businesses with brick and mortar stores, currently accept bitcoin such as Home Depot, Kmart, and Dell. Additionally, there are quite a few online companies such as Expedia, Steam, and Shopify that accept bitcoin as well. The first store I ever saw accepting bitcoin was <a href="http://www.coupacafe.com" target="_blank">Coupa Cafe</a> in Palo Alto, CA like 2013. At the time, I thought it was silly to waste a small amount of bitcoin for coffee if the price was going to rise exponentially. Hindsight, I guess. But then, I&#8217;ll point you to this <a href="http://www.coindesk.com/bitcoin-pizza-day-celebrating-pizza-bought-10000-btc/" target="_blank">pizza story</a> which I think is relevant and speaks about the behavior of the organizers of bitcoin. Short story, 2 Papa John&#8217;s pizzas purchased for 10,000 BTC in 2010.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a bitcoin payment service?</li>
<li style="text-align: left;">What risks are merchants exposed to accept bitcoin?</li>
<li style="text-align: left;">Briefly explain a simple transactions for a merchant who has a payment service.</li>
<li style="text-align: left;">How does the payment service benefit?</li>
</ul>
<p>Let&#8217;s start with a simple scenario as to why and how a merchant would go about accepting bitcoin. The Why? is simple, you want to increase your revenue and if you see consumers are willing to pay by bitcoin, then why would you reject money. That being said, it&#8217;s not that simple. I know several people who have never heard of bitcoin or even if they were to receive bitcoin would immediately want to convert it into cash. Also, if they are not technologically savvy, they may fear all the risks involved with this. Merchants want a simple way to implement this feature as well as not face maintenance issues.</p>
<p>The lecture covered certains risks that merchants may face: technology risk, security risk, and exchange rate risk. With any change in technology, the merchant may fear unknowns, if that sytem goes down, they will lose money. There are security risks that are faced by both the merchants and consumers in that their online wallets may be at risk from criminals. Furthermore, the volatility of bitcoin can be a concern. There have been times when bitcoin has jumped up <a>70% in one month</a> as well as fallen from $1200 to $1000 in a few days. How can a person selling a cup of coffee ensure they receive about $2.50. This is where <strong>payments services</strong> come into the picture.</p>
<h3>Payment Services</h3>
<p>Now that I have made merchants look like incompetant technophobes who need to be handled carefully (I don&#8217;t think this is always the case&#8230;), I&#8217;ll describe the role of the bitcoin payment service as well as give some examples of bitcoin payment services. A payment service acts as an intermediary between customer and merchant. Companies like Venmo, PayPal, and Square allow vendors to easily integrate with their system and allow their clients to pay how they like. Bitcoin payment services have similar features.</p>
<p>First, a merchant will go to the payment service website and fill out information on what they want to sell, price, and maybe some display parameters. They may also have to get a bitcoin address to receive funds. This likely will have either a simple UI or allow a merchant to connect to it programmatically. Then the service will give an online vendor some code to copy and paste into their website which will allow the vendor to receive payments in bitcoin. The vendor deploys the code and that should be it on their part.</p>
<h4>Look what happens on a transaction</h4>
<ol>
<li>Clients picks out an item and chooses &#8220;Pay with Bitcoin&#8221;</li>
<li>A HTTP request is sent to the payment service with info regarding the transaction</li>
<li>Information is sent back to the client to tell them how to pay via Bitcoin</li>
<li>Customer needs to initiate a bitcoin transfer to the pament service through their own wallet</li>
<li>Once the user creates payment, payment service will update the merchant on the status</li>
<li>Once the number of confirmations has occurred on the chain, the payment service sends the confirmation to the merchant</li>
<li>The payment service will send the merchant the money and the merchant will ship the goods to the user</li>
<li>The payment service pays the merchant in dollars/fiat currency hile taking a small percentage to do the transaction</li>
</ol>
<p>From my perspective, there needs to be quite a bit of trust to the payment service and the payment service is absorbing all the risk. If there are wide fluctuations in bitcoin, then the payment service either loses/gains from the price change.</p>
<h4>Who are some Bitcoin Payment Service Providers?</h4>
<ul>
<li><strong><a href="https://gear.mycelium.com/" target="_blank">Mycelium Gear</a>(</strong>https://gear.mycelium.com/) &#8211; Interestingly, they seem to deviate from their business model than the lecture. notes. According to their site, they take 0% commission and the transaction is peer to peer meaning that it does not pass through the Mycelium Gear wallet at all.</li>
<li><a href="https://developers.coinbase.com/docs/merchants/payment-buttons" target="_blank"><strong>Coinbase</strong></a> (https://developers.coinbase.com/docs/merchants/payment-buttons) &#8211; Coinbase says if you keep your money in bitcoin then the transaction is free. Otherwise, they charge 1% or $0.15 (whichever is greater) to convert the bitcoin you receive into the local currency. The lecture did mention then specifically.</li>
<li><a href="https://bitpos.me/" target="_blank">BitPOS</a> (https://bitpos.me/) &#8211; This one is based in Australia and allow merchants who do both e-commerce and brick and mortar stores to sign up.</li>
<li><a href="https://en.bitcoin.it/wiki/How_to_accept_Bitcoin,_for_small_businesses#Merchant_Services" target="_blank">many many more&#8230;.</a></li>
</ul>