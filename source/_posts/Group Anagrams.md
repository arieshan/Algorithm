---
title: Group Anagrams
---

### Problem:
Given an array of strings, group anagrams together.

```
For example, given: ["eat", "tea", "tan", "ate", "nat", "bat"], 
Return:

[
  ["ate", "eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```
Note: All inputs will be in lower-case.

***

### Analysis:
Sort each string and put it into a hashmap. The Time Complexity is O(m*nlogn)

1. collections.Counter creates a counter object. A counter object is like a specific kind of dictionary where it is build for counting (objects that hashes to same value)
2. tuple(sorted(s)) is used here so that anagrams will be hashed to the same value. tuple is used because sorted returns a list which cannot be hashed but tuples can be hashed
3. filter: selects some elements of the list based on given function (first argument - a lambda function is given here)
4. lambda function defined here returns True if number of anagrams of that elements is greater than 1

***

### Implementation:
```
   def anagrams(self, strs):
        count = collections.Counter([tuple(sorted(s)) for s in strs])
        return filter(lambda x: count[tuple(sorted(x))]>1, strs)
```

Or

1. collection.defaultdict is used instead of Counter. It is almost same as dict but you can set default value (the value when item is not found in the dictionary)
2. list comprehension is used in the return statement in order to select anagrams which have more than 1 word and also to flatten the d.values() which is list of lists

```
def anagrams(self, strs):
       d = collections.defaultdict(list)
       for s in strs:
           d[tuple(sorted(s))].append(s)  
       return [a for agram_group in d.values() if len(agram_group)>1 for a in agram_group]

```
