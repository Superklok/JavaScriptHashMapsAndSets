# JavaScript Group Anagrams

## Challenge:

Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### 1<sup>st</sup> Example:

`Input: strs = ["eat","tea","tan","ate","nat","bat"]`
<br/>
`Output: [["bat"],["nat","tan"],["ate","eat","tea"]]`

### 2<sup>nd</sup> Example:

`Input: strs = [""]`
<br/>
`Output: [[""]]`

### 3<sup>rd</sup> Example:

`Input: strs = ["a"]`
<br/>
`Output: [["a"]]`

### Constraints:

`1 <= strs.length <= 10⁴`
<br/>
`0 <= strs[i].length <= 100`
<br/>
`strs[i]` consists of lowercase English letters.

## Solution:

`const groupAnagrams = (strs) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let map = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let str of strs) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let s = str.split('').sort().join('');`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(!map[s]) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map[s] = [];`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map[s].push(str);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return Object.values(map);`
<br/>
`};`
<br/>
<br/>