# leetcode_2020
One leetcode a day keeps unemployment away. 


## Python snippets 

### Count characters in a string

```python
import collections 
print collections.Counter(['a', 'b', 'c', 'a', 'b', 'b']) 
--> {a: 2, b: 3, c: 1} 
```

### Check if there is duplicate characters in string
```python
if len(set(word)) < len(word):
   return True 
````

### Sort dictionary by value 
```python
import collections
sorted_dict = {k: d[k] for k in sorted(d, key=d.get, reverse=True)} 
```

