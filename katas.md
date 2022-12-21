---
layout: page
title: Coding Kata Catalog
short_title: Coding Katas
back_page: index.html
sidebar_link: true
sidebar_sort_order: 70
---

Welcome to my catalog of katas! I hope you find something to help you!

## Katas

Coding Katas are a great way of practising your coding skills by going through a prescribed set of steps as defined by someone whose coding style you want to learn to replicate. By following each step they took solving the prompt, you can get used to the flow, approach, pattern, and cadence of refactoring.

Those can help, however, there are other exercises that we still call "katas" to help you establish the techniques and concepts that you want to exhibit in your day-to-day coding. In these, we receive a prompt or other instructions for what to code, but don't have a prescribed set of steps to follow, instead allowing us to decide our approach.

### Bowling Game Kata

The Bowling Game Kata is a classic kata with a [walkthrough by Uncle Bob Martin](http://butunclebob.com/ArticleS.UncleBob.TheBowlingGameKata).

#### Summary

In this kata, the goal is to score a game of bowling for a single player. We don't need to show or track scores as we go, but only need the final score. Keeping things simple is what makes this an exercise instead of a full project.

##### Basics of Bowling

A player completes a game of bowling after bowling 10 frames. In each frame, the player rolls the ball down the lane 1 or 2 times trying to knock as many of the 10 pins at the end of the lane as possible (pins are reset for each frame). *Note: The player only makes the second roll if there are pins remaining standing after the first.*

If the player does not knock down all of the pins, their score is the number of pins they did knock down.

If the player knocked down all of the pins in a single roll, this is called a `strike`, and the player receives 10 points for their pins and a bonus point for each pin knocked down in their **next two rolls**.

If the player knocked down all of the pins on the second roll, this is called a `spare`, and the player receives their 10 points for their pins and a bonus point for each pin knocked down in the **next roll**.

In the final frame (10th), a player who rolls a strike or a spare will have extra rolls to complete the frame, because the bonus points need to be added for the strike or spare. Those rolls, however, won't earn bonus points.

#### Instructions

Create a function named `Roll` with a single parameter for the number of pins. This function will be called each time a player rolls a ball.

Example in C#:

```cs
public void Roll(int pins)
{
  // Code here
}
```

Create a parameterless function named `FinalScore`, returning a number, to be called at the end of the game to determine the final score of the game for a single player.

```cs
public int FinalScore()
{
  // Code here
}
```

### Fizz Buzz Kata

Details coming soon.

### Gilded Rose Refactoring Kata

Details coming soon.

### Greed Game Kata

Details coming soon.

### Potter Kata

Details coming soon.

### Prime Factors Kata

Details coming soon.

### String Calculator Kata

Details coming soon.

### Tennis Scoring Kata

Details coming soon.

### Lift Pass Pricing Kata

Details coming soon.
