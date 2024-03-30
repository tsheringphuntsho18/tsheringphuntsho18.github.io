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

![aaf](/assets/DBS_pictures/rank.png)

Dense_rank() function also gives rank to each row in the dataset but unlike rank it handles ties differently. It assigns the same rank to those having the same values and doesn’t skip any rank. E.g:

![aaf](/assets/DBS_pictures/drnk.png)

Row_number() does not handle the tie, it gives a unique sequential number for each row.It gives the rank one for the first row and then increments the value by one for each row. E.g:

![aaf](/assets/DBS_pictures/Row.png)


Demo of the above mention ranking function.

RANK()

![aaf](/assets/DBS_pictures/rdemo.png)

DENSE_RANK()

![aaf](/assets/DBS_pictures/drdemo.png)

ROW_NUMBER()

![aaf](/assets/DBS_pictures/rndemo.png)

### Widowing
Window function performs a calculation such as aggregation, ranking and moving average across a set of table rows related to the current row. Let’s imagine that we are looking out to a busy street from the window. We see different things, right? SQL window functions also work like that, they go through the data row by row and the cool thing is they remember what they have seen before and what’s coming up next.

There are two parts in a windowed aggregation:

OVER
The OVER clause  defines a window. This clause specifies how the rows that the function will operate on are determined. It can involve two parts:
Partition By
Order By

Rows Between or Range between
The difference between rows between and range between is that rows between specifies the distance in number of rows and range between specifies the distance in the values. 

DEMO

![demo](/assets/DBS_pictures/window.png)


### Pivoting
Pivot enables us to see rows as columns in a query result which makes data more readable and more presentable. The Unpivot operator does the opposite, that is it transforms the column based data into rows. E.g:

Suppose we have a table like this:
 
 ![demo](/assets/DBS_pictures/apivot.png)

And you want to pivot it so that each month's profit value is represented in a separate column, like this:

![demo](/assets/DBS_pictures/bpivot.png)

DEMO
Postgresql is not supporting pivot so can’t show a demo for pivot and unpivot. 

### Rollup and Cube
Rollup and cube make it possible for values to break it down in more detail, instead of just giving you one big summary (like a total). Rollup summarizes against a hierarchy of columns used in the group by clause. Cube groups by all combinations of the values.

Imagine we have a basket of apples. Normally, someone might just tell us "there are 50 apples." But with this approach, they'd tell you things like:

- 20 are red, 30 are green. 
- 10 are small, 30 are medium, 10 are large. 
- 40 are ripe, 10 are not quite ripe. 

This gives you a much richer understanding of the apples in the basket.

E.g:

Rollup

![demo](/assets/DBS_pictures/rol1.png)

Cube

![demo](/assets/DBS_pictures/cube1.png)


DEMO

Rollup

![demo](/assets/DBS_pictures/rollup.png)


Cube

![demo](/assets/DBS_pictures/cube.png)


As mentioned earlier, my group got advanced aggregation function ranking. It was a bit easy because the meaning is the same as that of the English language, but it was also a bit difficult because it has types and it follows certain rules when coding in sql. So being a software engineering student though we have little knowledge of function and all, we have great skill at googling. 

We referred to the link provided by the miss and many more links for better understanding. Then having got the ideas on how ranking works in sql, we prepared a demo on student’s results to present to the class later.

My friends from other groups have also done the presentation very well and cleared every doubt, leading to a better understanding on advance aggregation functions.
