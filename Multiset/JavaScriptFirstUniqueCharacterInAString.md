# JavaScript First Unique Character In A String

## Challenge:

Given a string `s`, find the first non-repeating character in it and return its index. If it does not exist, return `-1`.

### 1<sup>st</sup> Example:

`Input: s = "super"`
<br/>
`Output: 0`

### 2<sup>nd</sup> Example:

`Input: s = "supsuperklok"`
<br/>
`Output: 6`

### 3<sup>rd</sup> Example:

`Input: s = "aabb"`
<br/>
`Output: -1`

### Constraints:

`1 <= s.length <= 10⁵`
<br/>
`s` consists of only lowercase English letters.

## Solution:

`const firstUniqChar = (s) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const map = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let char of s) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map[char] ? map[char]++ : map[char] = 1;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let i = 0; i < s.length; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (map[s[i]] === 1) return i;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return -1;`
<br/>
`};`
<br/>
<br/>