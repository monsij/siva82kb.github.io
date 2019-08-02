---
layout: post
title: "Representation of Numbers in Computers"
date: 2019-07-08 09:00:060 +0530
comments: true
categories: [computer-science]
---

I have long wanted to write something on the different binary number representations used in a computer, along their corresponding arithmetic operations. I would have loved to have stumbled into something like this during my undergraduate years. So, I also hope that this will be useful for others who might be looking tutorial-like material on numerical data types used in a computer, in particular _integers_, _fixed-point_, and _floating-point_ numbers.

### Whole Numbers
The binary representation of _whole numbers_ is something all of us are familiar with. In the decimal system, the nuber 235 is represented as the following,

$$ 235 = 2 \times 10^2 + 3 \times 10^1 + 5 \times 10^0 $$

In the decimal system, the base is 10, and 10 decimal digits $0-9$ are used.

This number has the following representation in the binary system, where the base is 2 and the the digits 0 and 1 are used.

$$ 235 = 1 \times 2^7 + 1 \times 2^6 + 1 \times 2^5 + 0 \times 2^4 + 1 \times 2^3 + 0 \times 2^2 + 1 \times 2^1 + 1 \times 2^0 = \left[ 11101011 \right]_2 $$

(Note: $$\left[\cdot\right]_2$$ _indicates that the number in the square brackets is a binary number_)

A $n$ bit binary number $B$ is written as $B = \left[ b_{n-1}b_{n-2} \ldots b_1b_0 \right]_2$, where $b_i \in [0, 1], \, 0 \leq i \leq n-1$. Let $d(\cdot)$ be the function that coverts a binary number $B$ to its decimal equivalent, $$ d(B) = \sum_{i=0}^{n-1} b_i \times 2^i $$. 
<style>
div .textbox {
  width: 100%;
  background-color: #fee;
  padding: 5px;
  border: 0px solid gray;
  margin-bottom: 10px;
  text-align: left;
}
</style>
<center>
<div class="textbox">
<b>Prove:</b> <i>The maximum whole number that can be represented by a $n$-bit number is $2^n - 1$.</i>
</div>  
</center>

Arithmetic operations on binary numbers are carried out exactly the way we perform decimal arithmetic. We will only consider the addition and multiplication operation at this point, as whole numbers are not closed under the subtraction and division.

**Binary Addition** can be carried out with the knowledge of the following truth table. Addition of two $n$ digit binary numbers $A$ and $B$ can result in a binary number $C = A + B$ with at most $n+1$ binary digits.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:2px 2px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:2px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg .tg-baqh{text-align:center;vertical-align:top}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-7btt{font-weight:bold;border-color:inherit;text-align:center;vertical-align:top}
</style>
<center>
<table class="tg">
  <tr>
    <th class="tg-7btt">A</th>
    <th class="tg-7btt">B</th>
    <th class="tg-7btt">C = A + B</th>
    <th class="tg-7btt">C = A x B</th>
  </tr>
  <tr>
    <th class="tg-7btt">0</th>
    <th class="tg-7btt">0</th>
    <th class="tg-7btt">00<sub>2</sub></th>
    <th class="tg-7btt">00<sub>2</sub></th>
  </tr>
  <tr>
    <th class="tg-7btt">0</th>
    <th class="tg-7btt">1</th>
    <th class="tg-7btt">01<sub>2</sub></th>
    <th class="tg-7btt">01<sub>2</sub></th>
  </tr>
  <tr>
    <th class="tg-7btt">1</th>
    <th class="tg-7btt">0</th>
    <th class="tg-7btt">01<sub>2</sub></th>
    <th class="tg-7btt">00<sub>2</sub></th>
  </tr>
  <tr>
    <th class="tg-7btt">1</th>
    <th class="tg-7btt">1</th>
    <th class="tg-7btt">10<sub>2</sub></th>
    <th class="tg-7btt">01<sub>2</sub></th>
  </tr>
</table>
</center>

**Binary Multiplication** can be carried out with the knowledge of the above truth table. Multipliation of two $n$ digit binary numbers $A$ and $B$ can result in a binary number $C = A \times B$ with at most $2n$ binary digits.

### Integers
When representing negative numbers, on paper, one could simply use the '-' symbols, e.g. -51 in binary can be written as -110011. Since 0s and 1s are the only available symbols when representing things on a computer, we need to find a way to represent negative numbers. The 2s complement convention is used for representing negative numbers. Lets assume that we have 3 bits to represent numbers; we can represent upto 8 different possible numbers with 3 bits. The binary representation of positive numbers and zero remain unchanged. However when we have a negaitive number $N$, we first take the binary representation of $-N$, invert the bits and add 1 to the inverted numbers. 

$$ -2 \xrightarrow[\text{binary}]{\text{2 in}} 010 \xrightarrow[\text{bits}]{\text{Invert}} 101 \xrightarrow[\text{01}]{\text{Add}} 110$$

In 2s complement representation, the most significant bit represents the sign bit, and it is 1 for negative numbers. As the following table indicates.

<center>
<table class="tg">
  <tr>
    <th class="tg-7btt">Binary No.</th>
    <th class="tg-7btt">Whole number</th>
    <th class="tg-7btt">Integer</th>
  </tr>
  <tr>
    <th class="tg-7btt">000<sub>2</sub></th>
    <th class="tg-7btt">0</th>
    <th class="tg-7btt">0</th>
  </tr>
  <tr>
    <th class="tg-7btt">001<sub>2</sub></th>
    <th class="tg-7btt">1</th>
    <th class="tg-7btt">1</th>
  </tr>
  <tr>
    <th class="tg-7btt">010<sub>2</sub></th>
    <th class="tg-7btt">2</th>
    <th class="tg-7btt">2</th>
  </tr>
  <tr>
    <th class="tg-7btt">011<sub>2</sub></th>
    <th class="tg-7btt">3</th>
    <th class="tg-7btt">3</th>
  </tr>
  <tr>
    <th class="tg-7btt">100<sub>2</sub></th>
    <th class="tg-7btt">4</th>
    <th class="tg-7btt">-4</th>
  </tr>
  <tr>
    <th class="tg-7btt">101<sub>2</sub></th>
    <th class="tg-7btt">5</th>
    <th class="tg-7btt">-3</th>
  </tr>
  <tr>
    <th class="tg-7btt">110<sub>2</sub></th>
    <th class="tg-7btt">6</th>
    <th class="tg-7btt">-2</th>
  </tr>
  <tr>
    <th class="tg-7btt">111<sub>2</sub></th>
    <th class="tg-7btt">7</th>
    <th class="tg-7btt">-1</th>
  </tr>
</table>
</center>
<br>

We can convert 2s complement number to the corresponding decimal number using the following formula,

$$ N = -b_{n-1}2^{n-1} + \sum_{i=0}^{n-2} b_i2^i $$ 

The followiing image shows another way to look at 2's complement numbers.
<center>
  <img src="{{ site.baseurl }}/figs/2scomp.png" width="40%" height="40%">
</center>

<center>
<div class="textbox">
<b>Prove:</b> <i>In the 2s complement representation using $n$-bits, (a) the highest positive integer that can be represented is $2^{n-1} - 1$; and (b) the lowest negative integer that can be represented is $-2^{n-1}$.</i> 
</div>  
</center>

**Binary Addition**. The truth table for addition is the same, and we can add two numbers like we did with whole numbers. This handles the addition of both negative and positive numbers, but we need to be careful when interpreting the results because of the sign bit. Addition of a positive number to a 2s complement number corresponds to moving in the clockwise direction along the cirle, while that of a neative number corresponds to anti-clockwise movement. 

We need to keep in mind the following conditions, which indicate an overflow:
  - Addition of two positive numbers cannot result in a negative number, e.g. $$ 3 + 2 = [011]_2 + [010]_2 = [101]_2 $$.
  - Addition of two negative numbers cannot result in a positive number, e.g. $$ -1 + -2 = [111]_2 + [110]_2 = [101]_2 $$. Note that the addition of negative numbers in 2s complement number will result a four bit number. Here we simply ignore the fourth bit.



### Fixed-point Numbers

### Floating-Point Numbers