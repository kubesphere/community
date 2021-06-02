# Code Review Guide
> This documentation is mostly from [Google's Engineering Practices documentation](https://google.github.io/eng-practices/), we borrowed some highlights. It's highly recommended to read the original documentation.

## The Standard of Code Review

The primary purpose of code review is to make sure that the overall health of KubeSphere's code base is improving over time.

**In general, reviewers should favor approving a CL once it is in a state where it definitely improves the overall code health of the system being worked on, even if the CL isn’t perfect.**

### Mentoring

Code review can have an important function of teaching developers something new about a language, a framework, or general software design principles. It’s always fine to leave comments that help a developer learn something new. Sharing knowledge is part of improving the code health of a system over time. 

### Principles
* Technical facts and data overrule opinions and personal preferences.
* On matters of style, [CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments) is the authority.
* Aspects of software design are almost never a pure style issue or just a personal preference.


## What to look for in a code review

### Summary

In doing a code review, you should make sure that:

* The code is well-designed.
* The functionality is good for the users of the code.
* Any UI changes are sensible and look good.
* Any parallel programming is done safely.
* The code isn’t more complex than it needs to be.
* The developer isn’t implementing things they *might* need in the future but don’t know they need now.
* Code has appropriate unit tests.
* Tests are well-designed.
* The developer used clear names for everything.
* Comments are clear and useful, and mostly explain **why** instead of **what**.
* Code is appropriately documented (generally in g3doc).
* The code conforms to our style guides.

Make sure to review **every line** of code you’ve been asked to review, look at the **context**, make sure you’re **improving code health**, and compliment developers on **good things** that they do.

## Navigating a PR in review Summary

Now that you know [what to look for](), what’s the most efficient way to manage a review that’s spread across multiple files?

* Does the change make sense? Does it have a good description?
* Look at the most important part of the change first. Is it well-designed overall?
* Look at the rest of the CL in an appropriate sequence.


## How to write code review comments

### Summary

* Be kind.
* Explain your reasoning.
* Balance giving explicit directions with just pointing out problems and letting the developer decide.
* Encourage developers to simplify code or add code comments instead of just explaining the complexity to you.
