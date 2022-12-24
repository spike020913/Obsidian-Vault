Summary:![[Pasted image 20221120230849.png]]


```
The map::upper_bound() is a built-in function in C++ STL which returns an iterator pointing to the immediate next element just greater than k. 

If the key passed in the parameter exceeds the maximum key in the container, then the iterator returned points to the number of elements in the map container as key and element=0
```

	 ![[Pasted image 20221120230332.png]]

```
The map::lower_bound() returns an iterator pointing to the key in the map container which is equivalent to k passed in the parameter.

If k is not present in the map container, the function returns an iterator pointing to the immediate next element which is just greater than k. 

If the key passed in the parameter exceeds the maximum key in the container, then the returned iterator points to the number of elements in the map as key and element= any element.
```

![[Pasted image 20221120230542.png]]