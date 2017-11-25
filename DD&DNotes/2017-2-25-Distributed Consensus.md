---
layout: post
title: Distributed Consensus
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<p>These are my notes of the seventh lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017. This was a great lecture in that it started more from fundamentals to explain how decentralization has been done in bitcoin.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">Define consensus and distributed consensus.</li>
<li style="text-align: left;">What is a distributed consensys protocol?</li>
<li style="text-align: left;">What does consensus mean in Bitcoin</li>
<li style="text-align: left;">How does consensus work in bitcoin?</li>
<li style="text-align: left;">With all the pessimism with distributed consensus, what enables bitcoin/makes it less at risk for these shortfalls?</li>
</ul>
<p>Before we can started talking about distributed consensus and consensus for bitcoin, what on earth is consensus? According to the Merriam-Webster dictionary&#8230;</p>
<p><strong>Consensus:</strong></p>
<blockquote><p>general agreement about something; an idea or opinion that is shared by all people in a group</p></blockquote>
<p>Great, now what is distributed consensus?<br />
Well, when related to computer science, how can multiple main computer nodes agree on a single idea/piece of data if they are receiving different inputs. Then a consensus protocol is the answer to the question on &#8220;How&#8221; these nodes can come into agreement. If one is interested then please google &#8220;distributed systems protocols&#8221; to learn about these. Or just look at things like distributed hash tables or Paxos.</p>
<h4>Distributed Consensus Protocol</h4>
<p>Def<br />
fixed number of nodes, n<br />
each nodes have some input value</p>
<ol>
<li>each nodes have some input value</li>
<li>protocol terminates and all correct nodes decide on the same value</li>
<li>this value must have been proposed by some correct node</li>
<li>in this scenario there are bad, faulty, and malicious nodes as well as the correct nodes.</li>
</ol>
<h4>Consensus in Bitcoin</h4>
<p>Bitcoin is a peer to peer system. When Alice wants to pay Bob, she broadcasts the transaction to all Bitcoin nodes that comprise the peer-to-peer network. Also, Alice and Bob are not the only individuals broadcasting out transactions.</p>
<p>signed by Alice<br />
pay to pk_Bob: H()<br />
contains Hash of the coins history</p>
<p>Bob is not on the system he needs to be a bitcoin node to hear it</p>
<p>Consensus in bitcoin means if all these people are broadcasting their transactions and all these nodes are hearing them, how do you determine which transactions were broadcast, which were valid, and in what order. By the end, there should be a single, global ledger that is maintained by all. However, it also means that nodes will also have transactions they have that may not be on the block yet. These are called outstanding transactions.</p>
<p>How consensus could work in Bitcoin?<br />
at any given time:</p>
<ul>
<li>All nodes have a sequence of blocks of transactions they&#8217;ve reached consensus on</li>
<li>Each node has a set of outstanding transaction they&#8217;ve heard about (these have not reached consensus</li>
</ul>
<p>Scrooge Coin: transactions were put into blocks</p>
<h4>Why is bitcoin blockchain consensus hard?</h4>
<ul>
<li>Nodes may crash</li>
<li>Nodes may by malicious (put invalid transactions in blocks)</li>
<li>Network is imperfect</li>
<li>Not all pairs of nodes connected</li>
<li>Faults in network (poor network connectivity)</li>
<li>Latency since these nodes are all over the internet</li>
</ul>
<p>With high latency, this also means that there is no notion of global time. The ordering agreed upon does not indicate time. All we know is that one node was put one the block chain prior not which transactions actually was broadcasted and heard first. Because of this constraint, many consensus protocols in literature tend to be pessimistic. You get these impossibility results.</p>
<h4>Impossibility Result Examples</h4>
<p><a href="https://www.microsoft.com/en-us/research/wp-content/uploads/2016/12/The-Byzantine-Generals-Problem.pdf">Byzantine Generals Problem</a> which resulted in if a third or more of the generals (nodes) were traitors when it was impossible to achieve consensus.</p>
<p>Fischer-Lynch-Paterson (deterministic nodes)<br />
which proved that consensus impossible with a single faulty node</p>
<p>Paxos &#8211; never produces inconsistent result<br />
protocol can get stuck and never make any progress</p>
<p>These pessimistic models tend to shed light on the idea that bitcoin is the same problem as resolving a distributed database and thus can make concessions that the others were unable to.</p>
<h4>Consensus in bitcoin: theory versus practice</h4>
<p>While theory may sound pessimistic, practice seems to work better. This may be due to special features of bitcoin. Also, bitcoin contains the idea of incentives because it&#8217;s a currency. Second, bitcoin embraces randomness where as proper distributed systems hate it. Actually the consensus algorithm relies on randomness. So while you can never by 100% confident, you can be extremely confident when a block has entered the ledger. Also, the latency is fine since at this point, it&#8217;s one every ten minutes.</p>