---
layout: post
title: Currency Exchange Markets: Cryptocurrency Edition
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Currency Exchange Markets<br />
</strong></h1>
<p>Yes, I&#8217;m finally at the last lecture of week 4. Seriously, it&#8217;s so long. Also, I realize the first time I watched the lecture, I did not fully understand much of what was talked about during the lecture. I have remedied that by writing out this article.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">How is currency exchange markets different from bitcoin exchange?</li>
<li style="text-align: left;">How can I exchange my fiat for bitcoin?</li>
<li style="text-align: left;">Where can I find a Bitcoin ATM?</li>
<li style="text-align: left;">What simple ways did they classify owners of bitcoin?</li>
<li style="text-align: left;">Using the fiat mediated transaction model, what happens when supply is too low?</li>
</ul>
<h3>Currency Exchange Market, isn&#8217;t that just Forex?</h3>
<p>Currency exchange markets in this lecture refer to trading bitcoin against fiat currency. If you know anything about foreign exchange markets than you&#8217;re in luck since they operate similarly. The exchange rate refers to how much someone is willing to buy one currency and sell another currency.<br />
The site points to <a href="https://bitcoincharts.com/markets/">Bitcoincharts</a> as an example of a place to view markets. This website gives you pricing of not just USD but for a wide variety of different fiat currency. If you&#8217;re just interested in just USD prices then use <a href="https://bitcoincharts.com/markets/currency/USD.html">this link</a>.<br />
From viewing this site because of the constant updates, you can see this is a liquid market.</p>
<p>There is another option which is buying bitcoin in person with cash. There are sites like <a href="&quot;https://localbitcoins.com/">localbitcoins.com</a> where you can choose to find people near you to make these trades. I observed that even though bitcoincharts showed the price of bitcoin to be about $1300 (according to Coinbase it&#8217;s $1312.99, the prices that people were posting were at least $1400. Some were even $1500 and more. This does show the distinction between using a more liquid versus this one to one exchange. If you still want to go this path, there are apparently regular meetups that people go to to trade bitcoin. I&#8217;m not sure if that would be more liquid but I think that you would have more competition and thus perhaps the price to buy bitcoin may be more standard and closer to the market price listed online. There are also <a href="http://www.bitcoinvendingnetwork.com/">bitcoin vending machines</a> around the world where these machine may allow you to sell bitcoin. New Hampshire, USA has at least 5 bitcoin vending machines. Personally I think these machines are a bit shady in that I would be hesitant to use them given the transaction fees. This <a href="http://www.coindesk.com/6-cool-machines-accept-bitcoin/"> Coindesk</a> article while a bit old does touch upon certain types of new machines that accept bitcoin. Now, the lecturer decided to start talking about market dynamics&#8230; (I know this is a terrible segue but I&#8217;m watching the video).</p>
<h3>Basic Market Dynamics</h3>
<ul>
<li>market matches buyer and seller</li>
<li>large, liquid market reaches a market price</li>
<li>price set by supply (of BTC) and demand (for BTC)</li>
</ul>
<p>Now how does that translate to the bitcoin land. When the video was filmed there was 13.1 million BTC. As of April 29, 2017, there are 16,300,750 BTC. Supply of a currency is equal to the amount of coins in circulation plus the amount in demand deposits. If you have bitcoins in demand deposit for dollars then that does have to be included. the amount of bitcoin may rise beyond 21 million BTC dependin on what supply you&#8217;re looking at. The demand of bitcoin is defined as one to mediate fiat-currency transaction and as an investment.</p>
<p>What does mediate fiat-currency transactions mean?<br />
My interpretation is that you&#8217;re using Bitcoin as a tool to exchange other currencies and thus you have no plans to hold Bitcoin long term. The reason for doing this is that transferring money can be difficult. Using Western Union or MoneyGram can be expensive as well as you get large transaction fees as well as less ideal exchange rates. This is for transferring money internationally. Even domestically can be difficult if the two parties are not using the same bank and you need to transfer a large amount of money. If your&#8217;re actually interested in moving money without bitcoin, check out this article from <a href="https://www.nerdwallet.com/blog/banking/best-ways-to-wire-money-internationally/">Nerdwallet</a>.<br />
<a href="https://www.ofx.com/">OFX</a>, <a href="https://transferwise.com">Transferwise</a>, and <a href="https://www.xoom.com/money-transfer">XOOM</a> are all newer companies that are helping reduce costs but I think by comparison using bitcoin may be cheaper. You won&#8217;t win with speed though or with convenience at this point.</p>
<p>Below I&#8217;ve written down a concrete scenario to hopefully remove any abstraction.</p>
<p>This means that Alice buys BTC for some dollars. Then Alice sends BTC to Bob Then Bob sells the BTC for $. Thus the main take away is that the BTC is out of circulation for this time. The reason for doni this is that you&#8217;ll get If you use it for investment purposes, the idea is that the market thinks demand will go up in the future.</p>
<p>Now that we understand what is being done, the next question is what effect does transaction mediate have on the price of bitcoin?</p>
<p>He walks through a simple model for modeling transaction-demand. While listening I kept nodding and was like great this makes sense. After I walked away then tried to explain the concept to myself again and was completely at a loss. If this happened to you, I hope my below explanation can help.</p>
<p>There are three variables that this model relies upon.</p>
<p><strong>T (Total Transaction Value)</strong></p>
<p>This is your demand in a rate format. It is how much money that needs to be moved during a certain period of time. In this case all money (fiat) is boiled down to a base value in dollars. The period of time used by this model is in seconds. My understanding of how to calculate this would be to sum up all the potential transactions that need to be taken a day and then divide that by (24 * 3600 =  84,600). While I now understand this variable, my question would be is this an easy number to calculate? Can you get this from reading the blockchain?</p>
<p><strong>D (Duration)</strong></p>
<p>This is how long those bitcoins will be out of circulation in order to mediate a transaction. I thought about those payment services individuals as a way of understanding this number. Let&#8217;s say a merchant hired a firm to handle the bitcoin processing. Thus the duration would be how long it takes the merchant to accept the bitcoin from the client and then return the dollar amount to the merchant. Again this gets measured in seconds.</p>
<p><strong>S (Supply)</strong></p>
<p>Since this is a demand-supply model, it makes sense that supply is the last value. This refers to the supply of bitcoin that are liquid in the market. That means you take the full supply of bitcoin around 16 million and subtract the amount of bitcoin that are used for long term investment. This supply is a number in terms of bitcoin. To get to any sort of dollar amount to work with T, you would need to multiply the S by the price of bitcoin.</p>
<p><strong>P (Price of Bitcoin)</strong></p>
<p>Very simple this is the price of bitcoin. However, think of P as Dollars/1 Bitcoin. This will make it easier for the below part.</p>
<p>S/D &#8211; Number of bitcoins available per second. You&#8217;re dividing the total supply by the time needed for a transaction. If the</p>
<p>T/P &#8211; Bitcoins needed per second. Right now, you&#8217;re converting the total transaction value which is in dollars into the number of bitcoins.</p>
<p>From these two simple values of Number of Bitcoins available and Number if Bitcoins needed, the lecturer goes through different cases. If you think back to Econ 101, there were always Demand and Supply curves. <img alt="demand_supply" class="aligncenter size-full wp-image-165" src="https://i0.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/05/demand_supply.png?resize=400%2C301" /></p>
<p>Thus at a specific moment in time there is a supply of S/D and demand of T/P and with this model, prices will fluctuate in order to bring supply and demand in line with each other. Now let&#8217;s look at the consequences of inequalities between supply and demand. In econ, if supply is higher than demand, then that means the suppliers will be willing to lower their price. That translates to higher supply in available bitcoin means that people who are selling bitcoin will be able to lower their asking price in order to sell them. If you just care about equations and direction of movement, for T/P, when price drops (note that means the the denominator is getting smaller) the demand increases. Similar in econ when the supply is smaller than demand, this means that the demand people are willing to pay a larger price for the fixed supply. Again, for this model, it means people who want to mediate transactions cannot because of a fixed supply and thus the price increases. If you&#8217;re an equations kinda of person, the below ones sum this all up quite nicely. <img alt="equilibrium" class="aligncenter size-full wp-image-166" src="https://i1.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/05/eq_supply.png?resize=403%2C225" /><br />
What I thought was interesting, is this gives us a simple way to value the price of bitcoin. Using this equation, perhaps we can estimate if the price of bitcoin is higher or lower or matched up.</p>
<h3>World of Cryptocurrencies</h3>
<p>However, this lecture does not touch upon how many cryptocurrencies are out there that people trade. I almost think of bitcoin as the stable currency that people use to market the rest of their buys and sells against. There are different cryptocurrency exchanges that do not let you deal in fiat currency but instead you only use your cryptocurrency wallets.</p>