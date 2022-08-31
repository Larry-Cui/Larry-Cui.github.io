---
layout: post
title: Heap Sort
date: 2022-08-31
tags:
  - Algorithms
---

Heap sort is based on a heap. What is a heap? simply put, it's a way of array order. As heap is not common to our daily life, it's worth to elaborate a bit about the structure of heap.

Heap is a binary tree of numbers, and it a complete one, the definiton/features of which include:

- all upper level nodes have children;
- at the same level, if not all nodes are filled with children, then left-side nodes must be filled first;
- no child should be appended to any nodes until the nodes of the same level are filled with numbers.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="https://lh3.googleusercontent.com/31mkKeg9OeglKgBvg5-BMSJ2vCx5L5iDKna1TEZ_rqlI_Z12fJyXhAujLXkq3MSP7QFSVf0AErnNAK4lnskFCNBAnemMmYPD0vIK5ipFDNgjZiJ6fKfydNAJpNgPpNZLjKgHF3KmxA=w2400" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Complete and Non-complete Binary Tree Illustration</div>

<br>

You may have noticed the index order of the binary tree. It's top down and left to right. There's a mathematical connection between a node and its children. For the ease of calculation, we define the first (top) node of a binary tree at index 1.

**For node at index i:**

- left child at: 2\*i
- right child at: 2\*i+1

**For n number occupying an complete binary tree, its height of nodes:**

- $log_2 n$

Just as any sorted array can be in a ascending order or descending order, so does a heap, but in a slight different way, i.e., max heap and min heap.

**Heap is not for searching purpose!**

<br>
