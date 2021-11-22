*-This part should be included in [the Review of the 3rd Chapter](https://www.jianshu.com/p/b44b24f63607), I listed it separately since it's really essential throughout this one.-*

**Key Takeaway**

* Fundamentals of Number Theory
* Euler's Function/Theorem
* Euler's totient theorem (Fermat-Euler Theorem)
* Fermat's little theorem

Let's construct a simple framework of RSA algorithm, this helps us have a **basic intuition** of RSA algo. .

We have $p,q \in Prime$, a very large number $N$ which is the product of $p,q$. Then, we got an Euler's function $\phi(n)=(p-1)(q-1)$ which stands for the cardinality of the set of all integers not exceeding $n$ that are relatively prime to $n$, ( that is$N$).

Next, we find a integer $e, 1 \leqslant e \leqslant n$ randomly, $s.t.  gcd(e,\phi(n))=1$.

By Bezout's theorem, $ \exists $ integers$ x,y,  s.t. $
$$
 xe-y\phi=1 \\
 ex=1+\phi y  \quad...*
$$

The equation above is the soul of the RSA algorithm. We take $x$ as the **private keys**, $N,e$as the **public keys**, which can be sent without being encrypted. Let's directly dive into a scenario through the given example below.

>Assuming a real live scenario, two best friends, Chang and Xuan, want to send whispers to each other through RSA. Firstly, Chang sends a public key $N$ to Xuan publicly. Suppose the message has been converted to a sequence of numbers called $A$.

 

Concentrate on these two formulas below

$$
A ^ e \equiv R\ mod \ N  \ \qquad (1)\\ 
R ^ x \equiv A\ mod \ N \   \qquad (2) ...(\dagger)
$$

Once Xuan received the $N,e$, he finds the $A$ to the power of $e$ modular $N$, i.e. the reminder $R$, and sends it to Chang. To decrypt $R$, Chang only needs to get the $R$ to the power of $x$(**private key**) modular $N$. For now, we have basically gone through the concept of the RSA Algorithm.

Let's go in-depth step by step. You might get confused that why these two formulas hold. According to the logic above$(\dagger)$ and the marked equation $*$(do a substitution), we can deduce

$$
(A^e)^x \equiv A^{1+\phi y} \equiv A*A^{\phi y}
$$

To show the formula (2) can hold, we just simply prove the $A^{\phi y}\equiv1$. Fortunately, we do have a mathematical theorem to support this argument, that is the famous **Euler-Fermat theorem**, AKA the Euler totient theorem: if we have an Euler totient func. $\phi(n)\  \text{with}\ gcd(a,n)=1$, then

$$
a^{\phi(n)} \equiv 1\  mod\ N
$$

When $N$ is prime (which means $\phi(n)=n-1$), this formula would degrade to **Fermat's little theorem**

$$
a^{p-1} \equiv 1\ mod\ P
$$

We have the following deduction,

$$
A^{\phi y} \equiv (A^y)^{\phi} 
\equiv a^{\phi} \equiv 1 \mod N
$$

Obviously, $y$ means nothing to the RSA algorithm here as long as $a$ is relatively prime to $N$, and if we just go and ignore the tedious mathematical proof, it's good to leave a $Q.E.D.$ here. Later I would try to raise a proper example to demonstrate the completed algorithm better.
