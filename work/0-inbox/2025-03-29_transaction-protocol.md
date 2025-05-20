---
aliases:
  - transaction protocol
tags:
  - SQL
  - DB
title: transaction-protocol
---

# transaction protocol

A transaction is single unit of work that interacts with the DB, possibly altering it's contents. Inside a single transaction we can perform multiple changes in the DB, by encapsulating all of them, we can say that they all occur or non of them occur.

# The ACID principles

- Atomicity: Ensures that a group of related alternating all occur, or none of them occur.
- Consistency: since we are committing the changes, the DB moves from consistent state to consistent state
- Isolation: Multiple transactions can occur concurrently, i.e, while one user interact with the DB, another user won't see their changes until commit
- Durability: Once a transaction has been committed it's effect are permanent on the DB. The way the system is logging the changes pre-commit ensures that after the commit is performed even a power loss won't unroll this changes.

# Limitations

Basically this extra layer of features (kind of a version control) has some overhead, leading to more resource allocation. In the worst-case scenario poorly designed transactional system can lead to `deadlocks` (when two processes wait for each other indefinitely)

1. Why are you looking for a new job opportunity?
   I'm looking to transition from data science to software development because I’ve realized that what excites me most is building robust, maintainable systems and solving engineering problems at scale. In my current role, I found myself gravitating toward the engineering side of projects—developing data pipelines, optimizing performance, and working on backend systems. I want to move into a role where I can focus fully on software development and continue growing in that direction.

2. What kind of job are you looking for?
   I'm looking for a software development role on a team that values engineering best practices like testing, version control, and clean architecture. I want to work in an environment where I can continue learning from experienced developers, contribute to well-structured systems, and deepen my skills in systems programming and backend development.

3. What was the scope of your most recent project (technologies, tasks, etc.)?
   My most recent project was a proof of concept for a multi-camera person identification and tracking system, inspired by the MICRO-TRACK research paper. I implemented the full pipeline in Python, using multiprocessing to handle multiple video streams in parallel. For the vision components, I used YOLO for real-time person detection and a Vision Transformer (ViT) model implemented in PyTorch for cross-camera re-identification. The project focused on validating the research approach by building a modular, testable architecture and adapting the original methodology to real-world video data. I worked on optimizing inter-process communication, tuning the Re-ID model, and ensuring identity consistency across camera views. This PoC helped me strengthen my skills in deep learning with PyTorch, computer vision, and scalable system design.

4. What technologies/tools/frameworks do you master?
I started by improving an older Python codebase for a CRUD-style web application (with some AI component), with a FastAPI backend and a React frontend. As part of this work, I introduced extensive type hints to take full advantage of static analysis tools like mypy and ruff, which greatly improved code quality and maintainability. On the backend, I worked with NoSQL databases, primarily MongoDB and its Azure-managed equivalent, CosmosDB. I’ve used Docker extensively for containerizing and deploying web applications, and I’m comfortable setting up multi-container environments. I also have hands-on experience with Azure—particularly in debugging deployed systems, using logging utilities, and monitoring applications through Azure Metrics and Application Insights. 

5. When could you start a new assignment?
I need to give 1-month notice to my current company.

6. What would be your preferred work location: Porto, Braga or Lisbon?
I'm based in Lisbon, so the Lisbon office would be my primary option.

