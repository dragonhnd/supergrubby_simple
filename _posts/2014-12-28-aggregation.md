---
layout: article
title: "Aggregation"
date: 2014-12-28 13:24:21
categories: hack
---

> Aggregations are operations that process data records and return computed results.

Modern databse can do many aggregation work for you. That's the idealistic scenario - you get exactly what you need using some operators, no extra data I/O, no need to code the logic(which means less potential mistakes).

While, if you change your database, you have to check or sometimes rewrite the operations. And if you want to control the process of aggregation, you need to code yourself. So it's always necessary to understand the concept, process and types of aggregation.

## Types of Aggregation

### Filtering

SQL: HAVING, WHERE

MongoDB operator: $match


### Sorting

SQL: ORDER BY

MongoDB operator: $sort

### Grouping

SQL: GROUP BY

MongoDB operator: $group

### Projecting

SQL: SELECT

MongoDB operator: $project

### Aggregating items or item's values

SQL: SUM(), COUNT()

MongoDB operator: $sum

## Implementation by yourslef

The logic for filtering and projecting seems easy, while there might be a lot of knowledge when coming to grouping and sorting.

###1. Filtering

Iterate and find the element match then put it into the result.

###2. Sorting

define the sorting rule( field by which sorted and sorting order), iterate and put the sorted element into the result

###3. Grouping

Based on the grouping condition, iterate then put element into corresponding result

###4. Projecting

Get the fields into some kind of data structure and fileds.
