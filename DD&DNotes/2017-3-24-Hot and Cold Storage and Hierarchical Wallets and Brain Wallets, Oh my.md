---
layout: post
title: Hot and Cold Storage and Hierarchical Wallets and Brain Wallets, Oh my
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2>Lions, and Tigers and Bears, oh my! Hot and Cold Storage, Hierarchical Wallets, and Brain Wallets, Oh my!</h2>
<p><a href="http://www.deltadeltaandmoredeltas.com/local-storage-bitcoin/">Last time</a>, I just discussed local storage. I listed several options for storing bitcoins and I talked about storing bitcoin from a security, availability, and convenience standpoint. This lecture is again looking at different key management system but from the idea of access to the internet/blockchain. I talk about hierarchical wallets, brain wallets, and paper wallets. I would say &#8220;All the wallets&#8221; but there are more wallets to come&#8230;</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is cold and hot storage? How does that influence what wallet I choose?</li>
<li style="text-align: left;">This cold storage seems cool. Can I make it myself?</li>
<li style="text-align: left;">Why would you and how can you transfer coins from hot to cold and vice versa?</li>
<li style="text-align: left;">What is this hierarchical wallet? Is it similar to a hierarchical deterministic wallet?</li>
<li style="text-align: left;">What is a deterministic wallet? Has it been implemented and where?</li>
<li style="text-align: left;">What are the mechanisms used to do cold storage?</li>
<li style="text-align: left;">What is a brain wallet?</li>
<li style="text-align: left;">What is a tamper-proof seal device and give an example.</li>
</ul>
<h2><strong>Hot and Cold Storage</strong></h2>
<p>If you have worked in technology the words hot and cold storage may have popped up before. <strong>Hot storage</strong> simple means it&#8217;s connected to the internet and thus has the opportunity to be considered risky. Thus when you put your key management on a internet connected computer, phone, or a browser, this would be hot storage. Hot storage is not bad; it is even necessary if you want to conveniently make transactions. <strong>Cold storage</strong> is when the key management that is offline and can be considered more archival. That paper wallet is a form of cold storage. Also, if you manage your keys on a non internet device, this is also cold storage.</p>
<p>I saw quite a few tutorials online showing how to create a cold storage device. I&#8217;ve listed them below since I thought it was interesting.</p>
<ol>
<li><a href="https://www.reddit.com/r/Bitcoin/comments/5tmxx6/using_old_phone_for_cold_storage/"> Using Old Cellphone as Cold Storage</a>: These instruction show how you can use an old cellphone as a cold storage device. It is a bit difficult to follow but there is a <a href="https://www.youtube.com/watch?v=I46JkxsmNO4">video here</a>.</li>
<li><a href="https://www.youtube.com/watch?v=fzLLZYhbA50">Creating a Bitcoin Cold Storage Wallet</a>: This creates a cheap cold storage wallet using Mycelium. The phone was an android phone.</li>
<li><a href="https://www.youtube.com/watch?v=2qmOM567BF4">Creating a USB Bitcoin Wallet with MultiBit</a>: This tutorial shows you how to make an encrypted USB Bitcoin Wallet.</li>
<li><a href="https://bitcoinmagazine.com/articles/a-review-of-ravenbit-the-diy-physical-bitcoin-1408521825/">RavenBit: DIY Physical Bitcoin</a>: This company actually sends you a brass coin.</li>
<li><a href="https://www.bitcoin.com/guides/setting-up-your-own-cold-storage-bitcoin-wallet">Cold Storage Paper</a>: This tutorial came from Bitcoin.com where they describe creating a secure paper wallet.</li>
</ol>
<h3><strong>Remember</strong><br />
Hot- online convenient but risky<br />
Cold &#8211; offline archival but safer</h3>
<p>&nbsp;</p>
<p>Now that we know what hot and cold storage means, why did the people from Princeton devote an entire lecture to them and transferring bitcoin between each system? It is because it is something that will be necessary for owners and is non trivial. Suppose you get quite a bit of bitcoin via gambling in your hot storage and you need to offload that amount to your cold storage. You&#8217;ll need to transfer the coin from the hot key address to the cold key address. This can all be done with the cold storage offline, so this is an easy move. However, let us say you have been having a terrible gambling run and you have depleted your hot storage wallet. You can A. Quit and decide you&#8217;re done or B. Get more bitcoin into your account by transferring some of your secured funds from the cold storage to the hot.</p>
<p>&nbsp;</p>
<p>How can you transfer from cold to hot if you&#8217;d prefer to keep your cold storage device offline for security? Likely, you&#8217;ll want to receive coins in a separate address with different secret keys each time, thereby requiring some mechanism to actively generate new fresh cold addresses each time. Having new addresses improves anonymity since someone cannot be identified for having several transactions between a single address. Also, if one private key is compromised, it&#8217;s good to have other options.</p>
<p>A very simple approach reminds me of a feature in Gmail. With Gmail, you can set up 2-Factor Authentication. (If you don&#8217;t have 2-Factor Auth set up, do it now!) 2-Factor Authentication means that when you log in, you submit your password but then you have to submit a second code. This enables better security since that second code is usually sent to a device that thwarts hackers from just brute forcing your password. This means every time you log into your Gmail, you type your password and then Google sends a code to you via email or text message. There are times when you&#8217;re not online or you&#8217;re traveling where that secondary device is just unavailable. At moments like that, Google allows you to print a list of codes and just use those codes to log in. These codes can be printed out before your trip and you&#8217;ll take this sheet of paper with you so that when you want to check your Gmail, you&#8217;ll use these codes as a replacement for that second code.</p>
<p>Thus cold storage can just generate a bunch of addresses and send them to the hot storage. The only problem is that periodically, the cold storage device will have to go online to generate and deliver a new set of codes to the hot storage.</p>
<p>This is where <strong>hierarchical wallets</strong> come into play.</p>
<h2><strong>Hierarchical Wallet</strong></h2>
<p>A hierarchical wallet allows the cold storage side to have an unbounded number of addresses and the hot side knows these addresses vi a short, one time communication between the both sides. This sounds perfect!</p>
<p>I&#8217;ll explain how it works as well as I understand it. We will still be using the ECDSA scheme since it has special properties which I&#8221;ll touch upon later. For hierarchical wallet, key generation is slightly modified. Regular key generate (generateKey) creates a public key (address) and a secret key. Instead, the generate key creates a public and private key generation info. With the generation info and an index number, you can generate the ith address in the sequence.</p>
<p>With this &#8220;generation info&#8221;, you can create a sequence of addresses instead of just one. The cool part is that the address generation info does not leak information regarding private keys so giving people the index and generation info is reasonably safe. The reason this works is because ECDSA supports hierarchical key generation. Now as long as the hot and cold side know the right sequence number, you can generate addresses from the hot side and private keys on the cold side. Also, the public key are not linkable meaning that even if you figure out one, you can just reverse engineer in some way to get the rest of them an that the private keys are still safe.</p>
<p>Now you must be thinking, where is this hierarchical, I just see two different sides hot and cold? There can actually be more levels with this wallet. Currently the hot side is the lower level while the cold is the top level. As with a company employee chain, the higher the chain the more secure you want the communication chain.</p>
<h3><strong>(HIerarchical) Deterministic Wallets</strong></h3>
<p>While this word was not mentioned in the lecture, I think it is worth mentioning <a href="https://bitcoinmagazine.com/articles/deterministic-wallets-advantages-flaw-1385450276/" target="_blank"><strong>deterministic wallets</strong>. </a>A deterministic wallet allows the user to generate data for their keys from a single seed instead of randomly generating them The nice benefit of the deterministic wallet is that you can recreate your lost keys if say your hard drive gets corrupted as long as you know this seed. Honestly, to me this sounded just like hierarchical wallet ie a special generateKey function. Within the <a href="https://bitcoinmagazine.com/articles/deterministic-wallets-advantages-flaw-1385450276/">article</a> that I linked to, when the author, Buterin explain the wallet, it sounds exactly the same as the hierarchical just with different words. If you read the article, just substitute the word generation info with master public key.</p>
<p>I&#8217;ve also listed several links that either talk about hierarchical deterministic (HD) wallets or are implementation of HD wallets. Just know, many wallets nowadays do implement this feature. Hierarchical Deterministic Wallet (HD) term was more prevalent than just the hierarchical wallet. I feel like the lecturers may have chosen a less used term to explain this feature.</p>
<ul>
<li><a href="https://www.youtube.com/watch?v=YPvsTe5bjGs">Understanding Hierarchical Deterministic Wallets </a> &#8211; This youtube video by LTB Network features a podcast type explanation of the different wallets. It is about an 11 minute video. He explains the BIP: 32 in a nice clear fashion.</li>
<li><a href="https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki">Hierarchical Deterministic Wallets BIP: 32 </a> &#8211; This links contains the exact Bitcoin Improvement Protocol (BIP) for adding HD wallets. It is a technical read but incredibly informative.</li>
<li><a href="https://electrum.org">Electrum Protocol &#8211;</a> This company which I listed last week as a bitcoin wallet. As mentioned from <a href="https://bitcoinmagazine.com/articles/litecoin-electrum-beta-testing-1397330254/">Bitcoin Magazine</a>, the wallet full implement BIP32 making it a Hierarchical Deterministic Wallet</li>
<li><a href="https://wallet.trezor.io/#/">TREZOR &#8211;</a> This is another bitcoin wallet that implements HD wallet. Different from other wallets discussed, this is a <strong>hardware wallet</strong>. Thus when you buy TREZOR, they will send you palm sized, tamper and water- proof device which is your wallet.</li>
<li><a href="http://www.bitcoinarmory.com/">Armory Deterministic Wallet &#8211;</a> I mentioned this company last time as being a security conscious bitcoin wallet. They have a neat implementation for a deterministic wallet.</li>
</ul>
<p>Now, I know I listed some practical ways to do cold storage. I listed those DIY resources on how to make your phone, paper, or USB device into a cold storage. These methods incorporate methods such as brain wallets, paper wallet, and tamper-resistance devices. A paper wallet sometimes contains a tamper-evident seal over the private key. This makes sure there is not way to output or divulge the key. A <strong>brain wallet</strong> secures the bitcoins by a secret passphrase which I&#8217;ll discuss below.</p>
<h2>Brain Wallets</h2>
<p>A brain wallet is nice because you don&#8217;t need to have extra hardware to store your bitcoins. You only need to have a good memory or an effective but secure way to determine your passphrase. Once you have a good passphrase, then you can just hash it twice, maybe using SHA-256 to give you a secure public and private key. Now your password while it may look random, if the adversary knows how you generated the key and your passphrase, you will be at a loss. With your email, if someone puts into too many password, you can locked out, this does not happened with bitcoin. Thus if your passphrase is common, hackers can just use something called offline guess or password cracking to steal your coins. The lecture does discuss one way to do passphrase generation.</p>
<p>You just choose a random sequence of 6 random words from among the top 10,000 works in the English language. They are easy to remember and have roughly 80 characters. From there, use a hash function SHA-256 and compute is 2^20 times to just make it hard for the attacker.</p>
<p><strong>Key Stretching</strong> &#8211; use a deliberately slow function to derive the private key from the passphrase to make it harder for attackers to brute force.</p>
<p><a href="https://metamask.io/">Metamask.io</a> is a Chrome plugin. Besides having a cute evil fox, they use this brain wallet approach. When you create your new vault, as they call it, they give you 12 words that allows you to restore your MetaMask accounts for the vault. So you&#8217;ll be given words like &#8220;retreat brain math envelope earth dutch fake tired dot occasions worn focusing&#8221; which you need to store and use to recover your accounts.</p>
<p>There is one downside, if you forget the passphrase, you&#8217;re screwed&#8230;</p>
<h2>4 Ways to do Cold Storage</h2>
<ol>
<li>Information stored in device, device locked</li>
<li>Brain wallet encrypt info under passphrase or password that a user remembers</li>
<li>Paper wallet -print info on paper, lock up the paper</li>
<li>&#8220;Tamper-proof device&#8221; device will sign things for you but won&#8217;t divulge keys</li>
</ol>
<h1>Wrap-Up</h1>
<p>I&#8217;ve wrapped up below what I&#8217;ve talked about because it combined several components. I first discussed why there is a need for hot and cold storage as well as why you would want to transfer coins between these storage components. Additionally, I gave some links to tutorials on how to create a cold storage device. Next, I walked through how hierarchical wallets work. Next, I discussed deterministic wallets since this term is more actively used than hierarchical  wallet. Lastly, I discussed, what methods are used to do cold storage which involve offline devices, brain wallets, tamper-proof devices, and paper wallets.</p>
<p>Which of the following statements are true about cold wallet storage<br />
Cold storage keys in device without network access<br />
hot storage wallets can generate arbitrarily many cold storage addresses without contacting the cold storage</p>