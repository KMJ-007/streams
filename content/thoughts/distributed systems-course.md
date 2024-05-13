---
title: distributed systems-course
date: 2024-05-04
tags:
  - seed
enableToc: false
---
https://www.youtube.com/playlist?list=PL5aMzERQ_OZ9j40DJNlsem2qAGoFbfwb4

## Week 1 : Introduction to Assembly language and Basics of Concurrency - Part 1

1. Understanding assembly
2. writing a data structure in assembly
3. Understanding Concurrency with Rust:
    - Explore advanced techniques for building highly concurrent applications in Rust.
    - Discover synchronization primitives such as mutexes, condition variables, and atomic types.
    - Learn how to leverage concurrency patterns like channels and message passing to coordinate tasks.
4. Understanding Amdahl’s and Gustafson’s Law
5. Introduction to message passing

## Week 2 : Diving deep into Concurrency - Part 2

1. Non blocking Data structures
    1. Understanding various Non blocking Data Structures
    2. ABA problem
    3. Solutions to ABA problem
2. Hands on Implementation of non-blocking trieber stack

## Week 3 : Work stealing

1. Understanding work stealing and its application in concurrent computing.
2. Implementing a work-stealing queue in Rust.
3. Exploring work stealing in the context of the JVM.

## Week 4 : Introduction to GPU Programming

1. Understanding GPU architecture
2. Introduction to CUDA

## Week 5: Introduction to Distributed Systems - Part 1

Overview of Distributed Systems:

1. Introduction to the concept of distributed systems and their importance in modern computing.
    1. Understanding the key characteristics and benefits of distributed systems.
    2. Examples of distributed systems in real-world applications, such as cloud computing, content delivery networks, and social media platforms. Distributed System Models and Architectures:
2. Exploring different architectural models for distributed systems, including:
    1. Client-server model: Understanding the roles and interactions between clients and servers.
    2. Peer-to-peer model: Exploring the decentralized nature of peer-to-peer systems.
    3. Exploring distributed computing paradigms, including message passing, remote procedure calls (RPC), and publish-subscribe systems.
3. CAP Theorem and Data Consistency:
    - Introducing the CAP theorem (Consistency, Availability, and Partition tolerance) and its significance in distributed systems.
    - Exploring different consistency models, such as strong consistency, eventual consistency, and causal consistency.
    - Discussing the trade-offs between consistency and other system properties.
4. Understanding Map reduce research paper

## Week **6: Diving deep into Distributed Systems - Part 2**

1. Clocks and Time in Distributed Systems:
    - Understanding the challenges of time synchronization in distributed systems.
    - Logical Clocks - Lamport and Vector
    - Proof of Vector Clocks
    - Reading Time, Clocks and Order research paper from Leslie Lamport
2. Understanding Google Spanner research paper

## Week **7 : Consensus Algorithms and Introduction to TLA+, Distributed Systems - Part 3**

1. Understanding Consensus
    1. Introduction to consensus algorithms and their role in achieving fault tolerance in distributed systems.
    2. Exploring the RAFT algorithm as a popular consensus algorithm.
    3. Understanding the basic principles and components of the RAFT algorithm.
    4. Discussing the implementation of the RAFT algorithm.
    5. comparing Paxos with RAFT

## Week **8:** Fault Tolerance and Distributed Transactions - Part 4

1. Introduction to Fault Tolerance:
    - Exploring the concept of fault tolerance in distributed systems and why it's crucial for ensuring system reliability.
    - Understanding common types of faults, including hardware failures, network issues, and software errors.
2. Replication and Redundancy:
    - Discussing the role of replication and redundancy in achieving fault tolerance.
    - Exploring different replication strategies, such as primary-backup, active-passive, and active-active.
    - Examining the trade-offs and challenges associated with replication.
3. Understanding Distributed transactions
4. Distributed Transactions and Consistency:
    1. Exploring distributed transactions and their role in maintaining data consistency in fault-tolerant systems.
    2. Discussing two-phase commit (2PC), three-phase commit (3PC), and other approaches to distributed transaction management.