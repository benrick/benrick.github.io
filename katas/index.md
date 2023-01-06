---
layout: page
title: Coding Kata Catalog
short_title: Coding Katas
back_page: index.html
sidebar_link: true
sidebar_sort_order: 70
---

Welcome to my catalog of katas! I hope you find something to help you!

Coding Katas are a great way of practising your coding skills by going through a prescribed set of steps as defined by someone whose coding style you want to learn to replicate. By following each step they took solving the prompt, you can get used to the flow, approach, pattern, and cadence of refactoring.

Those can help, however, there are other exercises that we still call "katas" to help you establish the techniques and concepts that you want to exhibit in your day-to-day coding. In these, we receive a prompt or other instructions for what to code, but don't have a prescribed set of steps to follow, instead allowing us to decide our approach.

## [Bowling Game Kata](#bowling-game-kata)

The Bowling Game Kata is a classic kata with a [walkthrough by Uncle Bob Martin](http://butunclebob.com/ArticleS.UncleBob.TheBowlingGameKata).

### Bowling Summary

In this kata, the goal is to score a game of bowling for a single player. We don't need to show or track scores as we go, but only need the final score. Keeping things simple is what makes this an exercise instead of a full project.

#### Basics of Bowling

A player completes a game of bowling after bowling 10 frames. In each frame, the player rolls the ball down the lane 1 or 2 times trying to knock as many of the 10 pins at the end of the lane as possible (pins are reset for each frame). *Note: The player only makes the second roll if there are pins remaining standing after the first.*

If the player does not knock down all of the pins, their score is the number of pins they did knock down.

If the player knocked down all of the pins in a single roll, this is called a `strike`, and the player receives 10 points for their pins and a bonus point for each pin knocked down in their **next two rolls**.

If the player knocked down all of the pins on the second roll, this is called a `spare`, and the player receives their 10 points for their pins and a bonus point for each pin knocked down in the **next roll**.

In the final frame (10th), a player who rolls a strike or a spare will have extra rolls to complete the frame, because the bonus points need to be added for the strike or spare. Those rolls, however, won't earn bonus points.

### Instructions - Bowling Kata

Create a function named `Roll` with a single parameter for the number of pins. This function will be called each time a player rolls a ball.

Example in C#:

```cs
public void Roll(int pins)
{
  // Your Code here
}
```

Create a parameterless function named `FinalScore`, returning a number, to be called at the end of the game to determine the final score of the game for a single player.

```cs
public int FinalScore()
{
  // Your Code here
}
```

## [Fizz Buzz Kata](#fizz-buzz-kata)

Fizz Buzz is well-known introduction to programming exercises and katas, because it has a simple enough premise that one can learn the approach of the exercises without worrying about the challenge of any code itself.

This kata replicates a simple number game in which you count numbers, but replace some of the numbers with "Fizz", "Buzz", or "FizzBuzz" depending on the divisors of the number. For numbers divisible by 3, replace with "Fizz". For numbers divisible by 5, replace with "Buzz". For those divisible by both, replace with "FizzBuzz".

### Instructions - Fizz Buzz

- Create a function that prints (each on their own lines) the numbers 1 through 100 with the following exceptions:
  - Numbers divisible by 3 should print "Fizz" instead of the number.
  - Numbers divisible by 5 should print "Buzz" instead of the number.
  - Numbers divisible by 3 and 5 should print "FizzBuzz" instead of the number.

```
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
16
```

### Fizz Buzz Extra Credit

Finished the exercise early and want to add a bit more complexity?

- Numbers containing the digit '3' should print "Fizz" instead of the number.
- Numbers containing the digit '5' should print "Buzz" instead of the number.
- Numbers containing the digits '3' and '5' should print "FizzBuzz" instead of the number.

## [Gilded Rose Refactoring Kata](#gilded-rose-refactoring-kata)

In the Gilded Rose kata, you get to working someone else's code (Yay!) In this kata, you'll likely want to use careful refactoring as well as characterization testing to avoid breaking any existing features.

> "Hi and welcome to team Gilded Rose. As you know, we are a small inn with a prime location in a prominent city run by a friendly innkeeper named Allison. We also buy and sell only the finest goods. Unfortunately, our goods are constantly degrading in quality as they approach their sell by date. We have a system in place that updates our inventory for us. It was developed by a no-nonsense type named Leeroy, who has moved on to new adventures. The UpdateQuality() method is called each morning by another part of our system. Your task is to add the new feature to our system so that we can begin selling a new category of items. First an introduction to our system:
>
> - All items have a SellIn value which denotes the number of days we have to sell the item
> - All items have a Quality value which denotes how valuable the item is
> - At the end of each day our system lowers both values for every item
>
> Pretty simple, right? Well, this is where it gets interesting:
>
> - Once the sell by date has passed, Quality degrades twice as fast
> - The Quality of an item is never negative
> - "Aged Brie" actually increases in Quality the older it gets
> - The Quality of an item is never more than 50
> - "Sulfuras", being a legendary item, never has to be sold or decreases in Quality
> - "Backstage passes", like aged brie, increases in Quality as its SellIn value approaches
>   - Quality increases by 2 when there are 10 days or less
>   - Quality increases by 3 when there are 5 days or less
>  - Quality drops to 0 after the concert

### Instructions - Gilded Rose

We have recently signed a supplier of conjured items. This requires an update to our system:

- "Conjured" items degrade in Quality twice as fast as normal items

Feel free to make any changes to the UpdateQuality method and add any new code as long as everything still works correctly. However, do not alter the Item class or Items property as those belong to the goblin in the corner who will insta-rage and one-shot you as he doesn't believe in shared code ownership (you can make the UpdateQuality method and Items property static if you like, we'll cover for you).

Just for clarification, an item can never have its Quality increased above 50, however "Sulfuras" is a legendary item and as such its Quality is 80 and it never alters.

### Gilded Rose Extra Credit

- Item categories are determined by whether they contain a given string in their name (e.g. "Aged Brie" or "Sulfuras" or "Backstage passes")
- Any item can thus be conjured, with the resulting effects (e.g. "Conjured Backstage passes")

### Sources

- Original Source from NotMyself https://github.com/NotMyself/GildedRose
- A repository of starting code in various languages: https://github.com/emilybache/GildedRose-Refactoring-Kata

## [Greed Game Kata](#greed-game-kata)

Details coming soon.

## [Potter Kata](#potter-kata)

Details coming soon.

## [Prime Factors Kata](#prime-factors-kata)

Details coming soon.

## [String Calculator Kata](#string-calculator-kata)

Details coming soon.

## [Tennis Scoring Kata](#tennis-scoring-kata)

Details coming soon.

## [Lift Pass Pricing Kata](#lift-pass-pricing-kata)

Details coming soon.
