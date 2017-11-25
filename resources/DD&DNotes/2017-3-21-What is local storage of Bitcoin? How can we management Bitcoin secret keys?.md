---
layout: post
title: What is local storage of Bitcoin? How can we management Bitcoin secret keys?
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>What is local storage of Bitcoin? How can we manage Bitcoin secret keys? 20+ options listed<br />
</strong></h1>
<p>The entire week four is devoted to storing and using bitcoins. Yes, this will be a practical week of lectures! The first lecture felt very simple. Basically, the conversation of storage of bitcoin is focused on the management of secret keys. There are a variety of ways to do local storage on your phone which I&#8217;ll list at least 10 different wallets for your phone and desktop. I&#8217;ll talk about bitcoin vanity addresses as well.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What does local storage of bitcoin mean?</li>
<li style="text-align: left;">When considering local storage, what should you focus on?</li>
<li style="text-align: left;">What is a bitcoin wallet?</li>
<li style="text-align: left;">I want a wallet! What are some of my options?</li>
<li style="text-align: left;">How are addresses encoded to be sent to another party?</li>
<li style="text-align: left;">What is a vanity address?</li>
</ul>
<h2>What does local storage of bitcoin mean?</h2>
<p>When I think simple storage of money, I think of that crazy uncle who hid/stored all his money under his mattress. It was safe as long as the house was intact and no one knew where to look. One issue I have with that approach is that $100 sitting in a mattress from 1950 is still only $100 in 2017 though $100 does not go as far as before. Clearly those $100 were better invested in a bank at the very least or a stock market index&#8230;.</p>
<p>The approach of simple local storage of bitcoin is something like that. The bitcoin is stored on some local device. That local device can either be your home computer, phone, or a USB stick with some wallet software to help you manage that data.</p>
<h4>How do you spend a bitcoin?</h4>
<p>To spend bitcoin, think about what information needs to be shared so that a transaction can take place. There needs to be some connection to the blockchain, the identity of the coin to spend, and the worth of the coin. Also, you have a secret key which you use to sign transactions and verifies the owner. At the core, storing bitcoin boils down to storing and managing Bitcoin secret keys. The lecture broke down the key management into three approaches: availability, security, and convenience</p>
<p><strong>Three Approaches</strong></p>
<ul>
<li><strong>Availability</strong>: How quickly can you spend your coins?</li>
<li><strong>Security</strong>: How safe are my coins to ensure no one else spends my coins?</li>
<li><strong>Convenience</strong>: How easy is it to management my coins?</li>
</ul>
<p>.Evaluation of different methods</p>
<h5>Paper Wallet</h5>
<p>Back to my example of storing the bitcoin on your local device, it&#8217;s pretty simple. You can actually have a <strong>paper bitcoin wallet</strong>. I think several years ago at some of the early bitcoin conference, people were presented with paper wallets for attending certain talks. This is just like putting money in the mattress. Your bitcoin wallet will contain your public key and the private key. Usually there is also a QR code so that the wallet can be quickly scanned. I created a wallet just for academic purposes at <a href="https://www.bitaddress.org">BitAddress</a>. While paper wallets are simple, they are just as secure and available as your regular wallet. Though, you&#8217;ll likely have to use your phone or type out the address to use it. During that point, there is a potential for a hack to occur. Honestly, if you&#8217;re going to do this, at the very least laminate the paper wallet.</p>
<h5>DIGITAL WALLET: PHONE and DESKTOP</h5>
<p>What about storing the keys on a digital device like your phone or computer. It&#8217;s convenient since you can think of it just like your wallet especially if you store your coins on your phone. Also, to make sure you&#8217;re not writing individual transaction in C++ or Go, you will likely use a bitcoin wallet software. A <strong>bitcoin wallet software</strong> is one that keeps tracks of coins, manages details of your keys, and usually has a slick user interface. In terms of availability, the coin is only available when you have your device. Thus, all questions regarding availability and security are tied to that device. Simple problems like your phone getting lost/wiped/stolen could turn into a catastrophe if you have a lot of bitcoin stored. Similarly, if someone hacks your computer and steals your private keys, then your bitcoins are lost. While, I feel like I&#8217;ve painted a grim picture, there are quite a bit of wallet softwares on the market.</p>
<p>I&#8217;ve listed and provided links to many desktop and mobile wallets. Some of the companies will be listed on multiple categories. If you&#8217;re going to use any of these wallets, please do your own research just to make sure they fit your needs.</p>
<h5>Local Storage: Bitcoin Wallets for Desktop</h5>
<ol>
<li><a href="https://bitcoin.org/en/">Bitcoin Core</a>: solid multipurpose software including a wallet</li>
<li><a href="https://multibit.org/">MultiBit</a>: available on multiple platforms</li>
<li><a href="http://www.bitcoinarmory.com/">Armory</a>: security focused wallet</li>
<li><a href="https://darkwallet.is/">DarkWallet</a>: private bitcoin wallet focused on privacy with a Browser and Ubuntu download</li>
<li><a href="http://bitcoinknots.org/">Bitcoin Knots</a></li>
<li><a href="https://electrum.org/#home">Electrum</a></li>
<li><a href="https://ciphrex.com/">mSIGNA</a></li>
<li><a href="https://bither.net/">Bither</a></li>
<li><a href="https://multibit.org/">MultiBit HD</a></li>
<li><a href="https://greenaddress.it/en/">Green Address </a></li>
<li><a href="https://www.arcbit.io/">ArcBit</a></li>
<li><a href="https://copay.io/">CoPay</a></li>
<li><a href="http://bitgo.info/">BitGo</a></li>
</ol>
<h5>Local Storage: Bitcoin Wallets for Phone</h5>
<ol>
<li><a href="https://breadwallet.com/">breadWallet </a> iOS Android</li>
<li><a href="https://bither.net/">Bither</a>: iOS</li>
<li><a href="https://coin.space/" target="target=&quot;_blank&quot;">Coin.Space</a>: available for Android Windows iOS</li>
<li><a href="https://play.google.com/store/apps/details?id=com.btcontract.wallet" target="_blank">Simple Bitcoin Wallet</a> Android</li>
<li><a href="https://www.arcbit.io/">ArcBit</a> iOS Android</li>
<li><a href="https://copay.io/">CoPay</a> all</li>
<li><a href="https://airbitz.co/" target="_blank">Airbitz</a> iOS Android</li>
<li><a href="https://wallet.mycelium.com/" target="_blank">Mycelium</a> Android</li>
<li><a href="https://greenaddress.it/en/">Green Address </a> iOS Android</li>
<li><a href="https://coinomi.com/" target="_blank">Coinomi</a> Android</li>
</ol>
<h2>Encoding Keys with base 58 or QR code</h2>
<p>Now that I&#8217;ve overwhelmed some people on the various wallet companies, I&#8217;ll discuss a bit on how keys are encoded to be sent to other parties. They can get sent via a text string or a QR code. To send a text string is relatively simple. You just take the bits of the key and convert it from binary (ones and zeros) to a base 58 number. Base58 means that in total there are 58 symbols in the alphabet. The English alphabet can be thought of as base 26. Binary is base two 2 because it only contains ones and zeroes. The base58 contains upper case letters, lower case letters and digits. If you&#8217;re thinking that is way more than 58 you&#8217;re right. Upper Case letters ie ABC&#8230; (26) + Lower Case letters ie abc&#8230; (26) + Digits 0123&#8230; (10) would be 62. Certain symbols were removed since they look too alike with other characters such as the capital letter &#8216;O&#8217; and the number zero &#8216;0&#8217;. Below is the address of the first Bitcoin block reward in the genesis block, base58 encoded.</p>
<p><code> 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa</code></p>
<p>I mentioned there was a second method with the QR code. Just take a picture with a smart phone and the wallet software will convert it into the correct bit sequence for the address and allows you to spend that money.</p>
<p>Speaking of addresses, there is something called a <strong>vanity address</strong>. Vanity addresses unrelated to bitcoin just refer to some name manipulation to an identifying object to make it aesthetically more pleasing. This <a href="http://www.nytimes.com/1988/05/22/realestate/how-builders-invent-vanity-addresses.html"> NYT article</a> from 1988 talks about real estate buildings that have nicer names such as changing 338 East 44th Street to Three United Nations place. Within the bitcoin landscape, it is a address that starts with some human-meaningful text. According to the &#8220;Princeton Bitcoin Book&#8221;, they are generated by people repeatedly generating private keys until the public key has this nice name on them. There are techniques for generating vanity address more efficiently by incrementing the private key instead of choosing a new random one each time. If you&#8217;re interested they&#8217;re some tools that provide this service. <a href="https://en.bitcoin.it/wiki/Vanitygen">Vanitygen</a> is a command-line too to do this. <a href="https://bitcoinvanitygen.com/">BitcoinVanityGen</a> is an online too that will allow you to choose the first 6 characters free. This <a href="https://vante.me/#!/order/start">Vante </a>company provides this as well. Be careful though using another source since they now have the potential to know your private key. If you&#8217;re going to do this, I&#8217;d recommend doing the generating yourself.</p>