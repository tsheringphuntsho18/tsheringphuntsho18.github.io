---
Title: DBS101 Flipped Class 4
categories: [DBS101, Flipped_class4]
tags: [DBS101]
---

## Topic:  Advanced Aggregation Functions 
We know that aggregation functions in SQL are used to perform calculations on a dataset. When we say advanced aggregation function it includes some advanced aggregation like boolean, statistical, regression and windowed aggregations. In this flipped class we discuss ranking, windowing, pivot and rollup and cube.

These four functions were divided among four groups and my group got to explain about ranking. So firstly let's talk about ranking.

### Ranking 
Ranking also has many types like rank, dense rank , row number and so on.

Rank() function gives a rank to each row by going through the specific data. Rank() function gives the same rank to the row having the same values and skips the next ranking. The number of rank skipped depends on how many rows had an identical ranking. E.g:

![aaf](pictures/rank.png)

Dense_rank() function also gives rank to each row in the dataset but unlike rank it handles ties differently. It assigns the same rank to those having the same values and doesn’t skip any rank. E.g:

![aaf](pictures/drnk.png)

Row_number() does not handle the tie, it gives a unique sequential number for each row.It gives the rank one for the first row and then increments the value by one for each row. E.g:

![aaf](pictures/Row.png)


Demo of the above mention ranking function.
RANK()

![aaf](pictures/rdemo.png)

DENSE_RANK()

![aaf](pictures/drdemo.png)

ROW_NUMBER()

![aaf](pictures/rndemo.png)
