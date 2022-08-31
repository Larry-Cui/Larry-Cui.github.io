---
layout: post
title: Heap Sort
date: 2022-08-31
tags:
  - Algorithms
---

**Table of Contents:**

- [Definition and categories of heaps](#definition-and-categories-of-heaps)
	- [index and height of a heap](#index-and-height-of-a-heap)
	- [Max and min heaps](#max-and-min-heaps)
- [Insert an element to a heap](#insert-an-element-to-a-heap)
	- [Algorithem in normal language](#algorithem-in-normal-language)
	- [Code example](#code-example)
	- [Time complexity of heap insertion](#time-complexity-of-heap-insertion)
- [Create a heap](#create-a-heap)
	- [Time complexity](#time-complexity)
- [Deleting from Heap](#deleting-from-heap)

## Definition and categories of heaps

Heap sort is based on a heap. What is a heap? simply put, it's a way of array order. As heap is not common to our daily life, it's worth to elaborate a bit about the structure of heap.

Heap is a binary tree of numbers, and it a complete one, the definiton/features of which include:

- nodes cannot have any child if their siblings are not filled yet;
- at the same level, if not all nodes are filled with children, then left-side nodes must be filled first;
- no child should be appended to any nodes until the nodes of the same level are filled with numbers.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/31mkKeg9OeglKgBvg5-BMSJ2vCx5L5iDKna1TEZ_rqlI_Z12fJyXhAujLXkq3MSP7QFSVf0AErnNAK4lnskFCNBAnemMmYPD0vIK5ipFDNgjZiJ6fKfydNAJpNgPpNZLjKgHF3KmxA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Complete and Non-complete Binary Tree Illustration</div>

<br>

### index and height of a heap

You may have noticed the index order of the binary tree. It's top down and left to right. There's a mathematical connection between a node and its children. For the ease of calculation, we define the first (top) node of a binary tree at index 1.

**For node at index i:**

- left child at: $2i$
- right child at: $2i +1$

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/HIe-6tKQGQmaGpbeWDlVJDZBHWR7Jer0HboHhtWnRHoA99g0kqhebtV6rpZ_QJrNefbSaEIU92UB4ZEd2ozZNlhT4poI698aUZft4Gtyz6i-bQyZPgMXHvDrrQtv0fDGNmrcMNzApA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Index of a Heap Tree Illustration</div>

<br>

**For n number occupying an complete binary tree, its height of nodes:**

- $\log_2 n$

### Max and min heaps

Just as any sorted array can be in a ascending or descending order, so does a heap, but in a slight different way, i.e., max heap and min heap:

- In a max heap, every node is greater or equal than its children, while in a min heap, every node is less than its children.
- Nodes at the same level, siblings, are not necessarily in order.
- it's premitted that some children of one node is greater (in max heap) or less (in min heap) than their uncles.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/GKKmQdl8Awvr09vsgfebsfGGysmnvi3ZUvTWRaetU9twz3P5Rc_YI9_pQrxDVJL-OVz06-nepcpxidk1sc5Sz4gn_83NKIVJxX4yWUvBS0YQmkOR6jxNkfBg-fO59JJSNVSZwVNIsA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Min Heap (left) and Max Heap (right)</div>

<br>

**Heap is not for searching purpose!**

## Insert an element to a heap

First of all, we record the elements of a heap in an array, in an order as describe above, i.e, starting with the top node as index 1 (or index 0 in JavaScript), then the second layer of nodes as index 2 and 3, then the third layer as index 4-7, and so on.

### Algorithem in normal language

Let's use min heap as an example.

- We always start by adding the new element to the end of the array.
- Next, we compare the new element with its parent node, if the parent is greater than the new element, swap.
- Now the new element is in the swapped index, compare it with the upper parent again, swap by the same rule.
- If the new element is less than its parent, or it's already at the top node, insertion finishs.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/SbrcDlWdPtXXWdqJ_THOFYLeROkhtUzR_eTonF0CKKkZaTcK3X6a1wF3rYQyQ38-1bsxTUeig1rEwaMER_fG-ggxCSMAyx9nOFYRGBhTM2-4CeMDNIU4Bk95EmWxPIEYnA9vgUiL-A=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Inserting to a Min Heap Illustration</div>

<br>

### Code example

Now let's try code the algorith of heap insertion by JavaScript. Here we're using a technique called recursion, and also be noted that this is a max heap.

```js
// Heap Insertion

// we need a swap function
const swap = (arr, a, b) => {
	const temp = arr[a];
	arr[a] = arr[b];
	arr[b] = temp;
};

// recursive coding
const insertRecur = (array, index, n) => {
	// since JavaScript array starts from 0, we need some adjustment
	const parentNodeIndex = Math.floor((index - 1) / 2);

	// roll back condition of the recursion
	if (array[parentNodeIndex] >= n || index === 0) return array;

	swap(array, parentNodeIndex, index);
	index = parentNodeIndex;

	// recursion bichotomy point
	insertRecur(array, index, n);
};

// with swap and insertRecur function
// we only need to pass info and call these functions
const insertHeap = (array, n) => {
	array.push(n);
	const index = array.length - 1;
	insertRecur(array, index, n);
	return array;
};
```

### Time complexity of heap insertion

The insertion procedure takes at most as many steps as the height of the heap binary tree, so the time complexity is $\log n$ (short for $\log_2 n$).

## Create a heap

After we know how to insert new element to a heap, it comes intuitively that we can create a heap by inserting elements to a new array one by one. As a matter of fact, if we are given an un-ordered array and asked to create a heap using these element, we can work within the same array and do some compare and swap jobs as insertion algorithm demands.

Here below is the code practice for creating a heap. For ease of reference, I use a new array instead of working on the origianl one.

```js
// Create a heap array
// we are re-using insertHeap function from above

const heapArray = (n) => {
	const array = new Array();
	for (let i = 0; i < n; i++) {
		// here we use numbers by random funtion,
		// we can of course use other sources.
		let element = Math.round(Math.random() * n * 3);

		insertHeap(array, element);
	}
	return array;
};
```

### Time complexity

If we observe from the stand point of the last element, it takes at most $\log n$ steps to insert to the heap. As we have $n$ elements in total, so the worst scenario is $n \log n$.

## Deleting from Heap

It seems opposite to intuition, but the rule of heap deleting is, you can only delete the root element. In max heap, this is the largest element, in min heap, the smallest.

The procedure of the algorithm goes as follows (max heap):

- delete the first element (root) from the heap array
- now move the last element of the heap array to the root position, which is at index 0 in JavaScript
- compare root's two children, find the larger one, and swap position of the larger one with the root element if the child is larger than the root element (Remember: the root element is the element swapped from the last position of the array)
- go all way down with the root element, until it's larger than its children.

<br>

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/AjqdbpX0Po2EwlLfYuzkqWxD9tqpISHy3kKMTFHT_XZWmJRY82DZz7FbhSFRj6DNUoZjpgjTPoBvOygogOaMapRJzYDZdqBllrgURFIBuM1ZB1aL16l8dH2ytUbuu301XhUPLRHJIA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Step 1: "21" is the last of the heap array</div>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Step 2: delete "45", and move "21" to the root position</div>

<br>

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/X5Uo8tmqD0gIzyeUm4kah93zWuk8yxVCLzUdCwoGKRUIWnhLZfEii8z8H2IqRCSDtLXsuDGKE-hq0-q6xhK55z4nsbSAHi-szEJk601wG_OFkg3Q8G82ZStfAbroBQMNgiJ3GgZrxg=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Step 3: compare children of "21", "42" is larger than "23", so swap "42" with "21"</div>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Step 4: repeat step 3, child "35" is larger than "27", swap "35" with "21"</div>

<br>

After step 4, "21" has no child, we can stop the procedure, the new heap array is sorted.

Code practice here in JavaScript.

```js
// swap function is here to help swap elements
const swap = (arr, a, b) => {
	const temp = arr[a];
	arr[a] = arr[b];
	arr[b] = temp;
};

// we use recursive again!
// the array this heapify function takes in
// is a heap array except the first element swapped from the last
function heapify(arr, i) {
	// because JavaScript array starts from 0
	// left child is 2 * ( i + 1 ) - 1 = 2 * i + 1
	// right child is 2 * (i + 1 ) + 1 - 1 = 2 * i + 2
	let l = 2 * i + 1;
	let r = 2 * i + 2;

	// roll back conditions for heapify recursive function
	if ((arr[i] > arr[l] && arr[i] > arr[r]) || r > arr.length - 1) return arr;

	// compare child first, then use the larger child to compare with parent
	if (arr[l] > arr[r]) {
		if (arr[l] > arr[i]) {
			swap(arr, l, i);
			i = l;
		}
	} else {
		if (arr[r] > arr[i]) {
			swap(arr, r, i);
			i = r;
		}
	}

	// Recursively heapify the affected sub-tree
	// notice "i" has been changed to its child node index
	heapify(arr, i);
}

// Function to delete root and
// send array to heapify for further process
function deleteRoot(arr) {
	// get the root
	const root = arr[0];

	// splice comes back with an array,
	// so we need to get the number out of it
	arr[0] = arr.splice(-1, 1)[0];

	// heapify(sort) the array
	heapify(arr, 0);

	// return heapified array and the deleted root
	console.log("Deleted root is: " + root);
	return arr;
}
```

<br>
