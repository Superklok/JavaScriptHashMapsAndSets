# JavaScript Design HashMap

## Challenge:

Design a HashMap without using any built-in hash table libraries.

Implement the `MyHashMap` class:

`MyHashMap()` initializes the object with an empty map.
<br/>
`void put(int key, int value)` inserts a `(key, value)` pair into the HashMap. If the `key` already exists in the map, update the corresponding `value`.
<br/>
`int get(int key)` returns the `value` to which the specified `key` is mapped, or `-1` if this map contains no mapping for the `key`.
<br/>
`void remove(key)` removes the `key` and its corresponding `value` if the map contains the mapping for the `key`.

### 1<sup>st</sup> Example:

`Input: ["MyHashMap", "put", "put", "get", "get", "put", "get", "remove", "get"]`
<br/>
`[[], [1, 1], [2, 2], [1], [3], [2, 1], [2], [2], [2]]`
<br/>
`Output: [null, null, null, 1, -1, null, 1, null, -1]`
<br/>
`Explanation: MyHashMap myHashMap = new MyHashMap();`
<br/>
`myHashMap.put(1, 1); // The map is now [[1,1]]`
<br/>
`myHashMap.put(2, 2); // The map is now [[1,1], [2,2]]`
<br/>
`myHashMap.get(1);    // return 1, The map is now [[1,1], [2,2]]`
<br/>
`myHashMap.get(3);    // return -1 (i.e., not found), The map is now [[1,1], [2,2]]`
<br/>
`myHashMap.put(2, 1); // The map is now [[1,1], [2,1]] (i.e., update the existing value)`
<br/>
`myHashMap.get(2);    // return 1, The map is now [[1,1], [2,1]]`
<br/>
`myHashMap.remove(2); // remove the mapping for 2, The map is now [[1,1]]`
<br/>
`myHashMap.get(2);    // return -1 (i.e., not found), The map is now [[1,1]]`

### Constraints:

`0 <= key, value <= 10⁶`
<br/>
At most `10⁴` calls will be made to `put`, `get`, and `remove`.

## Solution:

`let MyHashMap = function() {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`this.map = {};`
<br/>
`};`
<br/>
<br/>
`MyHashMap.prototype.put = function(key, value) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`this.map[key] = value;`
<br/>
`};`
<br/>
<br/>
`MyHashMap.prototype.get = function(key) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return this.map[key] != undefined ? this.map[key] : -1;`
<br/>
`};`
<br/>
<br/>
`MyHashMap.prototype.remove = function(key) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`delete this.map[key];`
<br/>
`};`
<br/>
<br/>