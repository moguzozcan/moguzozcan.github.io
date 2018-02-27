---
title: "Finding Similar Items Notes From MMDS"
date: 2018-02-27
categories: 
  - Jekyll
---

A fundamental data-mining problem is to examine data for “similar” items.

Shingling:
Find textually similar documents by finding sets with a relatively large document.

Minhashing:
Compress data sets and still be able to deduce the similarity of the underlying sets.

Locality sensitive hashing:
Focus search on pairs that are most likely to be similar.

the similarity of sets by looking at the relative size of their intersection is called “Jaccard similarity.

Applications of Near-Neighbor Search

Jaccard Similarity of Sets
The Jaccard similarity of sets S and T is |S ∩ T |/|S ∪ T |, that is, the ratio of the size of the intersection of S and T to the size of their union. We shall denote the Jaccard similarity of S and T by SIM(S, T ).

Similarity of Documents
The aspect of similarity we are looking at here is character-level similarity, not “similar meaning,” which requires us to examine the words in the documents and their uses.

Some examples of near-neighbor searuchPlagiarism, Mirror Pages, Articles from the Same Source

Collaborative Filtering as a Similar-Sets Problem
A process whereby we recommend to users items that were liked by other users who have exhibited similar tastes.

The Jaccard similarity for bags B and C is defined by counting an element n times in the intersection if n is the minimum of the number of times the element appears in B and C. In the union, we count the element the sum of the number of times it appears in B and in C.

The bag-similarity of bags {a, a, a, b} and {a, a, b, b, c} is 1/3. The intersection counts a twice and b once, so its size is 3. The size of the union of two bags is always the sum of the sizes of the two bags, or 9 in this case.

Compute the Jaccard similarities of each pair of the following three sets: {1, 2, 3, 4}, {2, 3, 5, 7}, and {2, 4, 6}.

1 & 2 = {2, 3} / {1, 2, 3, 4, 5, 7} = 2 / 6
2 & 3 = {2} / {2, 3, 4, 5, 6, 7} = 1 / 6
1 & 3 = {2, 4} / {1, 2, 3, 4, 6} = 2 / 5

Compute the Jaccard bag similarity of each pair of the following three bags: {1, 1, 1, 2}, {1, 1, 2, 2, 3}, and {1, 2, 3, 4}
1 & 2 = {1, 1, 2} / {1, 1, 1, 2, 1, 1, 2, 2, 3} = 3 / 9
2 & 3 = {1, 2, 3} / {1, 1, 2, 2, 3, 1, 2, 3, 4} = 3 / 9
1 & 3 = {1, 2} / {1, 1, 1, 2, 1, 2, 3, 4} = 2 / 8


Shingling of Documents

k-Shingles
Suppose our document D is the string abcdabd, and we pick k = 2. Then the set of 2-shingles for D is {ab, bc, cd, da, bd}
Note that the substring ab appears twice within D, but appears only once as a shingle. A variation of shingling produces a bag, rather than a set, so each shingle would appear in the result as many times as it appears in the document. However, we shall not use bags of shingles here.

white space (blank, tab, newline,
etc.) is treated to replace any sequence of one or more white-space characters by a single blank.
