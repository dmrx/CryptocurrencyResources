---
layout: post
title: Hash Pointers
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2 style="text-align: center;"><strong>Hash Pointers</strong></h2>
<p>These are my notes of the fourth lecture from Coursera&#8217;s Bitcoin and Cryptocurrency Technologies during Dec 2016 &#8211; Feb 2017. The lecture gave me insight on some of the inner workings of blockchain which I greatly enjoyed.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">What is a hash pointer?</li>
<li style="text-align: left;">Once you have a hash pointer, what can you do with it?</li>
<li style="text-align: left;">What is the tamper evident property?</li>
</ul>
<h4>Hash Pointer</h4>
<p>Simply, a hash pointer is a kind of data structure that contains two parts</p>
<ul>
<li>pointer to where some info is stored</li>
<li>(cryptographic) hash of the info</li>
</ul>
<p>One feature of a hash pointer is we can ask to get the info back and verify that the information hasn&#8217;t changed. If you&#8217;re familiar with basic C programming, the word pointer should be very familiar. Hash pointers are similar to regular pointers which provide the memory address of some information and through the pointer you can access this information when you dereference it.</p>
<p>key idea: build data structures with hash pointers</p>
<h5>Linked List with hash pointers</h5>
<p>According to CLRS, a linked list is a data structure in which the objects are arranged in a linear order. A singly linked list contains an object with an attribute key and a next pointer. The head of the linked list is a hash pointer.</p>
<p><strong>Tamper Evident Log</strong> &#8211; log data structure that contains lots of data<br />
If someone messes with data earlier in the log, we want to be able to detect it.</p>
<p>Why does the block chain have this property?</p>
<p>If someone messes with a block in the middle of the chain. If he changes the data, then the hash generated for this block which is stored in the previous node also would need to change. So even though the hash of the previous block and the data block line up, the previous previous block next pointer is based on a hash of the previous block. Because the previous block is composed of both the data and previous Hash (which has a change) these would also indicate tampering. Thus the only way to make this block well is if you change the entire blockchain but at that point then the head of the block chain is incorrect and since this is the value that the users store, the user would be able to detect the tampering.</p>
<p>The head of the block chain is known genesis block.</p>
<h5>Binary tree with hash pointer (Merkle Tree)</h5>
<p>One takes consecutive pairs of data blocks and computes the hash of them. Thinking about a tree, you combine each pair of leaves to create a code. Combine the two blocks to create two hash pointers. Then, from those two hash pointers which were created from the left and right child, you make a hash pointer of that block where you point to the data. This occurs recursively until you get to some head hash pointer which as previously is what you store.</p>
<p>Bonus: You only need O(logn) data since you need to know the path of the block from the head to the leaf (data).</p>
<p><strong>Advantage of the Merkle Tree</strong></p>
<ul>
<li>Tree holds many items but only need to remember the root (I think you get that from the linked list)</li>
<li>Can verify membership in O(log n) time (this is the advantage over the linked list</li>
</ul>
<p><strong>Variant: Sorted Merkle Tree</strong></p>
<ul>
<li>can verify non-membership in O(log n)<br />
(show items before, after the missing one)<br />
One can prove that a block is not in a membership which I guess is just as important as well.</li>
</ul>
<p>Realistically hash pointers can be used in any acyclic data structure.</p>