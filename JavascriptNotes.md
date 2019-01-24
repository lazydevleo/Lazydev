## Javascript 


**If... Else**

there is no `elseif` keyword in JS. so for example code below represents the if else if block, but in reality this is not how it might seem to work.

```
if (condition1)
   statement1
else if (condition2)
   statement2
else if (condition3)
   statement3
...
else
   statementN
```

so above code will evaluate to ( with right indentation )

```
if (condition1)
   statement1
else
   if (condition2)
      statement2
   else
      if (condition3)
...
```
