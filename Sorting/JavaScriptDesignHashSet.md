# JavaScript Design HashSet

## Challenge:

Design a HashSet without using any built-in hash table libraries.

Implement `MyHashSet` class:

`void add(key)` Inserts the value `key` into the HashSet.
<br/>
`bool contains(key)` Returns whether the value `key` exists in the HashSet or not.
<br/>
`void remove(key)` Removes the value `key` in the HashSet. If `key` does not exist in the HashSet, do nothing.

### 1<sup>st</sup> Example:

`Input: ["MyHashSet", "add", "add", "contains", "contains", "add", "contains", "remove", "contains"]`
<br/>
`[[], [1], [2], [1], [3], [2], [2], [2], [2]]`
<br/>
`Output: MyHashSet myHashSet = new MyHashSet();`
<br/>
`myHashSet.add(1);      // set = [1]`
<br/>
`myHashSet.add(2);      // set = [1, 2]`
<br/>
`myHashSet.contains(1); // return True`
<br/>
`myHashSet.contains(3); // return False, (not found)`
<br/>
`myHashSet.add(2);      // set = [1, 2]`
<br/>
`myHashSet.contains(2); // return True`
<br/>
`myHashSet.remove(2);   // set = [1]`
<br/>
`myHashSet.contains(2); // return False, (already removed)`

### Constraints:

`0 <= key <= 10⁶`
<br/>
At most `10⁴` calls will be made to `add`, `remove`, and `contains`.

## Solution:

`let MyHashSet = function() {};`
<br/>
<br/>
`MyHashSet.prototype.add = function(key) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`this[key] = null;`
<br/>
`};`
<br/>
<br/>
`MyHashSet.prototype.remove = function(key) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`delete this[key];`
<br/>
`};`
<br/>
<br/>
`MyHashSet.prototype.contains = function(key) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return this.hasOwnProperty(key);`
<br/>
`};`
<br/>
<br/>