# JavaScript Distribute Candies

## Challenge:

Trev has `n` candies, where the `iᵗʰ` candy is of type `candyType[i]`. Trev noticed that he started to gain weight, so he visited a doctor.

The doctor advised Trev to only eat `n / 2` of the candies he has (`n` is always even). Trev likes his candies very much, and he wants to eat the maximum number of different types of candies while still following the doctor's advice.

Given the integer array `candyType` of length `n`, return the maximum number of different types of candies he can eat if he only eats `n / 2` of them.

### 1<sup>st</sup> Example:

`Input: candyType = [1,1,2,2,3,3]`
<br/>
`Output: 3`
<br/>
`Explanation: Trev can only eat 6 / 2 = 3 candies. Since there are only 3 types, he can eat one of each type.`

### 2<sup>nd</sup> Example:

`Input: candyType = [1,1,2,3]`
<br/>
`Output: 2`
<br/>
`Explanation: Trev can only eat 4 / 2 = 2 candies. Whether he eats types [1,2], [1,3], or [2,3], he still can only eat 2 different types.`

### 3<sup>rd</sup> Example:

`Input: candyType = [6,6,6,6]`
<br/>
`Output: 1`
<br/>
`Explanation: Trev can only eat 4 / 2 = 2 candies. Even though he can eat 2 candies, he only has 1 type.`

### Constraints:

`n == candyType.length`
<br/>
`2 <= n <= 10⁴`
<br/>
`n` is even.
<br/>
`-10⁵ <= candyType[i] <= 10⁵`

## Solution:

`const distributeCandies = (candyType) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const hashMap = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let output = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i = 0; i < candyType.length; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(!hashMap[candyType[i]]) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`output++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`hashMap[candyType[i]] = i + 1;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(output === Math.floor(candyType.length/2)) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return output;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return output;`
<br/>
`};`
<br/>
<br/>