---
layout: post
title: Mining Hardware: what kind of special hardware do I need?
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Mining Hardware<br />
</strong></h1>
<p>I&#8217;m not 100% why this lecture was not touched upon earlier. Since I thought I had this great understanding of SHA-256 back in<a href="http://www.deltadeltaandmoredeltas.com/cryptographichashfunction/"> lecture 1 </a>and now I&#8217;m like, I was a fool.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What else should I know about SHA256?</li>
<li style="text-align: left;">What is this mysterious function miners have to compute?</li>
<li style="text-align: left;">Where can I find a Bitcoin ATM?</li>
<li style="text-align: left;">What simple ways did they classify owners of bitcoin?</li>
<li style="text-align: left;">Using the fiat mediated transaction model, what happens when supply is too low?</li>
</ul>
<h3>SHA256: more words about it</h3>
<p>As mentioned earlier, it is a general purpose hash function. General purpose meaning that there is a list of other SHA-2 functions. SHA-2 stands for <span class="_Tgc">Secure Hash Algorithm <b>2</b></span> and was designed by the NSA. Yes, there is a SHA-1 if you&#8217;re curious and people are working on SHA-3. SHA-2 consists of SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, SHA-512/256. They are considered unbroken cryptographically even if there are known weaknesses. SHA-256 is computed with 32-bit words and SHA-512 is computed with 64-bit words. One takeaway is that SHA-256 has been optimized for 32-bit systems.</p>
<p>He showed a picture which reminded me of a crazy logic puzzle. OK, not really that but here&#8217;s a representative picture below. This is not the exact picture but a very similar one taken from Wikipedia.</p>
<p><a href="https://en.wikipedia.org/wiki/SHA-2"><img alt="" class="aligncenter size-medium wp-image-176" src="https://i1.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/06/600px-SHA-2.svg_.png?resize=300%2C212" /></a>Yet even in this lecture, he says we don&#8217;t really need to know SHA-256. He did give an overview which was more than we got previously. In the pictures you see the letters &#8220;A-H&#8221;, which are actually 8 32-bit words. As a sanity check, 8 * 32 = 256 so we&#8217;re still working with 256 bits. There are four computation rounds that take place. In each computation round, different bits are tweaked and then their bits are added and then everything is mod 32. A complete computation does 80 different iterations.</p>
<p>Honestly whenever I&#8217;ve used SHA-256 I just use a library to do it without thinking about the mechanics. However, after learning more about the importance with mining , this reflects what kind of work miners have to do. A basic code as presented from the lectures is listed below and you can observe that they are also calling SHA256 not once but twice.</p>
<p>while (1) {</p>
<p>HDR[kNonePos]++;</p>
<p>if (SHA256(SHA256(HDR)) &lt; (65535 &lt;&lt; 208) / DIFFICULTY)</p>
<p>return;</p>
<p>}</p>
<p>A normal machine can compute this calculation 2^24 hashes per second (10 -20 MHz). When bitcoin first started that would have been sufficient. Back in 2013 when this lecture was released, he mentions it would take ~140,000 years.</p>
<p>The next level was to use GPU mining which allows for high-performance graphics allowing high parallelism and high throughput. It was implemented in OpenCL which had people hacking the individual implementation for specific cards used. There were advantage back then. It was easily available and to set up. You get parallel ALUs (<span class="_Tgc">arithmetic-logic unit</span>s), bit-speciic instructions, overclocking, and rig multiple ones from 1 CPU. If people tell you they have their own mining rigs, I picture some crazy space cowboy rig from like Cowboy Bebop. Now even GPUs are not good enough.</p>
<p>People introduced FPGAs which allow for higher performance for GPU and have better cooling implementations. However as of when the lecture was released, it would take 25 years to find a bitcoin block. So yes you get superior performance than before but you&#8217;re really not good enough.</p>
<p>Nowadays people use ASICs is they mine. ASICs (Application Specific integrated circuits), are hardware machines that are specialized to mine bitcoin. They have been designed specifically for mining and have adjusted for any changes in the environment but they do require major expertise and long lead-times. Usually you have to pre-order the ASIC miner and the important question to ask is when the hardware will be shipped. It was interesting that the TerraMiner IV ($6000)  would take around 14 months to mine a block. Also, most boards are considered obsolete within 3-6 months and most profits are made in the first 6 weeks. That means time is of the essence to get this machine<strong>.</strong></p>
<p>Basically miners have only really made money because the price if bitcoin has exploded. There are now professional mining centers. He mentions one from the Republic of Georgia. To create one, you need cheap power, good network, and cooler climate.</p>
<p>&nbsp;</p>
<p><strong>Takeaway from this lecture, you&#8217;re never going to be good enough to mine bitcoin unless you have special skills, money, and live in an appropriate environment&#8230; </strong></p>
<h3>Remaining questions:</h3>
<ol>
<li>Can small miners stay in the game?</li>
<li>Do ASICs violate the original Bitcoin vision by going against every individual being part of the netowrk and working together?</li>
<li> Would we be better off without ASICs?<br />
Which statement about Bitcoin miners is NOT true?<br />
Bitcoin miners can recoup a reasonable fraction of their initial expenses by selling their ASICs once they are done with them to other users for less computationall intense purposes.</li>
</ol>