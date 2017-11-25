---
layout: post
title: Applications of Bitcoin Scripts: Micropayments
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Applications: Micropayments </strong></h1>
<p>This is a continuation of the Bitcoin Transaction Basics lecture. As mentioned before, I watched the entire third week in one sitting so some of my notes may reference previous posts. This part focuses on applications of Bitcoin scripts. There was quite a bit of material so I have broken down this part into 3 parts. This is the third part focusing on Micropayments. Here&#8217;s a link to the <a href="http://www.deltadeltaandmoredeltas.com/escrow-transactions-using-multisig" target="_blank">first part</a> and <a href="http://www.deltadeltaandmoredeltas.com/green-addresses/" target="_blank">second part</a>. Honestly, I thought this use case help the most promise or concreteness initially. Then I realized I watched the lecture and came out with more questions and skepticism about why use bitcoin for this. Face palm&#8230;.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a micropayment?</li>
<li style="text-align: left;">What do micropayments look like without Bitcoin?</li>
<li style="text-align: left;">What are some companies who are doing this</li>
<li style="text-align: left;">What does it look like with bitcoin?</li>
</ul>
<h3>What is a micropayment?</h3>
<p>It&#8217;s what you would think micropayment means, a transaction with a low amount. Specifically though it usually relates to an online transaction involving less than some currency standard like a dollar or a penny. Sometimes though it can be greater than that. As of March 2017, <a href="https://www.paypal.com/us/selfhelp/article/what-are-micropayments-faq664/1" target="_blank">Paypal</a> considers any payments less than $4.00 USD a micropayment. They also charge 5% + $.05 to merchants who process these transactions. Apparently Amazon also has a similar system but I was not able to find the exact documentation. Even so, how do you pay someone less than a penny when that&#8217;s not a physical quantity?</p>
<p>There are many technologies just handling micropayments. In most cases, there is some transaction fee associated with each payment which makes sense. These companies are providing a service to handle micropayments. Some may have a third-party micropayment provider who collects these small payments. Then the payment is made from a digital wallet when they have reached a potential threshold. A digital wallet is A site may choose not to make payments until the total amount is greater than 5 dollars. Some platforms have created &#8220;prepaid systems&#8221; where users add money to create a initial balance. Then the user can purchase these small purchases which may be less than a dollar but can be easily handled since the platform can just subtract from the platform.</p>
<p>Look at this list of companies who are making their business online payments incorporating micropayments.</p>
<ul>
<li><a href="http://buysimple.appappeal.com/" target="_blank">BuySimple</a></li>
<li><a href="https://www.dwolla.com/ach/micropayments/" target="_blank">Dwolla</a></li>
<li><a href="http://http://www.boku.com/" target="_blank">Boku</a></li>
<li><a href="http://http://bango.com/" target="_blank">Bango</a></li>
<li><a href="https://www.paymentwall.com/" target="_blank">Paymentwall</a></li>
<li><a href="https://fortumo.com/" target="_blank">Fortumo</a></li>
<li><a href="https://millipay.ch" target="_blank">milliPay </a></li>
<li><a href="http://www.paycron.com/" target="_blank">payCrony </a></li>
<li><a href="https://www.thelevelup.com/" target="_blank">LevelUp </a></li>
<li><a href="https://www.braintreepayments.com/?partner_source=US_DT_SEA_BNG_TXT_RES_DEV_CPC_GW_YBR&amp;utm_source=bing&amp;utm_medium=cpc&amp;utm_campaign=%5BUS-BING%5D%20Braintree%20Branded&amp;utm_term=braintree&amp;utm_content=Branded%20(e)&amp;gclid=CLCzg-TlydICFYyjNwodoloPlw&amp;gclsrc=ds&amp;dclid=CJSdhuTlydICFcW_swodvqsGDA" target="_blank">brainTree </a></li>
</ul>
<h3>Where does bitcoin scripts fit into this?</h3>
<p>Bitcoin scripts give users a way to do efficient micropayments. Suppose there is an online music streaming system where Jim has to pay for every minute he listens to Bitotify until he hits some max threshold and then just gets that bill. Maybe, this is likely silly but Spotify should try this. Billing Jim every minute is expensive since if Jim listened for 129 minutes, there would be 129 transactions and the transaction fees would add up. So, why not just combine the payments at the end so that there is only one transaction.</p>
<p>This is what gets done. A MULTISIG transaction gets created which has the maximum amount that Jim could be billed and it requires that both Jim and Bitotify sign the transaction to release the coins. In addition there is a transaction which will refund all of Jim&#8217;s money but is locked until a certain time. Just remember that bit for now and I&#8217;ll go back to it in a little bit. After each minute, Jim signs a transaction indicating how many coins he owes. Thus by the time minute 20 occurs, Jim will have signed 20 different transactions which were only signed by Jim and thus are not on the blockchain. Jim tells Bitotify when he&#8217;s done and Bitotify signs the most recent transaction that was signed and publish that to the blockchain.</p>
<p>This generates the potential double-spends, then Bitotify should only sign the last double spend. Also, if Bitotify never signs the last transasction there is a feature call Lock Time.</p>
<p><strong>Lock Time</strong> A time embedded into a transaction that will not publish a certain transaction until a specified lock time. The transaction will be invalidated if a specific block time or a specific point in time are put into blocks. Thus, this transaction of refund only gets kicked off if they haven&#8217;t been spent before.</p>
<p>So if you&#8217;re now thinking, <strong>SO WHAT!</strong>, I&#8217;ve got what the benefits are. This means that double spends are protected. Transaction fees are reduced since there is only one transaction being put onto the blockchain. There is no third party, it&#8217;s just between the two people.</p>
<p>So, escrow payments, green addresses, and micropayments are all examples of smart contracts. <strong>Smart Contract</strong> refer to contracts that are upheld be technical implementation of Bitcoin as opposed to laws and courts. In many of the examples, the true win for the blockchain was removing that single entity of validation. I know it doesn&#8217;t seem like that specifically when you think of the judge from the escrow payments and Mt. Gox from the green addresses.</p>
<p>A few companies that I&#8217;m interested in are <a href="https://brave.com/">Brave Browser</a>, <a href="https://satoshipay.io/terms/">SatoshiPay</a>, and <a href="https://faucethub.io/">FaucetHubIO</a>. I think the biggest improvement with the Bitcoin micropayments is enabling anonymity payments. So if I like a website, I can donate funds from my browser with micropayments instead of having to face the previous minimum donate amount.</p>