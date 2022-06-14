## Euclidean Algorithm

### Statement
The gcd of two non-negative integers $a$ and $b$ ($a >= b$ for simplicity) will be equal to the gcd of $b$ and $a \bmod b$ (Modulo) i.e. $$gcd(a,b) = gcd(b,a \bmod b)$$

### Proof Of Concept

#### Given: 
* Two positive integers $a$ and $b$
* $a > b$ 

#### Proof :
Let's say $d$ is the gcd of $a$ and $b$, $ gcd(a,b) = d$.


Since $a$ is greater than $b$ it can be written as 

$$ a = q.b + r $$ 

where $q$ and $r$ are any non-negative integers. 

Since $d$ is the gcd of $a$ and $b$, it should pefectly divide them both. Divide above equation by d

$$ a/d = q.b/d + r/d $$

let's say $ a/d = m $ and $ b/d = n$ 

Both $m$ and $n$ should be an integer and equation becomes

$$ m = q.n + r/d $$

For m to be an integer, $ r / d $ should also be an integer, which means $d$ must divide $r$ completely.

This means $d$ is also the gcd of $b$ and $r$, $gcd(a,b) = gcd(b, r)$ and that can be written $gcd(a,b) = gcd(b, a \bmod b) $


### Finding GCD
GCD of a and b can be written: 
$$ gcd(a, b) = gcd(b , r) = gcd(r, r1)...... gcd(rN, rM)$$

where $ r = a \bmod b $ and $ r1 = b \bmod r $ and so on...

Now let say $rM$ completely divides $rN$ i.e. $rN \bmod rM = 0$

$$ rN = z.rM $$ 

where $z$ is some positive integer. At this point we can say $rM$ will be the gcd of $rN$ and $rM$ i.e. 

$$gcd(rN, rM) = gcd(rM, rN \bmod rM) = gcd(rM, 0) = rM $$

From this $$ gcd(a, b) = gcd(b , r) = gcd(r, r1)...... gcd(rN, rM)$$

we can say

$$gcd(a,b) = gcd(rM, 0) = rM$$

When the second parameters turns zero the first will be gcd of given number a and b. 

### Code

```
function gcd(a , b) {
    if(b == 0) {
        return a;
    }

    if(a < b) {
        // we assume first to be greater than second
        return gcd(b , a);
    }

    return gcd(b, b%a);
}
```