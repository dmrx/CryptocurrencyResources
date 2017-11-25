---
layout: post
title: Energy Consumption and Ecology
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h1><strong>Energy Consumption and Ecology<br />
</strong></h1>
<p>This lecture sought to look at the effects of bitcoin mining from a different perspective. At least in July 2016, bitcoin mining is dominated by certain p2p pools. If you want some historical data regarding the bitcoin mining network, checkout <a href="http://organofcorti.blogspot.mx/">Neighbourhood Pool Watch</a>. According to <a href="https://bitnodes.21.co/">bitnode21</a>, there were 7599 nodes running on June 2017. This does not necessarily indicate the number of existing miners but should shed some light. The estimation from this <a href="https://bravenewcoin.com/news/number-of-bitcoin-miners-far-higher-than-popular-estimates/">Brave New Coin article</a> suggests around 100,000 miners. While, the statistics on mining pool estimates and miner hashrates is interesting, that was not the core focus on this lecture.</p>
<p>This lecturer focused on looking at the ecological effects that bitcoin may have.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">How do you defined energy used by bitcoin?</li>
<li>Where can I find the distribution of miners?</li>
<li style="text-align: left;">In terms of usage, how does that compare to modern life?</li>
<li>What should we do with this excess energy, if anything?</li>
<li>Think about more open questions.</li>
</ul>
<p>The lecture first begins with the <strong>Landauer&#8217;s principle </strong>developed by Ralph, you guessed it, Landauer in the 1960s. The principle states that any non-reversible computation must consume a minimum amount of energy. Each bit change requires kT ln 2 joules. This amount derived from basic physics. However, currently this is the theoretical minimum and at this point in time there is significantly more energy used.</p>
<p>Because energy is never destroyed, but transformed into something else. Note, <strong>SHA-256</strong> is not reversible meaning that energy consumption is inevitable. We walked through the three main energy aspects of mining: embodied energy, electricity, and cooling.</p>
<h3>Main Energy Aspects</h3>
<ol>
<li style="text-align: left;"><strong>Embodied energy</strong>: energy required to manufacture mining chips and ship it to the users which theoretically should decrease over time and returns to scale</li>
<li style="text-align: left;"><strong>Electricity</strong>: energy needed to perform the computations which will increase over time and returns to scale. This is where Landauer&#8217;s energy comes to play.</li>
<li style="text-align: left;"><strong>Cooling</strong>: energy need to protect equipment that is doing the mining which will cost more with increased scale</li>
</ol>
<h3>Follow up Notes</h3>
<p>He makes a point regarding the embodied energy that I&#8217;m not sure I agree with. It is that mining circuits will be obsolete less quickly. This was counter to what was previously discussed where with mining rigs, people are able to get rewards initially but slowly over time, less rewards are gained. Also, companies keep making newer and newer hardware that individuals have to purchase to keep up with the increased difficulty. Maybe this is a longer term goal that will be achieved later on&#8230;</p>
<p>Also, these electricity costs are relative. If you do you mining in a cooler climate, you don&#8217;t need to spend as much on cooling.</p>
<p>From March 2015, they post some statistics about energy usage. $.10/kWh since each block at this time was worth $15,000. $25/s and upper bound of electricity consumed is 900 MW.<br />
Then he went over a second calculation which was bottom-up approach. This approach looked at the number of hashes the miners were computing and then try to derive a lower bound of electricity consumption by assuming miners were using the most efficient hardware. The cutting edge ASICs performs 3 billion hashes per second while consuming 1 watt of power. The total network hashrate is about 350,000,000 GH/s then is takes about 117 MW to produce that many hashes per second. While these are just estimates, the idea is that miners are likely using a few hundred MW.</p>
<p>It was nice that after doing this calculation he gave a nice example of a frame of mind for what a megawatt means.</p>
<table style="height: 78px;" width="660">
<tbody>
<tr>
<th>Name</th>
<th>MW Used</th>
</tr>
<tr>
<td>Bitcoin Miner</td>
<td>~100-800 MW</td>
</tr>
<tr>
<td>Typical Hydroplant</td>
<td>1000 MW</td>
</tr>
<tr>
<td>Coal-fired plant</td>
<td>2000 MW</td>
</tr>
<tr>
<td>Nuclear Plant</td>
<td>4000 MW</td>
</tr>
<tr>
<td>Kashiwazaki-Kariwa (Nuclear)</td>
<td>7000 MW</td>
</tr>
<tr>
<td>Three Gorges Dam (Hydro)</td>
<td>10000 MW</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>The whole bitcoin network is consuming less than an entire power plant. That sounds more serious then the lecturer presented it as. Though he does rationalize it by saying that all payments systems require money such as storage of money/electronic transfers. It would be interesting if someone computed roughly the usage of credit cards as compared to the bitcoin miners.</p>
<h3>Data Furnaces</h3>
<p>Well, he then took the next logically step which was &#8220;Can we do something with this heat generated?&#8221;. The mining rig could also serve as a heater for your home. This mining rig is generating heat based on electricity. He mentions three challenges for this. One deals with that fact that gas heaters are 10x more efficient than electric heaters. Personally, while true, I don&#8217;t think this should prevent people from at least testing out this approach. I think electric versus gas and I think electric cars and Tesla. Simple minded, probably, but until I look into it further there is still a window of hope in my mind. The second challenge he mentioned was the ownership/maintenance model. Who owns the rewards that the machine gains? This is easily summed that the company would likely take the profit. It is foolish to think maybe if there is a smart contract on the mining rig that that contract should hold onto the coins? The last is that within the summer, the heater would not be used as heavily. If there is less mining power, what happens to the bitcoin mining? People would have odd incentives to use the heater in summer if they think others will not be using it and thus the difficulty may be lower.</p>
<p>This lecture was a series of &#8220;what ifs&#8221;. There is no conclusive evidence provided and merely this section to me sought to have the listener keep asking more questions.</p>
<h6>Questions</h6>
<p>Which of the following are assumptions made about the UPPER bound for the energy used for mining Bitcoins?</p>
<ul>
<li>Miners mine up to the point that all of the money they earn is used to pay for electricity</li>
<li>Miners all pay the same for electricity</li>
</ul>
<p>Which of the following are assumptions made about the LOWER bound for the energy used for mining bitcoins?</p>
<ul>
<li>Everyone mines where it is cold(cooling doesn&#8217;t consume energy)</li>
<li>Everyone mines at the maximum claimed efficiency</li>
</ul>