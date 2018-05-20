---
layout: post
title:  "Coding is Easy, Testing is Hard"
date:   2018-05-20 14:26:30 -0400
categories: blog
---

## Why Testing?

This is the first question I asked when faced with the sub-skill of unit testing and test driven development (TDD). When asking other devs their opinion of unit testing as a skill, the less experienced skeptically see it as a time-suck. On the other hand, more experienced devs tersely proclaim "it's important" without much explanation as to *why*. Why is this the case?

For new developers it's an easy skill to sweep under the rug and we'll look at these common barriers in the next section. For experienced developers, even those that have good testing habits, it can be difficult to describe the benefits of unit testing as are often experiential in nature. It's tough to track down the ratio of bugs to lines of code over time unless you were thinking way ahead in your career. So take a birds-eye view of the *why* for unit testing and/or TDD.

**Writing tests saves you time in the long run.**  
Writing tests saves time in countless ways. According to [Eric Elliot](https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d) well-written unit tests serve as free documentation to future dev on a project. This is because each test is given a clear description of its purpose and expected outcome.
Tests can also be implemented into a continuous delivery system that blocks bugged code from production, saving you time on backtracking a defective code push.

**Unit tests will cut down on QA**  
This is because manual QA involves a lot of clicking around, loading assets, timing situations so that you can manually test what a user may (or may not) encounter while using your app. I find myself doing this type of thing every day and while it does have a place in the pipeline of creating production-ready web apps, it often sucks disproportionate amounts of time out of a dev's work day.

**TDD increases code quality**  
This is because writing a test for some function, method or feauture in your API requires deep understanding of the logic *and* flow of that code. This forces the developer to rescan code blocks for opportunities to improve its logic and/or readability. On top of that if you find that some methods are simply to hefty to easily test, it may signal that this method should be further modularized or just simpler.

**TDD decreases bug encounters**  
Bugs are no match for a proper suite of tests. The [Microsoft developer docs](https://msdn.microsoft.com/en-us/library/aa730844(v=vs.80) describe the test suite as a "regression safety net", explaing that if a bug is found, a test which reveals the bug is to be written first, then the code is modified until it passes that test while still passing all previous tests. This ensures that the bug will never reappear.

So why aren't we all writing tests already?

## But Why Testing?
#### Common Barriers to Testing
 Perhaps the easiest excuse for me to muster in the fight against writing unit tests is that it just takes too much time. If your in the same boat, you're not necessarily wrong. Most experienced testers will freely admit that if writing tests isn't a regular practice for you it is difficult to start --that it does take more time than it saves. But isn't this the case with most skills? Testing is like riding a bike. The time it takes to learn is greater than the time it takes to walk to where you originally wanted to go, but once you've learned you can get to that place and others faster, forever. Bite the bullet, learn testing, save yourself time in the long run. Your return on investment increases exponentially.

 Another common barrier is that writing tests seem stupid redundant. This excuse is most likely born out of a misunderstanding for what a test is doing for you. You don't write tests to squash bugs, you write them to avoid bugs. According to test driven development principles you should write the test first, then write the code that will  actually be tested. So, if the tests are written well,  the time you end up saving is time you'll never know you gained. This is why many devs, when first asked, can't explain the immediate benefits of testing. It's an experience.

## Learn More About it
Here a few great articles on the subject.

1. [5 Questions Every Unit Test Must Answer](https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d)
2. [Guideline For Test Driven Development](https://msdn.microsoft.com/en-us/library/aa730844(v=vs.80)
3. [9 Benefits of Test Driven Development](https://www.madetech.com/blog/9-benefits-of-test-driven-development)

Bottom line is that coding is one aspect of what you do but testing will become an equally important partner in your journey to dev greatness. IT will force quality and understanding on all that you code.



### Until Next Time

## Take it Easy
