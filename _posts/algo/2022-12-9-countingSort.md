---
layout: post
title: Counting Sort
date: 2022-12-9
tags:
  - Algorithms
---

This post is based on two posts by [Geeksforgeeks](https://www.geeksforgeeks.org/counting-sort/) and [interviewcake](https://www.interviewcake.com/concept/java/counting-sort).

First thing first, what's counting sort?

> Counting sort is a sorting technique based on keys between a specific range. It works by counting the number of objects having distinct key values (a kind of hashing). Then do some arithmetic operations to calculate the position of each object in the output sequence.

<br>
**Characteristics of counting sort:**

- Counting sort makes assumptions about the data, for example, it assumes that values are going to be in the range of 0 to 10 or 10 – 99, etc, Some other assumption counting sort makes is input data will be all real numbers (or some items like inventory stocks that can be represented by real numbers).
- Unlike other algorithms this sorting algorithm is not a comparison-based algorithm, it hashes the value in a temporary count array and uses them for sorting. Because of this characteristic, counting sort runs in $O(n)$ time, making it asymptoticaly faster than comparison-based sorting algorithms like [quicksort](https://larry-cui.github.io/quicksort) or [mergesort](https://larry-cui.github.io/mergesort).
- It uses a temporary array making it a non-[In Place algorithm](https://www.geeksforgeeks.org/in-place-algorithm/).

<br>
**Weaknesses:**

- Restricted inputs. Counting sort only works when the range of potential items in the input is known ahead of time.
- Space cost. As this algorithm will use a counting array to store elements for further sorting, it uses up extra memory space. If the range of potential values is big, then counting sort requires double the space that the original array takes.

<br>
**Illustration of Counting Sort:**

Say we have this array:

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://drive.google.com/drive/u/0/folders/1K0tR9qp_bydYEEvUMlbzk6SOZmwPGIKo" alt="counting sort"/>

<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Illustration of Selection Sort</div>

Below is the implementation of the algorithm, we use recursion again:

```js
// swap function
const swap = (arr, a, b) => {
	const temp = arr[a];
	arr[a] = arr[b];
	arr[b] = temp;
};

// recursion realization of the selection sort
const selectRecur = (array, n) => {
	if (n === array.length) return array;

	for (let i = n; i < array.length; i++) {
		if (array[n] > array[i]) swap(array, n, i);
	}

	return selectRecur(array, n + 1);
};

// we test by a random array
const arr = [12, 10, 9, 7, 8, 5, 3, 4, 7, 7, 4, 3, 2, 1, 0, 2];
console.log(selectRecur(arr, 0));
```

<br>
