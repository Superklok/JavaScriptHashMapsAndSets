# JavaScript Groups of Special-Equivalent Strings

## Challenge:

You are given an array of strings of the same length `words`.

In one move, you can swap any two even indexed characters or any two odd indexed characters of a string `words[i]`.

Two strings `words[i]` and `words[j]` are special-equivalent if after any number of moves, `words[i] == words[j]`.

For example, `words[i] = "zzxy"` and `words[j] = "xyzz"` are special-equivalent because we may make the moves `"zzxy" -> "xzzy" -> "xyzz"`.

A group of special-equivalent strings from `words` is a non-empty subset of words such that:
<br/>
Every pair of strings in the group are special equivalent.
<br/>
The group is the largest size possible (i.e., there is not a string `words[i]` not in the group such that `words[i]` is special-equivalent to every string in the group).

Return the number of groups of special-equivalent strings from `words`.

### 1<sup>st</sup> Example:

`Input: words = ["abcd","cdab","cbad","xyzz","zzxy","zzyx"]`
<br/>
`Output: 3`
<br/>
`Explanation: One group is ["abcd", "cdab", "cbad"], since they are all pairwise special equivalent, and none of the other strings is all pairwise special equivalent to these.`
<br/>
`The other two groups are ["xyzz", "zzxy"] and ["zzyx"].`
<br/>
`Note that in particular, "zzxy" is not special equivalent to "zzyx".`

### 2<sup>nd</sup> Example:

`Input: words = ["abc","acb","bac","bca","cab","cba"]`
<br/>
`Output: 3`

### Constraints:

`1 <= words.length <= 1000`
<br/>
`1 <= words[i].length <= 20`
<br/>
`words[i]` consist of lowercase English letters.
<br/>
All the strings are of the same length.

## Solution:

`const numSpecialEquivGroups = (words) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const transform = (word) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const odd  = [],`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`even = [];`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let index = 0; index < word.length; index++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const str = word[index];`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`index & 1 ? odd.push(str) : even.push(str);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return \`${odd.sort()}${even.sort()}\`;
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return words.reduce((set, word) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return set.add(transform(word));`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}, new Set()).size;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've defined a function called `numSpecialEquivGroups` that takes in an array of words as an argument and returns the number of groups of words that have the same special equivalence.
<br/>

Inside the function, there is a helper function called `transform`. This function takes in a word and splits it into two arrays: one for the odd-indexed characters and one for the even-indexed characters. It then sorts both arrays and concatenates them into a single string.
<br/>

The main function, `numSpecialEquivGroups`, uses the `reduce` method on the input array of words. It applies the `transform` function to each word and adds the resulting string to a new `Set` object.
<br/>

Finally, the function returns the size of the `Set` object, which represents the number of unique special equivalence groups in the input array.
<br/>

In summary, the "numSpecialEquivGroups" function groups words based on their special equivalence and returns the count of unique groups. The special equivalence is determined by splitting the words into odd-indexed and even-indexed characters, sorting them, and concatenating them into a single string.
<br/>
<br/>