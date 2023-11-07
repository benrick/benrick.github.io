---
layout: page
title: Lift Pass Pricing Kata
short_title: Lift Pass Kata
back_page: /katas/index.html
sidebar_link: false
---

The Lift Pass Pricing Kata is a refactoring kata, which means that we start with an existing codebase. You can find the [original instructions and the starting source code for the kata here](https://github.com/martinsson/Refactoring-Kata-Lift-Pass-Pricing).

In this kata, we have an existing application that is a web API endpoint used to determine the price for buying a single pass to ride on a ski lift. This code is not written to be testable or reusable, which makes it a great candidate for our purpose of practicing refactoring.

## Instructions

The application is currently only able to provide the price of one pass at a time, so a consuming application would need to call this endpoint multiple times in order to get the prices for multiple tickets.

New Feature Request: **We need to be able to request the price for more than one lift pass at a time**.

### Suggested Steps

- Create a set of characterization tests using high-level functional testing at the endpoint level.
- Change the code to make future testing and the addtion of the new feature easier.
- Create unit tests where possible.
- Write code to allow multiple passes to be priced with appropriate tests on the new code.

### Tips

- Start with integration tests that rely on the database to ensure existing functionality is maintained.
- Extract code where possible to separate the API endpoint, database access, and the business logic.
- Create unit tests when possible around the extracted business logic.

## Database Installation

This application uses a MySql database by default. The [instructions for setting up this database](https://github.com/martinsson/Refactoring-Kata-Lift-Pass-Pricing#installation) can be found with the original source samples.
