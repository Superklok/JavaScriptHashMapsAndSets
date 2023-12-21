# JavaScript Happy Number

## Challenge:

Write an algorithm to determine if a number `n` is happy.

A happy number is a number defined by the following process:
<br/>
Starting with any positive integer, replace the number by the sum of the squares of its digits.
<br/>
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
<br/>
Those numbers for which this process ends in 1 are happy.

Return `true` if `n` is a happy number, and `false` if not.

### 1<sup>st</sup> Example:

`Input: n = 19`
<br/>
`Output: true`
<br/>
`Explanation: 12 + 92 = 82`
<br/>
`82 + 22 = 68`
<br/>
`62 + 82 = 100`
<br/>
`12 + 02 + 02 = 1`

### 2<sup>nd</sup> Example:

`Input: n = 2`
<br/>
`Output: false`

### Constraints:

`1 <= n <= 2³¹ - 1`

## Solution:

`const isHappy = (n) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const hashMap = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const recursion = (number) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const array = number.toString().split('');`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let newNumber = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i = 0; i < array.length; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`newNumber += Number(array[i])**2;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(newNumber === 1) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return true;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(hashMap[newNumber]) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return false;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`hashMap[newNumber] = newNumber;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return recursion(newNumber);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return recursion(n);`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've written a function called `isHappy` that takes in a number `n` as a parameter. Its purpose is to determine if the number is a `happy number` using recursion.
<br/>

Inside the function, an empty object called `hashMap` is created to keep track of numbers encountered during the recursion.
<br/>

The function defines a nested function called `recursion` that takes in a number as a parameter.
<br/>

Within the `recursion` function, the number is converted to a string and split into an array of individual digits.
<br/>

A variable called `newNumber` is initialized to `0`.
<br/>

A for loop iterates through each digit in the array. For each digit, it is squared using the exponentiation operator (**), and the result is added to `newNumber`.
<br/>

After the loop, there are three conditional statements:
<br/>

If `newNumber` is equal to `1`, it means that the number is a happy number, so the function returns true.
<br/>

If `newNumber` already exists as a key in the `hashMap` object, it means that the recursion has entered a cycle, and the number is not a happy number. In this case, the function returns false.
<br/>

If neither of the above conditions are met, the `newNumber` is added as a key to the `hashMap` object, and the recursion continues by calling the `recursion` function with `newNumber` as the argument.
<br/>

Finally, the function returns the result of the initial call to the `recursion` function with the input number `n`.
<br/>

In summary, the `isHappy` function determines if a number is a `happy number` by recursively calculating the sum of the squares of its digits. It uses a hashMap object to keep track of encountered numbers and returns true if the recursion reaches `1`, or false if it enters a cycle.
<br/>
<br/>