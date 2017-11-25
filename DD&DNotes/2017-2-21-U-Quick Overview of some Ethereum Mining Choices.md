
<h2 style="text-align: center;">Quick Overview of some Ethereum Mining Choices</h2>
<p>I researched what was ethereum mining and would like to share what I&#8217;ve learned so far.</p>
<p>In January 2016, there were many documents and videos showing 6 easy steps for ethereum mining.<br />
One such video I watched was by Digital Decrypt called <a href="https://www.youtube.com/watch?v=IKtwSH6inBs">How to Mine Ethereum on a Windows PC &#8212; 6 Steps </a>. Here are two other websites guides which are likely more detailed than mine:<br />
<a href="https://www.cryptocompare.com/mining/guides/how-to-mine-ethereum/">CryptoCompares </a> and <a href="https://99bitcoins.com/guide-ethereum-mining-how-to-mine-ethereum/">99bitcoins </a>.</p>
<h5>Mining using Geth and Ethminer</h5>
<ol>
<li>Get <a href="https://geth.ethereum.org/downloads/">Geth </a></li>
<li>Run Geth (from cmd window type <i> geth account new</i>) Need an account to mine.</li>
<li>Activating Geth (cmd window type <i> geth &#8211;rpc </i>) Start communicating with others</li>
<li>Get ethminer (<a href="http://cryptomining-blog.com/tag/ethminer-cuda/">CUDA</a> or <a href="https://github.com/Genoil/">Genoil</a> )</li>
<li>Configuring ethminer</li>
<li>Beginning to Mine (in command window type for GPU <i><span style="color: #666699;"> ethminer -G</span> </i> or for CPU <span style="color: #666699;"><i> etherminer</i></span>)</li>
</ol>
<h5>Here is a short glossary of what you just downloaded.</h5>
<p><strong>Geth</strong>: Geth (implemented in the programming language Go) lets one create fully connected node to Ethereum. With Geth, you can connect to the Ethereum network which is necessary for mining.</p>
<p><strong>ethMiner </strong>:(written in C++) This is the mining program. It will utilize your machines CPU/GPU to run the hashing program (EtHash)</p>
<p><strong>EtHash</strong>: This is Ethereum&#8217;s proof of work algorithm.</p>
<p><strong>Mist</strong>: the Go client GUI and web3 browser</p>
<p>From Oct 2016, I found a platform where one can mine called <a href="https://minergate.com/">MinerGate</a>. MinerGate is a mining pool which has fourteen currencies listed to mine including ethereum. Go <a href="https://minergate.com/faq/about-minergate-pool">here </a> for the exact ones in case they change.</p>
<h5>Mining with MinerGate:</h5>
<ol>
<li>Create an account with <a href="https://minergate.com">minergate.com</a></li>
<li>Download the MinerGate software and install it to your computer</li>
<li>Just go to the top tab <strong>Miner</strong> and click <strong>Eth</strong>. If you want MinerGate to do its job, stay at the top tab <strong> Smart Miner </strong> to proceed that way.</li>
<li>Start mining and don&#8217;t be worried when MinerGate create a DAG file onto your machine. That&#8217;s normal.</li>
</ol>
<h5>Miner with ethMiner and Genoil miner</h5>
<ol>
<li>Create an account with <a href="https://minergate.com">minergate.com</a></li>
<li>Download your miner software ie (ethMiner or Genoil miner)</li>
<li>Within the command window, you&#8217;ll type the below commands to mine the individual types.</li>
</ol>
<p>For EthMiner, the pattern is below</p>
<h4>CPU mining:</h4>
<p><code><br />
Ethminer.exe -C -F http://eth.pool.minergate.com:55751/YOUR_EMAIL --disable-submit-hashrate<br />
</code></p>
<p>For Genoil, the pattern is below. Note the difference between OpenCL and CUDA is the first parameter after ethminer.</p>
<h4>OpenCL</h4>
<p>&nbsp;</p>
<p>setx GPU_FORCE_64BIT_PTR 0<br />
setx GPU_MAX_HEAP_SIZE 100<br />
setx GPU_USE_SYNC_OBJECTS 1<br />
setx GPU_MAX_ALLOC_PERCENT 100<br />
setx GPU_SINGLE_ALLOC_PERCENT 100</p>
<p>ethminer -G -S eth.pool.minergate.com:45791 -O YOUR_EMAIL</p>
<h4>CUDA</h4>
<p><code><br />
setx GPU_FORCE_64BIT_PTR 0<br />
setx GPU_MAX_HEAP_SIZE 100<br />
setx GPU_USE_SYNC_OBJECTS 1<br />
setx GPU_MAX_ALLOC_PERCENT 100<br />
setx GPU_SINGLE_ALLOC_PERCENT 100</code></p>
<p>ethminer -U -S eth.pool.minergate.com:45791 -O YOUR_EMAIL</p>
<h4>Few difference between Ethereum versus Bitcoin mining</h4>
<p>One major difference that I can see is that Ethereum blocks occur every 10-15 seconds on average while Bitcoin occurs every 10 minutes. The reward for Eth is 5 ETH while the current reward for Bitcoin is 25 BTC.</p>
<p>Another is that there is a different hashing algorithm to bitcoin so the ASICs developed for Bitcoin are not usable for Ethereum. Ethereum is ASIC resistant since Ethash has a memory hard algorithm. This means while GPU would help against CPU, ASICs should not work.</p>
<p>There seemed to have been a weird ETH ASIC scam going around some of the forums <a href="https://steemit.com/ethereum/@elyaque/first-asic-miners-for-ethereum-classic-available">Steemit Ethereum </a>and <a href="https://forum.ethereum.org/discussion/6586/we-are-dead-eth-asic-are-out">Ethereum.org Forum </a> like 8 months ago (Aug 2016). Key takeaway was to watch out because it was a <b>SCAM</b>.</p>