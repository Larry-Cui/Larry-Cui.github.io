---
layout: post
title: Radix Sort
date: 2022-12-9
tags:
  - Algorithms
---

This post is based on [Geeksforgeeks](https://www.geeksforgeeks.org/radix-sort/), [Brilliant](https://brilliant.org/wiki/radix-sort/) and [Interview Kickstart](https://www.interviewkickstart.com/learn/radix-sort-algorithm).

The lower bound for the comparison based sorting algorithm (Merge Sort, Heap Sort, Quick-Sort .. etc) is $O(nLogn)$. They cannot do better than that. Counting sort is a linear time sorting algorithm that sort in $O(n+k)$ time when elements are in the range from 1 to k.

What if the total amount of elements is n, but the values are in the range from 1 to $n^2$ or even larger?

We can’t use counting sort because counting sort will take at least $O(n^2)$ which is worse than comparison-based sorting algorithms.

Can we sort such an array in linear time?

**Radix Sort** is the answer. The idea of radix sort is to do digit by digit sort starting from least significant digit to most significant digit. When sorting each digit, radix sort can use any sort algorithm as long as it's [stable](https://www.freecodecamp.org/news/stability-in-sorting-algorithms-a-treatment-of-equality-fa3140a5a539/). And as a prevalent custom, people use counting sort as a subroutine to sort.

Say we have an array: $[455, 61, 63, 45, 67, 135, 74, 49, 15, 5]$.

Here's how we do sort using radix sort:

<img style="display: inline-block; width: 90%; object-fit: cover;" src="https://lh3.googleusercontent.com/V3H--XYTI8ZUF-6LagfOZrlpjamhFrX803u7TRKl07v-Wlc7skSyApYELIwN37NBG1I09uxaIqJD7GGqqpDXK5A3M6fdG-ES7P0OQk_UTw-IlAQJ3PLIXDdEi7o1FZKHshLUP09Mew=w2400" alt="radix sort"/>

<br>

- We start off by finding the maximum element in the unsorted input array (maxim). The number of digits (d) in maxim gives us the number of passes we need to run to get the fully sorted output.
  Here, the maxim = 455 and d = 3. This tells us that 3 passes will be required to fully sort the array
  The loop will run once for units place, once for the tens place, and once for hundreds place before the array is finally sorted.

- <br>

**Weaknesses:**

- Restricted inputs. Counting sort only works when the range of potential items in the input is known ahead of time.
- Space cost. As this algorithm will use a counting array to store elements for further sorting, it uses up extra memory space. If the range of potential values is big, then counting sort requires extra double space as that of the original array.

<br>

**Illustration of Counting Sort:**

The algorithm can be divided into two parts, first, we count how many times each item occurs, then we build the sorted output.

**Counting**
Say we have this array, and we know all numbers in the array will be non-negative integers less than or equal to 10:
