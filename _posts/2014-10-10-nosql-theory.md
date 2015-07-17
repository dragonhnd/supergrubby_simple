---
layout: article
title : "NoSQL的理论基础"
date: 2014-10-10 16:27:31
categories: hack
---

NoSQL
=====

###CAP###

- Consistency
- Availability
- (Tolerance of network) Partition

####Practice####

1. k-v store (apply CAP)
2. domain model + distributed cache + storage

different kinds of data - different kinds of consistency

###Eventual Consistency###

No matter what the process can be, the result should be consistent at last.

1. Strong Consistency - always get the latest
2. Weak Consistency - Non-consistent window
3. Eventual consistency - A write, no other writing, get what A wrote

non-consistent window - interaction dealy, load average, number of replica. DNS.

###BASE###

- Basacally avalible
- Soft-state (Non-connection)
- Eventual Consistentcy

shard failure
partly inconsistent

####Practice####
1. Storage based on function
2. sharding fragment

####I/O 5 Minutes
####Don't delete data
	1. Soft deletion
	2. Hard deletion
	3. Specified state field (Effective, abandon, stop...)
####RAM is harddisk, harddisk is tape
IMDG
####Amdahl law & Gustafson law
S(n) = 1/(K+(1-K)/n) = n/(1+(n-1)K)
S(n) = K+(1-K)n
