---
layout : post
title: Notion Streaks Guide
date: 2023-04-8 11:00:00 +0200
categories: [Norion, Guides & Tools]
tags: [notion,streaks,tutorial,template]
---

# Create a Powerful Habit Tracker in Notion: Step-by-Step Guide to Counting Streaks 🔥



>🤓 Welcome fellow nerds ! Welcome to my guide. Here Is the mechanism behind my streak tracker. Hope you like it !


# How it works

**Objective**

Our goal is to create a habit tracker in Notion that counts the number of consecutive days we've checked the "Done" checkbox.

**Limitation**

Currently, Notion Formulas lack a built-in counter feature, so we'll need to devise a workaround.

**Step 1: Relate the databases**

First, we need to create two databases:

- The Calendar database with the "Done" checkbox
- The Habits database to count the streaks

Relate the two databases to each other using a relation property.

**Step 2: Add a rollup property**

Add a rollup property in the Habits database to display the "Done" checkboxes from the Calendar database. Note that the first checkbox will always be unchecked because it refers to the template we made inside the calendar.

**Step 3: Understand the checkbox values**

Unchecked boxes represent "No" and checked boxes represent "Yes." They are separated by commas. A "Yes" followed by a comma ("Yes,") is four characters, while "No," is three characters.

**Step 4: Count characters and use regex**

Count all characters using the "length" formula function. Then, use regex to remove the first array of "Yes," followed by "Yes". We use the “$” sign to start from the end. This leaves us with the rest of the string.

**Step 5: Calculate the streak**

Count the length of the remaining string and subtract it from the total number of characters. This gives us the number of characters representing consecutive "Yes" values. Divide this number by 4 (as "Yes," is four characters), and subtract 1 (since only one "Yes" doesn't have a comma). This final value is the number of last consecutive checked checkboxes and represents our streak.

## Databases


> 💡 This database is where you’ll be seeing your streaks. It needs 3 Formulas, a Relation and a Rollup property in order to work. The “format (Show Original)” Formula is used to explain how this method works.


[ Streak Tracker](https://www.notion.so/7284abd924dc465b862aec3150e99ce7)


> 💡 This is the Database where you’ll be setting up your habits. Aka the habit tracker. It needs a checkbox property. It also has to be shown as Created time. Be sure to watch this part of the video to set it up correctly. Also remember to make each habit repeat it self whenever you need it to (also mentioned in the video).


[Habit Tracker](https://www.notion.so/72708bf7819b4bcc9988035f5776b926)

## Formula Explanation

### Streak Tracker

```jsx
length(prop("Show original"))
```

```jsx
length(replaceAll(prop("Show original"), "(Yes,)+(Yes)$", "")) - 1
```

```jsx
if(prop("Total characters") - 1 == prop("removed consecutive Yes length"), "❄️", format((prop("Total characters") - prop("removed consecutive Yes length")) / 4) + "  🔥")
```

### Calendar

```jsx
if(not empty(prop("Date")), prop("Date"), prop("Created time"))
```