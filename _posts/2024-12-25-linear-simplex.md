---
layout: single
title: "LP Simplex"
categories: Mathematics
tag: [["Linear Algebra"], Optimization]
---


### Simplex

#### Assumptions:
We will develop the simplex algorithm for an LP in standard form
$$\text{minimize} ~~~~    c^{T}\mathbf{x}$$
$$ \text{subject to} ~~~~ A \mathbf{x} = \mathbf{b}, \mathbf{x} \geq 0 $$
where $A$ is $m \times n$

We assume that:
* $A$ has full row rank (no redundant rows)
* The LP is feasible
* All basic feasible solutions (i.e., extreme points) are nondegenerate

