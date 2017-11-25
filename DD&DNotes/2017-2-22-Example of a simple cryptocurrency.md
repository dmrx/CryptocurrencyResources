
<h4>1.5 A Simple Cryptocurrency</h4>
<p>These are my notes of the fifth lecture from Coursera��s Bitcoin and Cryptocurrency Technologies during Dec 2016 �C Feb 2017. This lecture covers simpler cryptocurrencies to allow one to think about the consequences of certain properties. Thus the takeaways for this post focus on these properties that are relevant to current currencies.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What happens when only one party create coins?</li>
<li style="text-align: left;">What is a double spend?</li>
<li>What does append only ledger mean and why does it help stop double spends</li>
<li>What is an issue with Scrooge coin?</li>
</ul>
<h5>GoofyCoin</h5>
<p>The first coin talked about was called GoofyCoin. Here are the main rules</p>
<ol>
<li>Only Goofy can create new coins. He owns the new coins created.</li>
<li>Whoever owns the coin can spend it</li>
<li>A coin is a string &#8220;CreateCoin [uniqueCoinID]&#8221; and Goofy&#8217;s signature</li>
<li>One can verify the coin by looking at Goofy&#8217;s valid signature as they walk up the chain of previous signatures of a coin.</li>
</ol>
<p>Goofy can create new coins. When he creates new coins, he generates a uniqueCoinID that is signed by pk_Goofy (public key Goofy). All new coins are owned by Goofy. Whoever owns the coin can spend it. Spending a coin means transferring the coin from one person to another which is done by cryptographic operations.</p>
<p>So if Goofy wants to transfer a coin to Donald, he has to go through a several steps. First steps wold create a new statement &#8220;Pay this to Donald&#8221; where this is a has pointer that references the coin in. The word &#8220;Donald&#8221; in the previous sentence refers to Donald&#8217;s public key. Goofy also signs the string since he owns the coin, he must sign that he is spending it. This statement now indicates that Donald now owns to the coin and he can spend it if he wants in a similar fashion. Each time an action is done to the coin, it gets chained together. The chain could be thought of as a linked list of hash pointers where hash pointer contains the hash of the previous coin. The initial creating pointer only contains a Create Coin uniqueCoinID statement and signature of Goofy.</p>
<p>Spending a coin means</p>
<p>Take the coins history</p>
<p>Donald payment<br />
signed by pk_Goofy<br />
pay to pk_Donald: H(head)</p>
<p>head<br />
signed by pk_Goofy<br />
CreateCoin [uniqueCoinID]</p>
<p>Now Donald owns the coin and she has to present the full blockchain if required.<br />
Now let&#8217;s say Donald pays the coin to Daffy then the chain now gets another entry.</p>
<p>Daffy payment<br />
signed by pk_Donald<br />
pay to pk_Daffy: H(Donald&#8217;s payment)</p>
<p>Donald&#8217;s payment<br />
signed by pk_Goofy<br />
pay to pk_Donald: H(head)</p>
<p>head<br />
signed by pk_Goofy<br />
CreateCoin [uniqueCoinID]</p>
<p>This is not a decentralized coin since only Goofy can create the coins. Also, the only people who know about the passing of coins are those present in the chain. Thus if Donald tries to give coins to Porky then there would almost be a two parallel paths that would not known about each other. Porky and Daffy could both look up the block chain they were given by Donald and verify that they had a valid coin created by Goofy. However, Donald was able to &#8220;double spend&#8221; his coin which is a severe issue.</p>
<p><strong>double-spending attack</strong> &#8211; someone one tries to spend a coin more than once.</p>
<p>Brainstorm ways to stop it:</p>
<p>Have a single ledger that everyone looks at. That would be similar to a bank today in that the bank holds one&#8217;s balance.</p>
<h4>Scrooge Coin</h4>
<p>This coin tries to prevent what happened with Goofy Coin. However it still has the property that only Scrooge creates coins. Scrooge publishes a history of all transactions (block chain, signed by Scrooge) instead of having others pass it along.</p>
<p>Scrooge is publishing then an append-only ledger. An append-only ledger means that any data written to the ledger will remain forever and thus only a single history will occur even if transferring of coins occurs between different people.</p>
<p>1 transaction per block for simplicity</p>
<p>Now Daffy and Porky cannot both get paid because Scrooge would have published both transactions and thus dependent on which one came first the other would be invalid. So while one person would lose, and it is not clear since it depends on which Scrooge publishes first. Having this published history helps people detect double spending and thus Porky can reject the coin if he notices that Donald is trying to send invalid coin.</p>
<p>Scrooge may also have the job to look for double spends as well and thus would only accept one and reject the other.</p>
<p>Here&#8217;s what it will look at breaking down the transactions.</p>
<p>Create Coins Block<br />
transID: ## type: CreateCoins<br />
num | value | recipient (pk)</p>
<p>Pay Coins Block<br />
transID: ** type: Paycoins<br />
consumed coinIDs:</p>
<p>coins created to new recipients</p>
<h5>Validity Rules for Scrooge</h5>
<ul>
<li>consumed coins valid</li>
<li>not already consumed (Within the same block?)</li>
<li>total value out == total value input</li>
<li>signed by owners of all consumed coins</li>
</ul>
<p>This transaction is signed by all owners who are payers</p>
<p>Coins are immutable so they&#8217;re constantly created and destroyed when you pay people.</p>
<p>Coins need to have at least these properties:<br />
Some transID(num) as its identifier<br />
Some value<br />
Some recipient that it belongs to</p>
<p>When a coin is paid, the old coin is consumed and a new coin is created</p>
<h5>What are the issues with Scrooge Coin?</h5>
<p>Still not decentralized and you have to trust Scrooge.<br />
If Scrooge stops creating, validating coins, and telling the truth, then the coin should no longer be trusted. He can allow for double spends as well as not meet people&#8217;s expectations in terms of how much coin they transferred.</p>