# Computer Science (Vets Who Code)
A repository covering the Computer Science topics I'm learning through the Vets Who Code program.

## Big O Notation

In the most simple terms, Big O Notation is a measure of how well an algorithm scales as the amount of data it is required to process increases. An algorithm is nothing more than a series of steps that need to be followed in order to solve a problem. Even though Computer Science algorithms can get pretty complex, you actually use algorithms in your every day life whether you realize it or not. Something as simple as following a recipe can be considered an algorithm. Think about it, you're following a sequence of steps and expecting a certain outcome, just like your computer does when you run a function you've coded. Now lets take a closer look at Big O Notation.

![alt tag](http://i.imgur.com/zEyBrXG.gif)

Let's say x^2 + x + 2 is your algorithm. (I know, that's not a very good algorithm but bear with me.) As X gets larger and larger, which part of the algorithm is going to have the biggest affect? Well, let's start with something small, like x = 10. If x = 10, your total will come out to be 112. We can see right away that the + 2 doesn't really contribute much, and even the x isn't really contributing much, since when x = 10, x^2 will equal 100 and x will equal 10. And what if x = 1000? Well your total will be 1,001,002. Now it's very evident that the + 2 does not matter at all, and even the x is irrelevant since in this case x^2 will be equal to 1,000,000. So we would say the algorithm x^2 + x + 2 has a Big O of O(N^2) - which reads order of N^2. This is obviously an overly simplistic way of looking at Big O, since you'll have to analyze code to figure out the Big O in a real world situation, but it's a good starting point to understand the basics. Below is a brief look at some of the most common cases of Big O: 
* O(1): takes the same amount of time to run regardless of how much data must be processed.
* O(N): the time it takes to run grows in direct proportion to the amount of data that must be processed. 
* O(N^2): the time it takes to run grows proportionally to the exponent(in this case 2).
* O(log N): the data that must be processed is decreased by roughly half each pass through the algorithm. This means that as the data inceases exponentially the time increases linearly, which makes algorithms that fall into this category very efficient. 


