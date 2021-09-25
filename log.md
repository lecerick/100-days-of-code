# 100 Days Of Code - Lecerick's Log

### Day 0: Sun Aug 29, 2021

1. Updated [personal website](https://lenaerickson.com/) with a design change. Graphically interesting pictures, a darker brown bottom navbar, and border radius on two of the pics to make things less boxy. Liking the new website design a lot. In terms of future improvements, I could see adding a 'contact me' form, a blog, and a virtual art gallery.
2. Created the finance-playground repository. Created a simple python file that basically does the PMT function in excel for installment loans. [amortization_schedule.py](https://github.com/lecerick/finance-playground/blob/main/amortization_schedule.py) I'm excited to formalize my financial knowledge using coding. (Writing a useful program is a good way to ensure you really understand the math.)

### Day 1: Mon Aug 30, 2021

Added a basic discounting function to the AmSchedule class in finance-playground. Looking foward, introducing compounding conventions and/or [daycount conventions](https://www.investopedia.com/terms/d/daycount.asp) (30/360 vs. 30/365 vs. actual/360 vs. actual/365 vs. actual/actual) could be a good way to spice up the AmSchedule. I'm less familiar with semi-annual discounting (bond markets) than monthly (mortgage markets), so that could be a learning opportunity.

### Day 2: Tues Aug 31, 2021

Forked the #100-Days-Of-Code repo. Logging my progress could be helpful, especially if I stall at any point and need to look back on prior thoughts for inspiration. Also spent some time looking through other github users' logs to see what they're working on, and that's a good source of ideas too! [Data Science](https://github.com/emiliehwolf/100-days-of-code/blob/master/log.md) // [Spotify API](https://github.com/miukimiu/100-days-of-code/blob/master/log.md) // [Grab Bag](https://github.com/Mmgfrog/100-days-of-code/blob/master/log.md) // [Advanced Webdev](https://github.com/nativedone/100-days-of-code/blob/master/log.md) // [Beginner Projects](https://github.com/rachaelcodes/100-days-of-code/blob/master/log2017.md) // [Full List of Forks](https://github.com/kallaway/100-days-of-code/network/members)

### Day 3: Wed Sept 1, 2021

Created a new repo called [math-playground](https://github.com/lecerick/math-playground/), with a subfolder for [Project Euler](https://projecteuler.net/archives) problems. Solved [PE Problem #1](https://github.com/lecerick/math-playground/blob/main/PE/p001_multiples_of_3_or_5.py) using a python script, which was straightforward. There's definitely more or less efficient ways to solve these challenges... I wonder if there's a package or function I can use to time the operations and compare efficiencies, sort of like they do in LeetCode? 

### Day 4: Thurs Sept 2, 2021

[PE Problem #2](https://github.com/lecerick/math-playground/blob/main/PE/p002_even_fibonacci_numbers.py) solved, but only by brute force.

### Day 5: Fri Sept 3, 2021

Created some dummy data / tables and did a [SQL join](https://github.com/lecerick/finance-playground/blob/main/joins.sql).

### Days 6-7: Sat-Sun Sept 4-5, 2021

Started playing around with the [pyglet](https://github.com/pyglet/pyglet) python package, beginning with their [starting guide](https://pyglet.readthedocs.io/en/latest/programming_guide/quickstart.html) in the documentation. Not hosting this as a repository in github though since I'm just playing around with it for fun on the long Labor Day weekend.

### Day 8: Mon Sept 6, 2021

[PE Problem #3](https://github.com/lecerick/math-playground/blob/main/PE/p003_largest_prime_factor.py) solved. Today's problem was to find the largest prime factor of a relatively big number. This is the first PE problem where I ran into run time issues with my original implementation (which worked on the smaller number just fine). So I had to come up with a more elegant approach out of necessity. 

### Day 9: Tues Sept 7, 2021

[PE Problem #4](https://github.com/lecerick/math-playground/blob/main/PE/p004_largest_palindrome_product.py) solved. This problem has to do with Palindrome numbers. At first, I tried to use modular arithmetic and divisors to determine the value of the various digits, but realized it would be easier to use strings and substring logic. Just because it's a math problem doesn't mean strings can't be handy!

### Day 10: Wed Sept 8, 2021

[PE Problem #5](https://github.com/lecerick/math-playground/blob/main/PE/p005_smallest_multiple.py) solved. 

### Day 11: Thurs Sept 9, 2021

[PE Problem #6](https://github.com/lecerick/math-playground/blob/main/PE/p006_sum_square_difference.py) solved. This one was very easy. Since I had extra time, I found a library that will time the run time difference of two methods, and chose the first 10 million natural numbers as a big enough experiment to observe a scaling difference. The console output follows:
```
BRUTE FORCE METHOD
2500000166666641666665000000
0:00:02.145663
```
```
CLEVER METHOD
2500000166666641498542440448
0:00:00.000087
```
To my horror, I notice that the answers no longer match between BRUTE FORCE and CLEVER methods. How? Why?
At first, my thought was that the brute force method was the wrong answer, since it appeared to be rounded. But upon googling, I found that Python 3 does not have any sort of cap on how large integers can get. I also ran the lower powers of 10, and the brute force answer for 10 ** 7 looked more consistent with those answers. So... the clever method? Could it be? More googling. The docs point to [Floating Point Arithmetic: Issues and Limitations](https://docs.python.org/3/tutorial/floatingpoint.html), which makes a lot of sense, since the clever method involves division and hence operations on float data types. The clever method is WAY quicker, but it's also inaccurate for large N. 

So my challenge to myself is this: maybe there's another option... a method that scales nearly as well as the clever method, but has the guaranteed accuracy of the brute force function. At this point, I'm going to be late for work, so we'll pick up on that question later. :)

Ok, got home from work and figured it out. Created a new function "cleverer" that fixed it by not using floats at all (since they're not actually necessary for this problem, it's just what Python was using since I had division involved.) I just swapped from the / operator to // so the outcome is an int (which it would be anyway, it's a sum/square of ints). 

Looking at the outcome over powers of 10, you can see the difference in the two methods. Brute force is O(n) and Clever is O(1), i.e. constant. I tried to run the brute force method on 10 ** 10 and stopped it after an hour of run time. It's really cool to see Big O in my own little experiment :)

```
N = 10 ** 1
BRUTE FORCE METHOD:  2640
BRUTE FORCE RUNTIME: 0:00:00.000188
CLEVER METHOD:       2640
CLEVER RUNTIME:      0:00:00.000095
---------------------------------------------------------------------------
N = 10 ** 2
BRUTE FORCE METHOD:  25164150
BRUTE FORCE RUNTIME: 0:00:00.000108
CLEVER METHOD:       25164150
CLEVER RUNTIME:      0:00:00.000061
---------------------------------------------------------------------------
N = 10 ** 3
BRUTE FORCE METHOD:  250166416500
BRUTE FORCE RUNTIME: 0:00:00.000313
CLEVER METHOD:       250166416500
CLEVER RUNTIME:      0:00:00.000062
---------------------------------------------------------------------------
N = 10 ** 4
BRUTE FORCE METHOD:  2500166641665000
BRUTE FORCE RUNTIME: 0:00:00.002393
CLEVER METHOD:       2500166641665000
CLEVER RUNTIME:      0:00:00.000092
---------------------------------------------------------------------------
N = 10 ** 5
BRUTE FORCE METHOD:  25000166664166650000
BRUTE FORCE RUNTIME: 0:00:00.023343
CLEVER METHOD:       25000166664166650000
CLEVER RUNTIME:      0:00:00.000088
---------------------------------------------------------------------------
N = 10 ** 6
BRUTE FORCE METHOD:  250000166666416666500000
BRUTE FORCE RUNTIME: 0:00:00.227982
CLEVER METHOD:       250000166666416666500000
CLEVER RUNTIME:      0:00:00.000098
---------------------------------------------------------------------------
N = 10 ** 7
BRUTE FORCE METHOD:  2500000166666641666665000000
BRUTE FORCE RUNTIME: 0:00:02.141993
CLEVER METHOD:       2500000166666641666665000000
CLEVER RUNTIME:      0:00:00.000079
---------------------------------------------------------------------------
N = 10 ** 8
BRUTE FORCE METHOD:  25000000166666664166666650000000
BRUTE FORCE RUNTIME: 0:00:20.984449
CLEVER METHOD:       25000000166666664166666650000000
CLEVER RUNTIME:      0:00:00.000075
---------------------------------------------------------------------------
N = 10 ** 9
BRUTE FORCE METHOD:  250000000166666666416666666500000000
BRUTE FORCE RUNTIME: 0:03:30.901138
CLEVER METHOD:       250000000166666666416666666500000000
CLEVER RUNTIME:      0:00:00.000083
```

### Day 12: Fri Sept 10, 2021

PE Problems [#7](https://github.com/lecerick/math-playground/blob/main/PE/p007_10001st_prime.py) and [#8](https://github.com/lecerick/math-playground/blob/main/PE/p008_largest_product_in_a_series.py) solved.


### Day 13: Sat Sept 11, 2021

[PE Problem #9](https://github.com/lecerick/math-playground/blob/main/PE/p009_special_pythagorean_triplet.py) solved.

### Day 14: Mon Sept 13, 2021

I had to work over the weekend, and between that and family stuff I didn't get any coding in yesterday. :(

Today I solved [PE Problem #10](https://github.com/lecerick/math-playground/blob/main/PE/p010_summation_of_primes.py). It took over a minute of run time (maybe 5 min? I didn't time it), which indicates there's a clever solution I haven't thought of yet. May come back to this one.

### Day 15: Wed Sept 15, 2021

Unfortunately I missed yesterday too. Been putting so much energy into work recently. Had a very weird day yesterday anyway, was super tired and lethargic.

Today I solved [PE Problem #11](https://github.com/lecerick/math-playground/blob/main/PE/p011_largest_product_in_a_grid.py). It's a pretty wordy solution that could definitely be made into fewer lines of code, but hey - it works. 

Over the past week(s) I've really gravitated to the project euler problems, I think because they are so easy to get started on and only take the small amount of time I have in the mornings before work. Despite being relatively straightforward challenges, these problems have been quite effective at forcing familiarization with basic syntax and tools of Python. Thus far, the primary topics have been lists (lists of lists!), strings and substring logic, for and while loops, and data types. I have not had to interface with any other data structures (hashmaps, queues, stacks, trees), but I'd like to. Algorithms (e.g. searching and sorting methods) would be a natural next step after that.

### Day 16: Thurs Sept 16, 2021

Working on [PE Problem #12](https://github.com/lecerick/math-playground/blob/main/PE/p012_highly_divisible_triangular_number.py), having run time issues. There's definitely a more efficient way to find the number of divisors...

### Day 17: Sun Sept 19, 2021

Finally created an efficient solution to [PE Problem #12](https://github.com/lecerick/math-playground/blob/main/PE/p012_highly_divisible_triangular_number.py)! I used a function from PE #3 that finds a prime divisor of N, in order to create a method that finds the prime factorization of N. Based on the prime factorization, it's very efficient (formulaic even) to find the number of divisors of N. An efficiency being used here is that I'm not actually finding all the divisors, just the divisor *count.* One small bump in the road that I learned from: in order to call a function in another python file, I realized that the file name couldn't start with a number, which conflicted with my prior naming convention. Hence, I changed the files of all of my PE problems from 00X_problem_title.py to p00X_problem_title.py. I'm proud of my solution this problem; it was hard won.

Also (later in the day) solved [PE Problem #13](https://github.com/lecerick/math-playground/blob/main/PE/p013_large_sum.py). Had to revisit how to do I/O on a text file since the input was a bit unwieldy.

### Day 18: Mon Sept 20, 2021

Solved [PE Problem #14: Longest Collatz Sequence](https://github.com/lecerick/math-playground/blob/main/P/Ep014_longest_collatz_sequence.py).

### Day 19: Tues Sept 21, 2021

Updated personal website

### Day 20: Wed Sept 22, 2021

Solved PE Problem [#15: Lattice Paths](https://github.com/lecerick/math-playground/blob/main/PE/p015_lattice_paths.py) using Pascal's Triangle.

### Day 21: Thurs Sept 23, 2021

Solved PE Problem [#16: Power Digit Sum](https://github.com/lecerick/math-playground/blob/main/PE/p016_power_digit_sum.py).

### Day 22: Fri Sept 24, 2021

Solved PE Problem [#17: Number Letter Counts](https://github.com/lecerick/math-playground/blob/main/PE/p017_number_letter_counts.py).
