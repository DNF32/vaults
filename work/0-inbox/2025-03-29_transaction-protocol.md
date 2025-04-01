---
aliases:
  - transaction protocol
tags:
  - SQL
  - DB
title: transaction-protocol
---

# transaction protocol

A transation is single unit of work that interacts with the DB, possibly altering it's contents. Inside a single transaction we can performe multiple changes in the DB, by encapasulating all of them, we can say that they all occur or non of them occur.

# The ACID principles

- Atomicity: Ensures that a group of related alterating all occur, or none of them occur.
- Consistency: since we are comming the changes, the DB moves from consistent state to consistent state
- Isolation: Multiple transactions can occur concurrently, i.e, while one user interact with the DB, another user won't see their changes until commit
- Durability: Once a transaction has been committed it's effect are permanent on the DB. The way the system is logging the changes pre-commit ensures that after the commit is performed even a power loss won't unroll this changes.

# Limitations

Basically this extra layer of features (kind of a version control) has some overhead, leading to more resource allocation. In the worse case scenario poorly designed transactional system can lead to `deadlocks` (when two processes wait for each other indefinitely)
