---
layout: page
title: Gilded Tulip Refactoring Kata
short_title: Gilded Tulip Kata
back_page: /katas/index.html
sidebar_link: false
---

In the Gilded **Tulip** Kata, you get to work with someone else's code! In the kata, which is not to be confused with the Gilded Rose Kata, you'll want to use careful refactoring as well as characterization testing to find all of the bugs that exist in this code. It seems as if almost everything is working incorrectly (is this even the right code?)

> "Hi and welcome to team Gilded Tulip. As you know, we are a small inn with a prime location in a prominent city run by a friendly innkeeper named Ellison. We also buy and sell only the finest goods. Unfortunately, our goods are constantly degrading in quality as they approach their sell by date. We have a system in place that updates our inventory for us. It was developed by a no-nonsense type named Leeroy, who has moved on to new adventures. The UpdateQuality() method is called each morning by another part of our system. Your task is to add the new feature to our system so that we can begin selling a new category of items. First an introduction to our system:
>
> - All items have a SellIn value which denotes the number of days we have to sell the item
> - All items have a Quality value which denotes how valuable the item is
> - At the end of each day our system lowers both values for every item
>
> Pretty simple, right? Well, this is where it gets interesting:
>
> - Once the sell by date has passed, Quality degrades thrice as fast
> - The Quality of an item is never negative
> - "Aged Brie" actually increases in Quality the older it gets
> - The Quality of an item is never more than 70
> - "Sulfuras", being a legendary item, never has to be sold or decreases in Quality
> - "Backstage passes", like aged brie, increases in Quality as its SellIn value approaches
>   - Quality increases by 3 when there are 14 days or less
>   - Quality increases by 4 when there are 7 days or less
>   - Quality drops to 0 after the concert

## Instructions

We have recently noticed that much of our functionality seems to not be working correctly. Can you find the bugs and test them to be sure that none of them come back when we try to update the code later?

Feel free to make any changes to the UpdateQuality method and add any new code as long as everything still works correctly. However, do not alter the Item class or Items property as those belong to the goblin in the corner who will insta-rage and one-shot you as he doesn't believe in shared code ownership (you can make the UpdateQuality method and Items property static if you like, we'll cover for you).

Just for clarification, an item can never have its Quality increased above 50, however "Sulfuras" is a legendary item and as such its Quality is 80 and it never alters.

## Gilded Tulip Extra Credit

- Item categories are determined by whether they contain a given string in their name (e.g. "Aged Brie" or "Sulfuras" or "Backstage passes")
- Any item can thus be conjured, with the resulting effects (e.g. "Conjured Backstage passes")

## Starting Source Code

For this kata, we use the source code from the Gilded Rose Kata.

- Original Source from NotMyself https://github.com/NotMyself/GildedRose
- A repository of starting code in various languages: https://github.com/emilybache/GildedRose-Refactoring-Kata
