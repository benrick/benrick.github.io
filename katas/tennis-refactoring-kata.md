---
layout: page
title: Tennis Refactoring Kata
short_title: Tennis Refactoring Kata
back_page: /katas/index.html
sidebar_link: false
---

Tennis is a very popular sport. The game itself isn't too hard to understand, but the scoring is a little bit cryptic, using words like "love", "fifteen", "thirty", "fourty", "deuce", and "advantage" to describe the score of a game. Essentially, you have to win by 2 and have at least 4 points, but those aren't the words used. 

You start with no points, called "love" and get "fifteen", "thirty", and "forty" as your next 3 points. Once both players reach "forty", we call all subsequent ties "duece" and if a player gets a 1 point lead, they're said to have "advantage".

For this exercise, we're going to using [Emily Bache's Tennis Refactoring Kata](https://github.com/emilybache/Tennis-Refactoring-Kata). Using that link to her repository, you'll find sample code for quite a few languages, so pick one that you feel comfortable working with (or want to improve!)

Unlike most of the exercises we do, this one isn't about building the tests yourself, but is instead showing the value of _having_ those tests in place while refactoring. If you're ever working on code without tests, you can add a suite like this first.

## Kata Instructions

Imagine that you've just been assigned to work on this _mostly_ completed code, and your job is to finish it up, fix any bugs you find, and make some notes for improvements you would make.

- Download the source code and open the language of your choice.
- Pick a version of the tennis game code you want to start with (there are multiple that are all run by the same tests).
  - TennisGame1 and TennisGame3 are good first attempts, with the latter being more cryptic in its naming.
- Build and run the tests to confirm everything works locally.
- Review the code, making notes of any bugs, incomplete features, or code smells.
- Fix any bugs found, running tests as you work.
- Finish any incomplete features, running tests as you work.
- Fix any code smells, running tests as you work.

## Source Code

Here's the link to the source code for this exercise.

- A repository of starting code in various languages: [https://github.com/emilybache/Tennis-Refactoring-Kata](https://github.com/emilybache/Tennis-Refactoring-Kata)
