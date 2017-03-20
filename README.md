# Computer Science (Vets Who Code)
A repository covering the Computer Science topics I'm learning through the Vets Who Code program.

## Big O Notation

In the most simple terms, Big O Notation is a measure of how well an algorithm scales as the amount of data it is required to process increases. An algorithm is nothing more than a series of steps that need to be followed in order to solve a problem. Even though Computer Science algorithms can get pretty complex, you actually use algorithms in your every day life whether you realize it or not. Something as simple as following a recipe can be considered an algorithm. Think about it, you're following a sequence of steps and expecting a certain outcome, just like your computer does when you run a function you've coded. Now lets take a closer look at Big O Notation.

![Big O](http://i.imgur.com/zEyBrXG.gif)

When figuring out the Big O of an algorithm you want to figure out which portion of the algorithm is going to have the biggest affect on the runtime of your program. Let's say x^2 + x + 2 is your algorithm. (I know, that's not a very good algorithm but bear with me.) As X gets larger and larger, which part of the algorithm is going to have the biggest affect? Well, let's start with something small, like x = 10. If x = 10, your total will come out to be 112. We can see right away that the + 2 doesn't really contribute much, and even the x isn't really contributing much, since when x = 10, x^2 will equal 100 and x will equal 10. And what if x = 1000? Well your total will be 1,001,002. Now it's very evident that the + 2 does not matter at all, and even the x is irrelevant since in this case x^2 will be equal to 1,000,000. So we would say the algorithm x^2 + x + 2 has a Big O of O(N^2) - which reads order of N^2. This is obviously an overly simplistic way of looking at Big O, since you'll have to analyze code to figure out the Big O in a real world situation, but it's a good starting point to understand the basics. Below is a brief look at some of the most common cases of Big O: 
* O(1): takes the same amount of time to run regardless of how much data must be processed.
* O(N): the time it takes to run grows in direct proportion to the amount of data that must be processed. 
* O(N^2): the time it takes to run grows proportionally to the exponent(in this case 2).
* O(log N): the data that must be processed is decreased by roughly half each pass through the algorithm. This means that as the data increases exponentially the time increases linearly, which makes algorithms that fall into this category very efficient. 

## Recursion


![Recursion](http://i.imgur.com/yJ0XuI6.jpg)

I think the popular quote "to understand recursion, you must first understand recursion" pretty well sums up understanding recursion. Recursion is essentially when a function calls itself...until it doesn't anymore. I think the best way to explain it is using a small snippet of code. A very popular example of using recursion is for finding the factorial of a number. If you need a quick refresher, a factorial of a number is the product of that number and all of the numbers below it. So if you wanted to find the factorial of 4, you would multiply 4 * 3 * 2 * 1. Lets take a look at how that would look in a simple factorial function:
```javascript
function factorial(n) {
  if (n === 1) {
    return 1
  }
  else {
    return n * factorial(n-1)
  }
}
```
Every recursive function must have a base case. A base case is the condition which tells the function when it should stop calling itself. Without a base case, your function would continue to call itself until you either run out of memory or kill your program. In the case of the factorial function the line ```if (n === 1)``` is the base case. This is basically saying, once n, the number you pass into the function, reaches 1, exit the function. Say for instance you pass 3 into the function. The first pass through it'll ask, is 3 equal to 1? The answer is clearly no, so the function moves to and executes the code following the else statement, which is where recursion comes in. Here the line ```return n * factorial(n-1)``` is calling the factorial function inside of the factorial function. Using 3, this line essentially says multiply 3 by factorial(3-1). But here's the catch, your function doesn't yet know what factorial(3-1) is, which is where the stack comes in. (You can read up on a stack here if you need to - http://www.i-programmer.info/programming/javascript/1674-javascript-data-structures-stacks-queues-and-deques.html)

Essentially your function will "remember" that it wants to multiply 3 by whatever factorial(3-1) is. So it places this on the stack, and then calls the factorial function again with 3-1 as the input. Here it goes through the same process again, first it'll ask if 2 is equal to 1, since the answer is no it'll execute the code following the else statement. And now onto the stack goes 2 * factorial(2-1). So on our stack we now have 3 * factorial(3-1), and 2 * factorial(2-1). At this point the factorial function will be called one final time, with the input 2-1. This time once the function reaches the base case and it asks is 1 equal to 1, the answer is yes and the ```return 1``` will execute. What happens now is the information that the stack has been "waiting" for is passed back through the stack. Remember our stack currently has 3 * factorial(3-1) and 2 * factorial(2-1). Factorial(2-1) knows that it is 1, thanks to the base case, so it can pass that information back down the stack. So now, 2 * factorial(2-1), knows that it is 2 * 1. 3 * factorial(3-1) is still waiting, but now our function knows that factorial(3-1) is 2. So here we get 3 * 2 = 6, and that is what will be returned as the answer. 

## Sorting Algorithms

![Sorting](http://i.imgur.com/sSzvYe3.gif)

### Bubble Sort
A bubble sort will compare a pair of adjacent elements in an array, see which one is larger, and then swap the values so they are in sorted order if it is necessary. Let's say you have the array [12, 5, 9, 2, 1]. On the first pass through the array, the bubble sort will compare the 12 and 5. It'll ask, is 12 larger than 5? The answer is yes, so the 12 and the 5 will swap positions and our array will now be [5, 12, 9, 2, 1]. Next the 12 and the 9 will be compared, and it'll ask if 12 is larger than 9. The answer again is yes, so now our array looks like [5, 9, 12, 2, 1]. This process will continue until the algorithm finds a value that 12 is not greater than, or it reaches the end of the array. Since 12 is the largest value in this array, it will end up in the last position. 

After the first pass through, the array will be [5, 9, 2, 1, 12], and at this point the algorithm will begin again by comparing the 5 and the 9. Here since 5 is less than 9 nothing gets swapped, and the algorithm moves on to comparing the 9 and the 2. This process will continue until the array is completely sorted. 

### Insertion Sort
An insertion sort will compare the current value it is looking to sort to the array, and insert it into the portion of the array it knows is already sorted. Let's say we have the same array as used above, [5, 12, 9, 2, 1]. When the algorithm first looks at the array it sees that there are no values preceding 5, so it moves on to the value 12. It compares the value 12 to the portion of the array it knows is sorted, in this case only 5, and asks is 12 greater than 5? Since the answer is yes, no swap will occur, and the algorithm now knows that the array is sorted from index 0 to 1, containing the values 5 and 12. At this point it will move on the value 9, and it will compare the value to each value in the sorted range. 

Since 9 is less than 12, and 12 is inside the sorted portion of the array, the algorithm now knows it needs to insert 9 into the sorted range. In order to find the correct place to insert the current value (9), the current value has to be compared to each value already in the sorted range until the correct insertion point is found. Once the correct insertion point is found, our algorithm knows that the array is sorted from index 0 to 2, containing the values 5, 9, and 12. It will then move on to the value 2 in the array, and the process will continue until the array is completely sorted. 

### Merge Sort
A merge sort algorithm uses the concept of divide and conquer. Each pass will divide the array into equal halves, and this will contine until the array can no longer be divided. Then the algorithm will reassamble the array and sort it as it is being reassambled. For example, let's say we have the array [5, 12, 9, 3, 2, 1, 6, 7]. On the first pass through, the algorithm will break the array into two arrays, [5, 12, 9, 3] and [2, 1, 6, 7]. Then these arrays will further be divided, giving us [5, 12] [9, 3], [2, 1] [6, 7]. This process will occur one more time, until we have eight arrays containing one value each: [5] [12], [9] [3], [2] [1], [6] [7]. Notice the grouping (notated by commas) has not changed. 

When reassembling the array, the algorithm will compare the values that were grouped before being split into single arrays. For instance the 5 and the 12 will be compared, and the algorithm will ask is 5 greater than 12? The answer is no, so it combines the two values back into the array [5, 12], and it knows that this array is in sorted order. It does this for each pair of values, until we end up with 4 sorted arrays: [5, 12] [3, 9], [1, 2] [6, 7]. These arrays of two values will then merge back into two sorted arrays of four values, giving us [3, 5, 9, 12] and [1, 2, 6, 7]. Finally, the last merge will combine the two sorted arrays into one sorted array, ending with [1, 2, 3, 5, 6, 7, 9, 12].
