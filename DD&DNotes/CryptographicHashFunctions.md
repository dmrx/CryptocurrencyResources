# **Cryptographic Hash Function**

These are my notes of the first lecture from Coursera’s Bitcoin and
Cryptocurrency Technologies during Dec 2016 – Feb 2017.

## Questions answered in this Post:

-   What is a cryptographic hash function?
-   What are the security properties?
-   What are the applications of some of these properties?
-   What does SHA-256 do at a simple level?

## Hash Function

-   takes any string as input
-   fixed size output (256 bit bitcoin uses)
-   efficiently computable (can figure out output in a reasonable amount
    of time)

## Security Properties

-   collision-free
-   hiding
-   puzzle-friendly

### **Collision-free**

Math definition – nobody can find x and y where x != y and H(x) = H(y)

in words:  
nobody can find two different input strings so that if you apply the
hash function to them, they have the same output.

the idea that nobody can find really means it’s really really really
hard to find it….

Note that there has to be a collisions  
since you’re going from a much larger input space to a fixed output
space (2^256).

### **Hiding**

Given H(x), it is infeasible to find x.

If r is chosen from a probability distribution that has min-entropy,
then given H(r | x), it is infeasible to find x

High min-entropy means that the distribution is “very spread out” so
that no particular value is chosen more than negligible probability.

in words: if you are given the hashed version of x then you will be
unable to find x

## **Puzzle Friendly**

for every possible output value y,  
if k is chosen from a distribution with a high min entropy (super spread
out) then it is infeasible to find x such that H(k|x) = y.

If someone wants to target a certain hash function, get some value of y,
if part of the input is chosen in a random way, it’s difficult to find
another value to target the hash function value.

Given a “puzzle ID” id ( from high min-entropy distribution) and a
target set Y:  
Try to find a “solution” x such that H(id|x) \\in Y.

*id | x means id concatenated x*

## Application of having something **collision-free**

Hash becomes a message digest meaning that you can use the has as a
replacement of the msg  
You can use H(x) and H(y) as smaller forms of the input string.

So if H(x) = H(y) then x = y.  
Technically H(x) is only 256 bits while the x can be of some large
arbitrary length

## Application of **puzzle friendly**

Puzzle friendly property implies that no solving strategy is much better
than trying random values of x

## Application of the **hiding property**

In words, the idea is that you want to create a secret message that you
can put in a public envelope.

## **Commitment API – to help explain public envelope example **

Want to “seal a value in an envelope” and “open the envelope” later

Commit to a value, reveal it later

(com, key) := commit(msg)  
match := verify(com, key, msg)

To seal msg in envelope:  
(com, key) := commit(msg) — then publish com

To open envelope:  
publish key, msg  
anyone can use verify(com, key, msg) to check validity

Want two security properties:  
Hiding: given com, infeasible to find msg;  
Binding: infeasible to find msg != msg’ such that  
verify(commit(msg, msg’) == true)

commit(msg) := (H(key | msg), key) where key is 256 bit  
verify(com, key, msg) := (H(key|msg) == com)

## More about the Security Properties

key is a randomly generated 256 bit value

Hiding: Given H(key | msg) infeasible to find mg  
Binding: Infeasible to find msg != msg’ such that  
H(key | msg) == H(key | msg’)

Basically can’t find two different messages where you committed to one
and verified with another one.

So you use the hash function in both commit and verify

What hash function will we use? **SHA-256**

## **Step by Step of what SHA-256 does**

1.  You have an input message of an arbitrary length
2.  You also have a 256 bit value called IV (Initialization Vector
    [(https://en.wikipedia.org/wiki/Initialization\_vector)](http://You%20also%20have%20a%20256%20bit%20value%20called%20IV%20(Initialization%20Vector)%20(https://en.wikipedia.org/wiki/Initialization_vector))
3.  The input string gets broken up into 512 bit blocks and we’ll
    reference them as block\_1, block\_2, block\_3, and block\_n will be
    the last block. The last block will also contain padding where the
    last 64 bits is the length of the input message and prior to that is
    a 1{0\*}.
4.  The 256 bit value and block\_1 come together as inputs to a
    compression function (c) which basically squashes the 768 bits back
    into 256 bits.
5.  Next the output of c gets mashed with block\_2 and to the
    compression function and out pops a 256 bit value.
6.  This continues along the entire length of the message where the last
    output is Voila, the hash.
