---
layout: post
title: Heap Sort
date: 2022-08-31
tags:
  - Algorithms
---

Heap sort is based on a heap. What is a heap? simply put, it's a way of array order. As heap is not common to our daily life, it's worth to elaborate a bit about the structure of heap.

Heap is a binary tree of numbers, and it a complete one, the definiton/features of which include:

- nodes cannot have any child if their siblings are not filled yet;
- at the same level, if not all nodes are filled with children, then left-side nodes must be filled first;
- no child should be appended to any nodes until the nodes of the same level are filled with numbers.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/31mkKeg9OeglKgBvg5-BMSJ2vCx5L5iDKna1TEZ_rqlI_Z12fJyXhAujLXkq3MSP7QFSVf0AErnNAK4lnskFCNBAnemMmYPD0vIK5ipFDNgjZiJ6fKfydNAJpNgPpNZLjKgHF3KmxA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Complete and Non-complete Binary Tree Illustration</div>

<br>

You may have noticed the index order of the binary tree. It's top down and left to right. There's a mathematical connection between a node and its children. For the ease of calculation, we define the first (top) node of a binary tree at index 1.

**For node at index i:**

- left child at: $2i$
- right child at: $2i +1$

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/HIe-6tKQGQmaGpbeWDlVJDZBHWR7Jer0HboHhtWnRHoA99g0kqhebtV6rpZ_QJrNefbSaEIU92UB4ZEd2ozZNlhT4poI698aUZft4Gtyz6i-bQyZPgMXHvDrrQtv0fDGNmrcMNzApA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Index of a Heap Tree Illustration</div>

<br>

**For n number occupying an complete binary tree, its height of nodes:**

- $log_2 n$

Just as any sorted array can be in a ascending or descending order, so does a heap, but in a slight different way, i.e., max heap and min heap:

- In a max heap, every node is greater or equal than its children, while in a min heap, every node is less than its children.
- Nodes at the same level, siblings, are not necessarily in order.
- it's premitted that some children of one node is greater (in max heap) or less (in min heap) than their uncles.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/GKKmQdl8Awvr09vsgfebsfGGysmnvi3ZUvTWRaetU9twz3P5Rc_YI9_pQrxDVJL-OVz06-nepcpxidk1sc5Sz4gn_83NKIVJxX4yWUvBS0YQmkOR6jxNkfBg-fO59JJSNVSZwVNIsA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Min Heap (left) and Max Heap (right)</div>

<br>

**Heap is not for searching purpose!**

## Insert an element to a Heap

First of all, we record the elements of a heap in an array, in an order as describe above, i.e, starting with the top node as index 1 (or index 0 in JavaScript), then the second layer of nodes as index 2 and 3, then the third layer as index 4-7, and so on.

**Algorithem in normal language**
Let's use min heap as an example.

- We always start by adding the new element to the end of the array.
- Next, we compare the new element with its parent node, if the parent is greater than the new element, swap.
- Now the new element is in the swapped index, compare it with the upper parent again, swap by the same rule.
- If the new element is less than its parent, or it's already at the top node, insertion finishs.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/SbrcDlWdPtXXWdqJ_THOFYLeROkhtUzR_eTonF0CKKkZaTcK3X6a1wF3rYQyQ38-1bsxTUeig1rEwaMER_fG-ggxCSMAyx9nOFYRGBhTM2-4CeMDNIU4Bk95EmWxPIEYnA9vgUiL-A=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Inserting to a Min Heap Illustration</div>

<br>

<br>
