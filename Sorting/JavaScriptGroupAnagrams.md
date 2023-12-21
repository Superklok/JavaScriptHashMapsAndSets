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

## Explanation:

I've coded a function called `groupAnagrams` that takes in an array of strings as input. Its purpose is to group the strings that are anagrams of each other and return an array of arrays, where each inner array contains the grouped anagrams.
<br/>

Inside the function, an empty object called `map` is declared. This object will be used to store the anagram groups.
<br/>

The function then iterates through each string `str` in the input array `strs` using a for...of loop.
<br/>

Within the loop, a new variable `s` is created. It represents the sorted version of the current string `str`. This is achieved by splitting the string into an array of characters, sorting the array, and then joining the sorted array back into a string.
<br/>

It checks to see if `s` is already a key in the `map` object using an if statement. If it is not, `s` is added as a key in the `map` object, and its value is set as an empty array.
<br/>

The current string `str` is then pushed into the array value of `map[s]`, which represents the anagram group.
<br/>

After the loop finishes, the function uses `Object.values(map)` to extract all the values (anagram groups) from the `map` object and returns them as an array.
<br/>

In summary, the `groupAnagrams` function takes an array of strings, groups the anagrams together, and returns an array of arrays representing the grouped anagrams.
<br/>
<br/>