# JavaScript Longest Substring Without Repeating Characters

## Challenge:

Given a string `s`, find the length of the longest substring without repeating characters.

### 1<sup>st</sup> Example:

`Input: s = "abcabcbb"`
<br/>
`Output: 3`
<br/>
`Explanation: The answer is "abc", with the length of 3.`

### 2<sup>nd</sup> Example:

`Input: s = "bbbbb"`
<br/>
`Output: 1`
<br/>
`Explanation: The answer is "b", with the length of 1.`

### 3<sup>rd</sup> Example:

`Input: s = "pwwkew"`
<br/>
`Output: 3`
<br/>
`Explanation: The answer is "wke", with the length of 3.`
<br/>
`Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.`

### Constraints:

`0 <= s.length <= 5 * 10⁴`
<br/>
`s` consists of English letters, digits, symbols and spaces.

## Solution:

`const lengthOfLongestSubstring = (s) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let set     = new Set(),`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`left    = 0,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`maxSize = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(s.length === 0) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return 0;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(s.length === 1) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return 1;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i = 0; i < s.length; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`while(set.has(s[i])) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`set.delete(s[left]);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`left++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`set.add(s[i]);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`maxSize = Math.max(maxSize, i - left + 1);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return maxSize;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've defined a function called `lengthOfLongestSubstring` that calculates the length of the longest substring without repeating characters in a given string.
<br/>

Inside the function, a set called `set` is initialized to store unique characters, and two variables, `left` and `maxSize`, are initialized to keep track of the left index of the current substring and the maximum length of the substring, respectively.
<br/>

The function first checks if the length of the input string is `0` or `1`. If it is, it immediately returns `0` or `1` respectively since there can be no repeated characters in such cases.
<br/>

Next, the function enters a loop that iterates through each character of the input string.
<br/>

Inside the loop, there is another loop that runs as long as the set `set` already contains the current character `s[i]`. This inner loop is used to remove characters from the set until there are no repeating characters in the current substring.
<br/>

In each iteration of the inner loop, it deletes the leftmost character of the current substring from the set using `set.delete(s[left])` and increments the `left` index to move to the next character.
<br/>

Once there are no repeating characters in the current substring, it adds the current character `s[i]` to the set using `set.add(s[i])`.
<br/>

After adding the character to the set, it calculates the length of the current substring by subtracting the left index from the current index and adding 1 (`i - left + 1`).
<br/>

It then updates the `maxSize` variable with the maximum value between the current `maxSize` and the length of the current substring using `Math.max(maxSize, i - left + 1)`.
<br/>

After iterating through all the characters of the input string, the function returns the `maxSize`, which represents the length of the longest substring without repeating characters.
<br/>

In summary, the `lengthOfLongestSubstring` function finds the length of the longest substring without repeating characters in a given string by using a set to keep track of unique characters and two pointers to track the current substring.
<br/>
<br/>