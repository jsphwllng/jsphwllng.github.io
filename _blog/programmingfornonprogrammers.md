---
layout: default
title: programming for non-programmers
description: "using fizzbuzz to help non-programmers get their programming hands dirty"
order: 8
---

I was fortunate enough to run an [unconference](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4310607/#:~:text=Unlike%20traditional%20conferences%2C%20an%20unconference,even%20the%20time%20and%20venues.) at my company's recent offsite titled "programming for non-programmers". When deciding what tasks and challenges we could do as a group I settled on fizzbuzz. [Fizzbuzz](https://en.wikipedia.org/wiki/Fizz_buzz#:~:text=Fizz%20buzz%20is%20a%20group,with%20the%20word%20%22fizzbuzz%22.) is a fairly simple programming challenge often presented to junior engineers. I will paste my solution below and then dive into why I think this is the perfect fit for non-programmers to get involved.

```py
for fizzbuzz in range(51):
    if fizzbuzz % 3 == 0 and fizzbuzz % 5 == 0:
        print("fizzbuzz")
        continue
    elif fizzbuzz % 3 == 0:
        print("fizz")
        continue
    elif fizzbuzz % 5 == 0:
        print("buzz")
        continue
    print(fizzbuzz)
```

The seemingly simple code covers a number of new subjects for the non-programmer:

* strings
* mathematical operations
* lists
* invoking functions
* conditional operations
* loops
* exit conditions

The end result of being guided through all of this means that the non-programmer can produce a small chunk of code that is normally used in junior interviews.

When discussing with the non-programmer it is important to first show the outcome of fizzbuzz:

```
1
2
fizz
4
buzz
fizz
7
8
fizz
buzz
11
fizz
13
14
fizzbuzz
...
```

From here a discussion can be lead with "what is happening here?", "if we were to do the same with a deck of cards, what would we do?".

The important part is deciding as a group what the order of operations should be, what the code is "deciding" to do and what that would look like as an ordered list of decisions rather than the actual code. Non-programmers shouldn't be *too* worried about the syntax of code but more concerned about setting up the logic gates around the problem.

Before even touching the code a list can be drawn up as so:

1. create a list of 1-50
2. go through each number of the list
3. check if it is divisible by 3 and 5
   * if so print "fizzbuzz"
   * move to the next number
4. check if it is divisible by 3
   * if so print "fizz"
   * move to the next number
5. check if it is divisible by 5
   * if so print "buzz"
   * move to the next number
6. if none of the other rules are true then print the number

Getting started with code is infinitely easier than people think and we, as engineers, should be working to reduce these barriers for entry wherever possible. Showing how simple it would be to pass the first technical challenge in an interview is just the first step in this process
