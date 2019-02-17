## Starting with Elixir 

Using HomeBrew , installed the latest version of Elixir. 


### Learning the Language

*= is a match operator in Elixir*

a = 1 is a success if LHS can be matched to RHS

```
	iex>​ a = 1  // left hand side , variable value is changed. 
​ 	1
​ 	​iex>​ 1 = a  // here RHS is replaced with value, meaning a is replaced with 1.
​ 	1
​ 	​iex>​ 2 = a  // here a is replaced with 1 and now this becomes equal to 2 = 1 , and no match found error happens. 
```

**Complex Matches**

```
iex>​ list = [1, 2, 3]
​ 	[1, 2, 3]
​ 	​iex>​ [a, b, c ] = list
​ 	[1, 2, 3]
​ 	​iex>​ a
​ 	1
​ 	​iex>​ b
​ 	2
​ 	​iex>​ c
​ 	3

	​iex>​ list = [1, 2, [ 3, 4, 5 ] ]
	​ 	[1, 2, [3, 4, 5]]
	​ iex>​ [a, b, c ] = list
	​ 	[1, 2, [3, 4, 5]]
	​iex>​ c
	​ 	[3, 4, 5]
	
	[1, _, _] = [1, ​"​​cat"​, ​"​​dog"​]. // wildcard entry , 'underscore' will accept any value here and discards immediately.
	

```

**Variable Bound Once**

```
[a, a] = [1, 1] // a=1 this will match.
[b, b] = [1, 2] // this will not match. as variable will only match once.

it can bound to new value on subsequent match.

```


**Pin Operator**

if you want the variable to retain the previously binded value, we can use ^ symbol. 

```
^a = 1
```


### Immutability

- No Side effects
- Making concurrency less frighting.
- Faster Garbage collection.  As app is split as proceses. Heap is per Process. If Process exits before the heap is full , no garbage collection is required as the data is cleaned up.

```

​iex>​ list1 = [ 3, 2, 1 ]
​ 	[3, 2, 1]
​ iex>​ list2 = [ 4 | list1 ] // list 1 is re-used as we know list1 will not change in Elixir.
​ 	[4, 3, 2, 1]
```

Now we know what is immutability, data does not change, so we can always expect name will always hold the same value. If we ever change it, it will be returning new value but the orginal value will remain the same. 

```
iex(19)> name = "elixir"
"elixir"
iex(20)> cap_name = String.capitalize name
"Elixir"
iex(21)> name
"elixir"
iex(22)> cap_name
"Elixir"
iex(23)>
```




In Elixir, we always transform the data in place. we never modify it. 


### Built-In Types

**Value Types**

- numbers  - there is no fixed limit. Decimal numbers may contain underscore.
- names ,Atoms - constant, its name is its value. specified by a leading colon (:)
	```
	​:fred​  ​:is_binary?​  ​:var@2​  ​:<>​  ​:===​  ​:"func/3"​
	​ 	​:"long john silver"​  ​:эликсир​   ​:mötley_crüe​
	```
- ranges  - represented as start..end, where start and end are integers.
- regular expressions. - ~r{regexp} or ~r{regexp}opts

opts are mentioned below. 



```
f	Force the pattern to start to match on the first line of a multiline string.
i	Make matches case insensitive.
m	
If the string to be matched contains multiple lines, ^ and $ match the start and end of these lines. \A and \z continue to match the beginning or end of the string.

s	
Allow . to match any newline characters.

U	
Normally modifiers like * and + are greedy, matching as much as possible. The U modifier makes them ungreedy, matching as little as possible.

u	Enable unicode-specific patterns like \p.
x	
Enable extended mode—ignore whitespace and comments (# to end of line).
```

**System Types**

- PID - Refers to local/remote process. new PID is created when you spawn a process.
-  PORT - Refers to external app/resource you will read or write. 



### Collections


- Tuples 
	- *ordered collection of values* 
	```
	{:ok, "something"} 
	```

- Lists

	- *they are not arrays, they are linked data structures. they are not stored contiguously in memory. They are like linkedlist.*

	- *easy traversal, but you can get the nth random element.*

	- *as it is immutable. to remove head, return the tail reference/pointer, its performant*

	- 	```
		[1,2,3] [1,[1,2,3]]
		```
		
		**Operations on List**
		
		
		```
		​iex>​  [ 1, 2, 3 ] ++ [ 4, 5, 6 ]      ​# concatenation​
		​ 	[1, 2, 3, 4, 5, 6]
		
		
		​ iex>​ [1, 2, 3, 4] -- [2, 4]           ​# difference​
		​ 	[1, 3]
		
		
		​ iex>​ 1 ​in​ [1,2,3,4]                   ​# membership​
		​ 	true
		
		
		​ iex>​ ​"​​wombat"​ ​in​ [1, 2, 3, 4]
		​ 	false
		```

		we can ignore the [] when it is a ``` [name: "Dave",city: "Dallas"]``` , Elixir will convert this to list of tuples ```[{:name,"Dave"},{:city,"Dallas"}]```.




- Maps


	 Represented as 
	 ```
	 %{key=>value,key=>value}
	 ```
	
	  	
		
		
	 
