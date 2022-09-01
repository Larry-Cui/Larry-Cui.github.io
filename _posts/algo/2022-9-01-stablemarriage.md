---
layout: post
title: Stable Marriage Problem
date: 2022-09-01
tags:
  - Algorithms
header-includes:
  - \usepackage[ruled,vlined,linesnumbered]{algorithm2e}
---

## Introduction

According to [wikipedia](https://en.wikipedia.org/wiki/Stable_marriage_problem), the stable marriage problem (also stable matching problem or SMP) is the problem of finding a stable matching between two equally sized sets of elements given an ordering of preferences for each element.

The stable marriage problem has been stated as follows:

> Given n men and n women, where each person has ranked all members of the opposite sex in order of preference, marry the men and women together such that there are no two people of opposite sex who would both rather have each other than their current partners. When there are no such pairs of people, the set of marriages is deemed stable.

A matching is not stable if:

> When given a married pair, X-a and Y-b, if man X prefers b more than his current wife a and woman b prefers X more than her current man Y, then X-b is called a dissatised pair. X-b also has a very confusing name, the unstable pair, although they seem more stale than the currently matched pairs.

In other words, a matching is stable when there does not exist any pair which both prefer each other to their current partner under the matching.

For detailed discussion on the time complexity topic, please refer to [_The Stable Marriage Problem_ <i class="fa-sharp fa-solid fa-file-pdf fa-lg"></i>](https://drive.google.com/file/d/1vosbdHsUlBAKfXCYkRtHvNEiFelf1isr/view?usp=sharing) by William Hunt.

## Algorithm explained

In 1962, David Gale and Lloyd Shapley proved that, for any equal number of men and women, it is always possible to solve the SMP and make all marriages stable.

The Gale–Shapley algorithm (also known as the deferred acceptance algorithm) can be summarized as follows:

- Use the marriage as an example. We assume it's men that alwarys make the proposal, women can accept or reject it, but never propose back to men.
- each unengaged man proposes to the woman he prefers most (the one comes first on his waiting list), and at the same time delete this women from his waiting list.
- If the woman being proposed is unmatched, she accepts the proposal from the man. If the woman is already engaged, she checks her waiting list (no entry of the woman's waiting list will be deleted or changed, it keeps whole throughout the matching process): if the proposer comes after the man she already engaged, she turns down the proposal; if comes before, she drops the current man and accept the latter's offer.
- repeat above steps until all men and women are matched.

$n+1$

```algorithm
\begin{algorithm}[H]
\DontPrintSemicolon
\SetAlgoLined
\KwResult{Write here the result}
\SetKwInOut{Input}{Input}\SetKwInOut{Output}{Output}
\Input{Write here the input}
\Output{Write here the output}
\BlankLine
\While{While condition}{
instructions\;
\eIf{condition}{
instructions1\;
instructions2\;
}{
instructions3\;
}
}
\caption{While loop with If/Else condition}
\end{algorithm}
```

They presented an algorithm to do so

In quicksort, divide and compare happen before the fork. When the recursion goes down to the end, we only need to stitch individual elements back together. In mergesort, however, an array of elements is always divided equally without comparing. when the recursion goes down to the end, compare happens and stitch back with the designated order, ascending or descending.

<img style="display: inline-block; width: 100%; object-fit: cover;" src="" alt="insertion sort"/>
<div style="display: flex; align-items: flex-start; justify-content: center; font-size: 14px; color: #777;">Illustration of Mergesort</div>

<br>

## Code example

Here's the code in JavaScript for mergesort:

```js

```

Some notes to take here:

- before every fork, the array/sub-array has been divided equally into two sub-arrays without sorting, so the structure of the recursion is always a binary tree.
- when roll back from the leaves, `merge()` is working to compare(sort) and combine sub-arrays.
- the height of the binary tree is always $\log n$.

## Time complexity

The dividing part of the mergesort involves no comparison, so we can simply ignore it.

For the sorting and merging part from bottom up, we have $n/2$ comparing and sorting for each level. With a total of $\log n$ levels (height), the complexity is $n \log n$.

<br>
