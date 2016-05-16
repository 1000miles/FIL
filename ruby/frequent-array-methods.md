# Ruby
## Cheat Sheet – frequent Array Methods to look up

### (A-Z)

**.count, .size, .length**
```
[4, 8, 15, 16, 23, 42].count
=> 6
# count number of elements in the array & return

[4, 8, 15, 16, 23, 42].size
=> 6
# count the number of elements in the array & return

[4, 8, 15, 16, 23, 42].length
=> 6
# count the number of elements in the array & return
```

**.compact**
```
[1, 2, nil, 3, nil, 4, 5].compact
=> [1, 2, 3, 4, 5]
# return the array without nil

[1, 2, 3, [4, 5, nil], nil].compact
=> [1, 2, 3, [4, 5, nil]]
# return the array without nil on the first level
```

**.flatten**
```
[ 1, 2, [3, [4, 5] ] ].flatten
=> [1, 2, 3, 4, 5]

[ 1, 2, [3, [4, 5] ] ].flatten(1)
=> [1, 2, 3, [4, 5]]
```

**.index**
```
[4, 8, 15, 16, 23, 42].index(8)
=> 1
# return the index of the element from the array with the number 8
```

**.join**
```
[4, 8, 15, 16, 23, 42].join(", ")
=> "4, 8, 15, 16, 23, 42"
# pass in a separator (coma) after each element of the array
# remove the separator for the last element of the array & return
```

**.pack**
```
array = [8, 15, 16, 23, 42]
=> [8, 15, 16, 23, 42]
# assigns values of the array to the variable array from right to left

array.pack("ccc")
=> "\b\x0F\x10"
# returns packed string of the elements converted into appropriate binary sequences

array.pack("slq")
=> "\b\x00\x0F\x00\x00\x00\x10\x00\x00\x00\x00\x00\x00\x00"

p [177, 8978].pack("UU")
"±⌒"
=> "±⌒"

Learn more about pack [directives](http://ruby-doc.org/core-1.9.3/Array.html#method-i-pack).
```

**.pop**
```
array = [8, 15, 16, 23, 42]
=> [8, 15, 16, 23, 42]
# assigns values of the array to the variable array from right to left

array.pop(1)
[42]
=> [42]
# removes the last element (42) from the array

p array
[8, 15, 16, 23]
=> [8, 15, 16, 23]
# prints out the array without number 42

array.pop(2)
=> [16, 23]
# removes the last 2 elements from the array

p array
[8, 15]
=> [8, 15]
# prints out the array without numbers 16 & 23
```

**.push**
```
array = [8, 15, 16, 23, 42]
=> [8, 15, 16, 23, 42]
# assigns values of the array to the variable array from right to left

p array
[8, 15, 16, 23, 42]
=> [8, 15, 16, 23, 42]
# prints out array

array.push(33,78,25)
=> [8, 15, 16, 23, 42, 33, 78, 25]
# pushes and appends the numbers 33, 78, 25 to the array

```

**.slice**
```
[4, 8, 15, 16, 23, 42].slice(2)
=> 15
# slice & return element from array at index 2

[4, 8, 15, 16, 23, 42].slice(2..4)
=> [15, 16, 23]
# slice & return elements from array at index 2 to 4 (range)

array.slice(-2..-1).join("|")
# slice last 2 elements of the array and pass in a separator ("|") & return
```

**.shift**
```
array = [4, 8, 15, 16, 23, 42]
=> [4, 8, 15, 16, 23, 42]
# assigns values of the array to the variable array from right to left

p array.shift
4
=> 4
# removes the first element (4) from the array

p array
[8, 15, 16, 23, 42]
=> [8, 15, 16, 23, 42]
# prints out array without number 4

p array.shift(2)
[8, 15]
=> [8, 15]
# removes first 2 elements (8,15) from the array

p array
[16, 23, 42]
=> [16, 23, 42]
# prints out array without number 8 & 15
```

**.unshift**
```
array = [16, 23, 42]
=> [16, 23, 42]
# assigns values of the array to the variable array from right to left

p array
[16, 23, 42]
=> [16, 23, 42]
# print out current array

array.unshift(17)
=> [17, 16, 23, 42]
# push number 17 to the first position of the array
# change the previous index order

array.unshift(33..36)
=> [33..36, 17, 16, 23, 42]
# push the range from 33 to 36 to the first position of the array
# change the previous index order => 0 become 1, 1 becomes 2, etc.

p array
[33..36, 17, 16, 23, 42]
=> [33..36, 17, 16, 23, 42]
# print out array

array.unshift(77,88)
=> [77, 88, 33..36, 17, 16, 23, 42]
# push the numbers 77 & 88 to the first two positions of the array
# change the previous index order => 0 become 1, 1 becomes 2, etc.
```

**.zip**
```
[4, 8, 15, 16, 23, 42].zip
=> [[4], [8], [15], [16], [23], [42]]
# put all elements into a separate array within the array & return

[4, 8, 15, 16, 23, 42].zip([42, 23, 16, 15, 8])
=> [[4, 42], [8, 23], [15, 16], [16, 15], [23, 8], [42, nil]]
# return all elements of the array & put each element into a separate array
# pass into each element of the array each element in the parenthesis
# if an element doesn't exist, assign the value nil to it & return
```
