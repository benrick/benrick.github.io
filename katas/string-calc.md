---
layout: page
title: String Calculator Kata
short_title: String Calculator
back_page: /katas/index.html
sidebar_link: false
---

This kata is designed to help you practice and learn to use TDD in a methodical way. To that end, please follow these rules:

- Try not to read ahead.
- Do **one task at a time**.
- Make sure you only test for **correct inputs**. there is no need to test for invalid inputs for this kata.
- Always write tests before making _any_ changes.

## String Calculator Kata Steps (step-by-step)

1. Create a `StringCalculator` object with a method `int Add(string numbers)`, taking a string parameter and returning a number.
	1. The *numbers* parameter can include 0, 1, or 2 integers (e.g. "", "1", "1,2").
	1. The return value should be the sum of the numbers given in the *numbers* string.
	1. Start with the simplest test case of an empty string, then 1 number, then 2.
	1. Solve things as **simply** as possible!
	1. **Note:** An empty string should return a sum of 0.
	1. Remember to refactor after each test.
1. Allow the `Add` method to handle an unknown quantity of numbers (in the string).
1. Allow the `Add` method to handle **new lines** between numbers (optionally instead of the commas).
	1. Example: "4\n5,6" returns 15.
1. Implement support for different delimiters between the numbers in the string.
	1. To change the delimiter, the beginning of the string should be a separate line formatted like this: `"//[delimiter]\n[numbers]"`
	1. Example: `"//;\n1;2"` returns 3 (the delimiter is ";").
	1. **Note:** This first line is optional; all existing scenarios should still work.
1. Calling `Add` with a **negative number** will throw an exception message `"Negatives not allowed: "` followed by the negative number that was in the list of nubmers.
	1. Example: `"-1,2"` throws `"Negatives not allowed: -1"`.
1. Calling `Add` with **multiple** negative numbers will throw an exception message `"Negatives not allowed: "` followed by a list all negative numbers that were in the list of numbers.
	1. Example: `"1,-2,3,-4"` throws `"Negatives not allowed: -2,-4"`.
1. Add a method to `StringCalculator` like `int GetCalledCount()` that will return how many times `Add()` has been called.
  1. Don't forget to use TDD, there should be a failing test before you make this method work!
1. Numbers greater than 1000 should be ignored.
	1. Example: `"2,1001"` returns `2`.
1. Allow multiple delimiters using this syntax: `"//[delimiter1][delimiter2]\n"`. Example: `"//[|||]\n1|||2|||3"` returns `6`.
1. Allow multi-character delimiters. Example: `"//[**]\n1,2**3"` returns `6`.

## Original Source

This is a Roy Osherove kata [https://osherove.com/tdd-kata-1/](https://osherove.com/tdd-kata-1/)
