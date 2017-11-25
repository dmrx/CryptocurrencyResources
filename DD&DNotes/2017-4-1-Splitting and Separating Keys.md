---
layout: post
title: Splitting and Separating Keys
status: publish
published: true
meta:
  _edit_last: "1"
type: post
tags:
---
<h2>Splitting and Separating Keys</h2>
<p>This lecture adds a twist to the key management system by adding a new feature. Currently one downside with  bitcoin key management is that, if you lose your passphrase/physical bitcoin wallet, you are likely in trouble. Loss of your key can be synonymous with loss if bitcoin unless you had safeguards in place. Using <a href="http://www.deltadeltaandmoredeltas.com/hot-and-cold-bitcoin-storage/" target="_blank">hierarchical deterministic wallets</a> is one type of safeguard. We now address is there a better way then relying on a single passphrase. Can we  remove this <strong> single point of failure</strong>?</p>
<p>I presented many ways to hide or keep safe your wallet but this feature takes it to a new level. Now, instead of just hiding the wallet, we&#8217;re going to split up and separate the key. This means that if someone is able to find one of our hiding spots, as long as most of the others are safe, your keys are still protected. While the general technique is called secret sharing, it seems like this lecture covered<a href="https://cs.jhu.edu/~sdoshi/crypto/papers/shamirturing.pdf"> Shamir&#8217;s</a> version.</p>
<p>Questions answered in this Post:</p>
<ul>
<li style="text-align: left;">Why would you want to split keys?</li>
<li style="text-align: left;">What is secret sharing?</li>
<li style="text-align: left;">What are the positive and negative attributes of secret sharing?</li>
<li style="text-align: left;">What is Shamir&#8217;s secret sharing algorithm?</li>
<li style="text-align: left;">Explain briefly how it works.</li>
<li style="text-align: left;">How does multi-signatures improve the system?</li>
</ul>
<h2>The Magic of Secret Sharing</h2>
<p><a href="https://www.jetico.com/web_help/bc8/html/08_1_new_key_generator/03_SSS.htm" target="_blank">Secret Sharing</a> (cryptographically) refers to method to distribute a secret into various parts such that each of those parts are useless alone and only when combined with other parts can the secret be reconstructed. I mentioned removing that single point of failure as one use case for this mechanism. Another could be having a group of partners that collectively own a lot of bitcoin and for any transactions to occur on this bitcoin they require at least 2 of the partners to participate in the transaction. This scheme is building trust into the system without requiring the use of some third party lawyer. It also means that if some of these partners were to leave the pact or die, the bitcoin is still secure and accessible.</p>
<h3>Simple Idea<br />
split secret key into some number of pieces, such that given just a partial number of pieces, can reconstruct the original secret, and if given fewer than some threshold number of pieces, you can&#8217;t learn anything</h3>
<p>To me this entire idea sounds like a nifty number theory trick. Bare with me because it is pretty neat. Also, this trick is not as simple as just breaking up the secret key into 10 pieces where if it were a 40 character secret key you just chuck out 4 digits each time. This method allows that if you broke up the piece into 10 pieces, then you may only need 8 of them to complete the full secret key. Now before we go to large number of pieces, let&#8217;s just start with a simpler case.</p>
<h3>Base Case</h3>
<p>Suppose you are able to generate from the secret key, two transformations of the secret key. Now to reconstruct the secret key, both transformations need to be combined so that the secret key can be created. Having just one of the transformations is insufficient to return the original key.</p>
<p><strong>Example N=2, K=2</strong></p>
<p><strong>Secret Key</strong>= &#8220;Sky is Gold&#8221;</p>
<p><strong>P</strong> = a large prime number<br />
<strong>S</strong> = secret key that is within the bounds [0,P)<br />
<strong>R</strong> = random number between  [0, P)</p>
<p>To generate <strong>S, </strong>I took the secret key phrase and converted it to a large number with python.<br />
<code><br />
import hashlib<br />
message = "Sky is Gold"<br />
S = int(hashlib.sha256(message).hexdigest(), 16)<br />
print(S)<br />
58771470648245278604116241071520971200801549972357756564470365515982039414038L<br />
</code></p>
<p>From <strong>S</strong>, we generate two transformation of the number from the below formula to create X_1 and X_2.</p>
<p><img alt="init_eq" class="alignnone wp-image-137 size-medium" src="https://i2.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/init_eq.png?resize=300%2C112" /></p>
<p>These two keys can not be separated and stored on two different machines or with two different people. The keys need to come together if you are going to make a transaction. This works by applying the below formula.</p>
<p><img alt="final_eq" class="alignnone size-full wp-image-136" src="https://i0.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/final_eq.png?resize=238%2C27" /></p>
<p>How does this formula work? Why does the left hand side equal the write. I&#8217;m sure I could say <a href="https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/what-is-modular-arithmetic" target="_blank">modular arithmetic</a> and some people would nod their heads and be happy. I&#8217;m not one of those people so I&#8217;ll walk through at least a written out example in case you&#8217;re curious, unsatisfied, and have a &#8220;show me&#8221; attitude. Below, I&#8217;ve rewritten the formula to be more explicit as to what modulus means. A mod B means to divide A by B and then output the remainder. 10 mod 5 would equal 0 because 10 / 5 is equal to 2 with no remainder. On the other hand 11 mod 5 would equal 1 because 11  / 5 equals 2 remainder. Another way to represent this is 2 * 5 + 1 = 11 which is exactly what the below equation does.</p>
<p><img alt="rewrite_eq" class="alignnone size-full wp-image-135" src="https://i1.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/rewrite_eq.png?resize=213%2C57" /></p>
<p>The letters n and m represent how many times (S + R) and (S + 2R) divide into the prime number P. Concretely think of n and m as 5. What is useful to  know is that similar to how 10 mod 5 is equal to 0 because 2 * 5 equals 10 which can be rewritten as 2 * 5 mod 5, n * P mod P and m * P mod P will both equal 0. Below I&#8217;ve tried to expand my reasoning by utilizing<a href="https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/modular-addition-and-subtraction" target="_blank"> addition property of modular arithmetic. </a></p>
<p><img alt="explicit_eq" class="size-full wp-image-134" src="https://i2.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/03/explicit_eq.png?resize=425%2C223" /></p>
<p>Voila! At least you can see now how this works for the simple case with N = 2 and K = 2. Now what if we want expand this further. Now instead of having only two partners, let&#8217;s say there are 10 partners that we wish to give keys so that any two of those partners may come together to reconstruct the key.</p>
<p>He then drew a Cartesian plane and declared that you could plot a line with the Y-intersect being (0, S) and slope R. I made my own figure below. He claimed that given any two points on the line, one can interpolate it and find S. I agree that one can get any point on the line given two points that exist on the line. One point gives very little information since there are infinitely many lines that could be drawn.</p>
<h2><img alt="(0,S), (1,S+R), (2,S+2R)" class="alignnone size-full wp-image-138" src="https://i2.wp.com/www.deltadeltaandmoredeltas.com/wp-content/uploads/2017/04/linear_eq.png?resize=500%2C262" /></h2>
<p>Next he jumped from looking at a line to a<a href="https://en.wikipedia.org/wiki/Parabola"> parabola</a>. A parabola can be defined by three points. If you used three points, you would be able to recover S if the parabola was fitted in such a way to embody the values of S and R within it. This entire system relies on a very large polynomial P and some value R. This can be expanded to higher values by using higher order polynomials. I think this is pretty sweet and I found a cool github library called <a href="https://github.com/blockstack/secret-sharing">secret-sharing. </a>I also found this <a href="http://point-at-infinity.org/ssss/">ssss</a> site use and a site on <a href="https://math-linux.com/mathematics/interpolation/article/lagrange-interpolation-polynomial">Lagrange Interpolation</a> useful to understanding these concepts. Lagrange interpolation is the mathematical formula that lets you reconstruct higher order polynomials given K  points for a K &#8211; 1 order function. This means needed two points to construct a line and three points to construct a parabola.</p>
<p>I&#8217;ve been raving about secret sharing since it is way to break up a secret key and solve the issue with the single point of failure if the secret key were to get lost. Also, you are able to lost some of the secret keys as long as at least K of them exist. Realize that when you need to use the secret key, at least those K pieces need to be combined to recreate the secret. At this time, because you have the secret key constructed, there is a vulnerability. This vulnerability is still present without secret sharing. Using<a href="http://www.deltadeltaandmoredeltas.com/escrow-transactions-using-multisig/" target="_blank"> multi-signatures </a>which I discussed earlier is one way to remove that restriction. Another method is using something called <a href="https://en.wikipedia.org/wiki/Threshold_cryptosystem">threshold cryptography</a>. My simple understanding of threshold cryptography is that it allows one to reconstruct the secret key without the components having to come together.</p>
<h2>Multi-signature algorithm</h2>
<p><a href="http://www.deltadeltaandmoredeltas.com/escrow-transactions-using-multisig/" target="_blank">Multi-Sig</a> -lets you keep shares apart, approve transaction without requiring reconstructing key at any point.</p>
<p>Multisignature solves many of the shortcomings of secret sharing. Many wallets implement this which allows you to take advantage of this feature. While it is different from secret-sharing, it&#8217;s useful to know and seems to be the approach many wallets have given to consumers.</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>