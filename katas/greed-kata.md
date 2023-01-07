---
layout: page
title: Greed Game Kata
short_title: Greed Kata
back_page: /katas/index.html
sidebar_link: false
---

The Greed Game Kata is based on the dice rolling, push-your-luck game of the same name. In that game, two or more players take turns rolling a set of 6 six-sided dice. Each turn has the player rolling the dice to try to earn points, and the player can choose to reroll some dice in a risky attempt to earn more points for that turn. We won't be building this whole game. For now, we'll just build a method that can determine the score of a single roll of the dice without consideration for rerolling.

## Instructions

Write a function to calculate the score of a given roll of 6 six-sided dice. When rolled, each die will have a result of 1, 2, 3, 4, 5, or 6. For scoring, using each die only one time, figuring out which rules will give the player the most points.

### Scoring Rules

**Singles:**
- A single one (100 points)
- A single five (50 points)

**Triples:**
- Triple twos [2,2,2] (200 points)
- Triple threes [3,3,3] (300 points)
- Triple fours [4,4,4] (400 points)
- Triple fives [5,5,5] (500 points)
- Triple sixes [6,6,6] (600 points)

**Quads:**
- Four ones [1,1,1,1] (1000 points)

### Example Score Outputs

- [1,1,1,5,1,6] = 1050 points
- [2,2,3,3,4,6] = 0 points
- [3,4,5,3,3,4] = 350 points
- [3,3,3,4,4,4] = 700 points
- [5,5,5,1,1,4] = 700 points

## Extra Credit

Finished the exercise early and want to add a bit more complexity?

- The number of dice rolled can vary. Allow 1-6 dice to be rolled instead of just 6.
- Six-of-a-Kind [#,#,#,#,#,#] = 5000 points
- Straight [1,2,3,4,5,6] = 1000 points
- Three Pairs = 800 points (e.g. [1,1,3,3,5,5] = 800)
