---
layout: default
title: programming for non-programmers
description: "using fizzbuzz to help non-programmers get their programming hands dirty"
order: 16
---

<p>I was fortunate enough to run an <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4310607/#:~:text=Unlike%20traditional%20conferences%2C%20an%20unconference,even%20the%20time%20and%20venues.">unconference</a> at my company's recent offsite titled "programming for non-programmers". When deciding what tasks and challenges we could do as a group I settled on fizzbuzz. <a href="https://en.wikipedia.org/wiki/Fizz_buzz#:~:text=Fizz%20buzz%20is%20a%20group,with%20the%20word%20%22fizzbuzz%22.">Fizzbuzz</a> is a fairly simple programming challenge often presented to junior engineers. I will paste my solution below and then dive into why I think this is the perfect fit for non-programmers to get involved.</p>

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

<p>The seemingly simple code covers a number of new subjects for the non-programmer:
  <ul>
    <li>strings</li>
    <li>mathematical operations</li>
    <li>lists</li>
    <li>invoking functions</li>
    <li>conditional operations</li>
    <li>loops</li>
    <li>exit conditions</li>
  </ul>
The end result of being guided through all of this means that the non-programmer can produce a small chunk of code that is normally used in junior interviews. 
</p>
<p>
  When discussing with the non-programmer it is important to first show the outcome of fizzbuzz:

<code>
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
</code>
<br>
From here a discussion can be lead with "what is happening here?", "if we were to do the same with a deck of cards, what would we do?".
  </p>
<p>
  The important part is deciding as a group what the order of operations should be, what the code is "deciding" to do and what that would look like as an ordered list of decisions rather than the actual code. Non-programmers shouldn't be <i>too</i> worried about the syntax of code but more concerned about setting up the logic gates around the problem.
</p>
<p>Before even touching the code a list can be drawn up as so:
<ol>
  <li>create a list of 1-50</li>
  <li>go through each number of the list</li>
  <li>check if it is divisible by 3 and 5</li>
    <ul id="list2">
    <li>if so print "fizzbuzz"</li>
    <li>move to the next number</li>
  </ul>
  <li>check if it is divisible by 3</li>
    <ul id="list2">
    <li>if so print "fizz"</li>
    <li>move to the next number</li>
  </ul>
<li>check if it is divisible by 5</li>
    <ul id="list2">
    <li>if so print "buzz"</li>
    <li>move to the next number</li>
  </ul>
  <li>if none of the other rules are true then print the number</li>
  </ol>
<p>Getting started with code is infinitely easier than people think and we, as engineers, should be working to reduce these barriers for entry wherever possible. Showing how simple it would be to pass the first technical challenge in an interview is just the first step in this process</p>


