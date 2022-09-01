---
layout: post
title: Stable Marriage Problem
date: 2022-09-01
tags:
  - Algorithms
---

## Introduction

According to [wikipedia](https://en.wikipedia.org/wiki/Stable_marriage_problem), the stable marriage problem (also stable matching problem or SMP) is the problem of finding a stable matching between two equally sized sets of elements given an ordering of preferences for each element.

The stable marriage problem has been stated as follows:

> Given n men and n women, where each person has ranked all members of the opposite sex in order of preference, marry the men and women together such that there are no two people of opposite sex who would both rather have each other than their current partners. When there are no such pairs of people, the set of marriages is deemed stable.

A matching is not stable if:

When given a married pair, X-a and Y-b, if man X prefers b more than his current wife a and
woman b prefers X more than her current man Y, then X-b is called a dissatised pair. X-b also has a very confusing name, the unstable pair, although they seem more stale than the currently matched pairs.

For detailed discussion on the time complexity topic, please refer to _The Stable Marriage Problem_ () by William Hunt.

<i class="fa-brands fa-square-github fa-xl"></i>

- There is an element A of the first matched set which prefers some given element B of the second matched set over the element to which A is already matched, and
- B also prefers A over the element to which B is already matched.

In other words, a matching is stable when there does not exist any pair (A, B) which both prefer each other to their current partner under the matching.

## Algorithm explained

In quicksort, divide and compare happen before the fork. When the recursion goes down to the end, we only need to stitch individual elements back together. In mergesort, however, an array of elements is always divided equally without comparing. when the recursion goes down to the end, compare happens and stitch back with the designated order, ascending or descending.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/EIbh-aP55dd4uCU2fMlWrBc2IkVW31HUUh0pGZfdtt2CAk7HI66xSOirdAI6BZz5tO-LWFEqCIduZeeIoLvIt7NOpBosgZ1hwra7u12_MMmuLWPjqMsuEhDzlYrx-2Cu1jk4fER_-g=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Illustration of Mergesort</div>

<br>

## Code example

Here's the code in JavaScript for mergesort:

```js
/* ************************* */
// Mergesort recursion code
/* ************************* */

function mergeSort(array) {
	const length = array.length;

	// roll back condition:
	// if a sub-array's length is equal to or less than 1,
	// we are at the leaves of the binary tree.
	if (length <= 1) return array;

	// partitioning of the array/sub-array
	// the array/sub-array haven't been sorted yet
	const mid = Math.floor(length / 2);
	const sortedLeftArray = mergeSort(array.slice(0, mid));
	const sortedRightArray = mergeSort(array.slice(mid));

	// here below is the sorting and merging process
	// when the recursion reach the end of leaves and roll back
	// the program will continue as below

	// we define a merge function first
	function merge(sortedLeftArray, sortedRightArray) {
		let result = [];

		// by combining push() and shift(), elements
		// in left and right arrays are extracted and pushed to result

		while (sortedLeftArray.length && sortedRightArray.length) {
			// when array lenght = 0, bolean value would be false!!!

			if (sortedLeftArray[0] < sortedRightArray[0]) {
				result.push(sortedLeftArray.shift());
			} else {
				result.push(sortedRightArray.shift());
			}
		}

		/* Either left/right array will be empty or both */
		return [...result, ...sortedLeftArray, ...sortedRightArray];
	}

	// we call the merge function //
	// merge() function constructs sorted array/sub-array,
	// but it needs to be returned to
	// above place where the mergeSort() is called to be
	// further compared and merged.
	return merge(sortedLeftArray, sortedRightArray);
}
```

Some notes to take here:

- before every fork, the array/sub-array has been divided equally into two sub-arrays without sorting, so the structure of the recursion is always a binary tree.
- when roll back from the leaves, `merge()` is working to compare(sort) and combine sub-arrays.
- the height of the binary tree is always $\log n$.

## Time complexity

The dividing part of the mergesort involves no comparison, so we can simply ignore it.

For the sorting and merging part from bottom up, we have $n/2$ comparing and sorting for each level. With a total of $\log n$ levels (height), the complexity is $n \log n$.

<br>
