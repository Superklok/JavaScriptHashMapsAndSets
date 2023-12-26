# JavaScript Group Anagrams
<br/>

## Challenge
Given an array of strings `strs`, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
<br/>
<br/>

### 1<sup>st</sup> Example

```JavaScript
Input: strs = ['eat','tea','tan','ate','nat','bat']
Output: [['bat'],['nat','tan'],['ate','eat','tea']]
```

### 2<sup>nd</sup> Example

```JavaScript
Input: strs = ['']
Output: [['']]
```

### 3<sup>rd</sup> Example

```JavaScript
Input: strs = ['a']
Output: [['a']]
```

<br/>

### Constraints

- `1 <= strs.length <= 10⁴`
- `0 <= strs[i].length <= 100`
- `strs[i]` consists of lowercase English letters.

<br/>

## Solution

```JavaScript
const groupAnagrams = (strs) => {
    let map = {};

    for(let str of strs) {
        let s = str.split('').sort().join('');

        if(!map[s]) {
            map[s] = [];
        }

        map[s].push(str);
    }

    return Object.values(map);
};
```

<br/>

## Explanation

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
<br/>
<br/>

### :next_track_button: [Next (Longest Substring Without Repeating Characters)][Next]
<br/>

### :previous_track_button: [Previous (Find Bottom Left Tree Value)][Previous]
<br/>

### :play_or_pause_button: [More HashMap & HashSet Challenges][More]
<br/>

### :eject_button: [Return to Course Outline][Return]
<br/>

[Next]: https://github.com/Superklok/JavaScriptHashMapsAndSets/blob/main/Sorting/JavaScriptLongestSubstringWithoutRepeatingCharacters.md
[Previous]: https://github.com/Superklok/JavaScriptTrees/blob/main/JavaScriptFindBottomLeftTreeValue.md
[More]: https://github.com/Superklok/JavaScriptHashMapsAndSets
[Return]: https://github.com/Superklok/LearnJavaScript