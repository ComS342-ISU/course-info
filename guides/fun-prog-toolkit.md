# Functional Programmer's Toolkit

One of the most important skills that a functional programmer needs to have is the ability to work with immutable collections. Scheme has one-size-fits-all collection called `list`. Other functional languages provide more of these (sets, maps, etc).

These collections are usually accompanied with the same set of operations that can be applied to them. Most of these work on flat collections, for the list:  
```
(list (list 1 2) (list 3 4))
```  
the operations will be applied on the elements `(1 2)` and `(3 4)` instead of `1` `2` `3` `4`

### flatten
```
;This function flattens a list of any arbitrarily high nesting level
> (flatten lst)

```  
Example:  
```
> (flatten '((1 2) (3 (4 (5)))))
'(1 2 3 4 5)
```  

You will find yourself using flatten most often before applying any of the functions featured below.


### map
```
> (map 1-arg-fun lst)
;This function applies the operation described by `1-arg-fun` on every element of the list
;and returns a new list containing the results of this operations.
```
```
> (map (lambda (x) (+ x 42)) '(1 2 3));this expression increments every element of the list by 42
'(43 44 45)                           ;;and returns a new list
```  
Map can also be applied to an `n` number of lists, but then we have to pass an `n` argument function.

```
> (map (lambda (x y) (+ x y)) '(1 2 3) '(4 5 6))
'(5 7 9)
;this does 1+4, 2+5, 6+3
```

### for-each
```
> (for-each 1-arg-fun lst)
```

This is similar to map, only that the results of the `1-arg-fun` are discarded and no new list is returned. We use this function when we only care about the side-effects of applying the `1-arg-fun` to every element.

```
> (for-each (lambda (x) (+ x 42)) '(1 2 3))
;it returns nothing

;but if we print, we can see that it works
> (for-each print '(1 2 3))
123
```
### filter
````
> (filter 1-arg-fun lst)
1-arg-fun must return a boolean.
```

This function retains all elements in the list for which the `1-arg-fun` returns `#t`.
```
> (filter odd? '(1 2 3))
'(1 3)
```  

Similarly, filter-not retains all elements for which the `1-arg-fun` returns `#f`

```
> (filter-not odd? '(1 2 3))
'(2)
```
### fold
```
> (foldl two-arg-fun identity-element lst)
```  
`fold-left` or in other languages called `reduce-left` iterates through the elements of the list and reduces them to one value single by iteratively applying the two-arg-fun to the `identity-element` and an element of the list; then proceeding with applying the result of the previous application and the next element.  

```
> (foldl + 0 '(1 2 3 4))
10

> (foldl cons '() '(1 2 3 4))
'(4 3 2 1)
```  
It is important to be attentive to the types of the `two-arg-fun`. In the above example `cons'` signature is: `(cons any-type? list?)`. As you can see the type of the zero-element has to be the same as the type of the second argument of the `two-arg-fun` (which is an accumulator for the final result). And the type of the elements in the list has to be the same as the
type of the first argument of the `two-arg-fun`.  

`foldl` can be applied to multiple lists at once. In that case, for `n` lists the number
of arguments of the function has to be `n + 1`.  
```
> (foldl + 0 '(1 2 3) '(4 5 6))
21
```  

Similarly, we have `foldr` which applies op from last element towards the first.
 ```
 > (foldr cons '() '(1 2 3 4))
'(1 2 3 4)
```

### andmap
```
> (andmap 1-arg-fun lst)
```

`andmap` is best used with `1-arg-funs` that return booleans, but it can accept other return types.

This function is most useful if we want to check if every element in the list holds a
certain property described by the `1-arg-fun`:
```
> (andmap odd? '(1 3 5))
#t
> (andmap odd? '(1 2 5))
#f
```  

Similarly, `ormap` returns `#t` if at least one element of the list has the property:  
```
> (ormap odd? '(1 2))
#t
```

### Final observations

Making use of these functions will:
- reduce the amount of code you have to write
- convey the intended functionality of your code more clearly because most people know how and when to use the above functions.
- when you write your own versions of the above functions potential bugs can arise from both the part of the code that iterates through the collection and the one that manipulates data. Using these functions leaves room for error only data manipulation part.

### TODO: More complex example