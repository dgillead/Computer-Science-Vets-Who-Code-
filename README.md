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
