# 100 Days Of Code - Lecerick's Log

### Day 0: Sun Aug 29, 2021

1. Updated [personal website](https://lenaerickson.com/) with a design change. Graphically interesting pictures, a darker brown bottom navbar, and border radius on two of the pics to make things less boxy. Liking the new website design a lot. In terms of future improvements, I could see adding a 'contact me' form, a blog, and a virtual art gallery.
2. Created the finance-playground repository. Created a simple python file that basically does the PMT function in excel for installment loans. [amortization_schedule.py](https://github.com/lecerick/finance-playground/blob/main/amortization_schedule.py) I'm excited to formalize my financial knowledge using coding. (Writing a useful program is a good way to ensure you really understand the math.)

### Day 1: Mon Aug 30, 2021

Added a basic discounting function to the AmSchedule class in finance-playground. Looking foward, introducing compounding conventions and/or [daycount conventions](https://www.investopedia.com/terms/d/daycount.asp) (30/360 vs. 30/365 vs. actual/360 vs. actual/365 vs. actual/actual) could be a good way to spice up the AmSchedule. I'm less familiar with semi-annual discounting (bond markets) than monthly (mortgage markets), so that could be a learning opportunity.

### Day 2: Tues Aug 31, 2021

Forked the #100-Days-Of-Code repo. Logging my progress could be helpful, especially if I stall at any point and need to look back on prior thoughts for inspiration. Also spent some time looking through other github users' logs to see what they're working on, and that's a good source of ideas too! [Data Science](https://github.com/emiliehwolf/100-days-of-code/blob/master/log.md) // [Spotify API](https://github.com/miukimiu/100-days-of-code/blob/master/log.md) // [Completed All 100 Days! Grab Bag of Topics](https://github.com/Mmgfrog/100-days-of-code/blob/master/log.md) // [Advanced Webdev](https://github.com/nativedone/100-days-of-code/blob/master/log.md) // [Beginner Projects](https://github.com/rachaelcodes/100-days-of-code/blob/master/log2017.md) // [Full List of Forks](https://github.com/kallaway/100-days-of-code/network/members)

### Day 3: Wed Sept 1, 2021

Created a new repo called [math-playground](https://github.com/lecerick/math-playground/), with a subfolder for [Project Euler](https://projecteuler.net/archives) problems. Solved [PE Problem #1](https://github.com/lecerick/math-playground/blob/main/PE/problem001.py) using a python script, which was straightforward. There's definitely more or less efficient ways to solve these challenges... I wonder if there's a package or function I can use to time the operations and compare efficiencies, sort of like they do in LeetCode? 

### Day 4: Thurs Sept 2, 2021

[PE Problem #2](https://github.com/lecerick/math-playground/blob/main/PE/problem002.py) solved, but only by brute force.

### Day 5: Fri Sept 3, 2021

Created some dummy data / tables and did my first [SQL join](https://github.com/lecerick/finance-playground/blob/main/joins.sql).

### Days 6-7: Sat-Sun Sept 4-5, 2021

Started playing around with the [pyglet](https://github.com/pyglet/pyglet) python package, beginning with their [starting guide](https://pyglet.readthedocs.io/en/latest/programming_guide/quickstart.html) in the documentation. Not hosting this as a repository in github though since I'm just playing around with it for fun on the long Labor Day weekend.

### Day 8: Mon Sept 6, 2021

[PE Problem #3](https://github.com/lecerick/math-playground/blob/main/PE/problem003.py) solved. Today's problem was to find the largest prime factor of a relatively big number. This is the first PE problem where I ran into run time issues with my original implementation (which worked on the smaller number just fine). So I had to come up with a more elegant approach out of necessity. 

### Day 9: Tues Sept 7, 2021

[PE Problem #4](https://github.com/lecerick/math-playground/blob/main/PE/problem004.py) solved. This problem has to do with Palindrome numbers. At first, I tried to use modular arithmetic and divisors to determine the value of the various digits, but realized it would be easier to use strings and substring logic. Just because it's a math problem doesn't mean strings can't be handy!

### Day 10: Wed Sept 8, 2021

[PE Problem #5](https://github.com/lecerick/math-playground/blob/main/PE/problem005.py) solved. 

### Day 11: Thurs Sept 9, 2021

[PE Problem #6](https://github.com/lecerick/math-playground/blob/main/PE/problem006.py) solved. This one was very easy. Since I had extra time, I timed the run time difference of two methods (brute force vs. clever) when finding the value for the first 10 million natural numbers. 
```
$ BRUTE FORCE METHOD
$ 2500000166666641666665000000
$ 0:00:02.145663
$ ---------------
$ CLEVER METHOD
$ 2500000166666641498542440448
$ 0:00:00.000087
```
