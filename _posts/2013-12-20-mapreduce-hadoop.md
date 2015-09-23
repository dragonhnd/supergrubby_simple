---
title: "MapReduce & Hadoop"
date: 2013-12-20 15:22:31
description: Notes about MapReduce and Hadoop
---
MapReduce - distribute computation/parallel programming

DataVolume -> Large-scale Computing

Copy data over network consuming time -> MapReduce

* Bring computation close to data -> MapReduce
* store files multiple times for reliability -> HDFS/GFS


##HDFS
* failure among machines
* scale and failure of large clusters


###HDFS

* Distributed File System
* Global file namespace
* Repilca to ensure data recovery


**core arch** - detection faults, automatic recovery

###Data Characteristics

* Streaming data
* Batch processing
* Write once read many


###Master/slave arch

* NameNode as master -> namesapce for data storage in files
* DataNode as slave -> files splited
* Namenode stores meta-data(c, r, m, rn, etc), the number of replicas


###Data Replication

* File -> sequence of blocks(same size except the last one)
* Fault tolerance
* Size configurable
* DataNode (HeartBeat, BlockReport - all blocks)-> NameNode
* minimize bandwidth consumpution and latency -> Reader node, local data center preferred
* NameNode check DataNode with acceptable number of replicas, if not-> **SafeMode**


###Filesystem MetaData###

* EditLog(in NameNode) to record changes of metadata
* Keep image of entire file system ns
* startup -> Gets FsImage & EditLog -> Update FsImage with EditLog -> Sotes a copy of FsImage as a checkpoint
* last checkpoint recovered when crash


###DataNode
* block - separate file
* placed in different directories
* creation determined by heuristics
* starup -> generate Blockreport -> send to NameNode


##MapReduce

* Read data sequentialy
* Map - extract
* Sort and Shuffle - group by key
* Reduce - Aggregate, summarize, filter or transform
* Write


* M Map tasks, larger than number of nodes, 1 chunk/map -> improve dynamic load balancing and speeds up recovery
* R Reduce tasks, smaller than M usually


###Data Flow

* DataNode server - computation server
* input and final output stored in distributed FS, near the input location
* intermediate results soted on local FS of Map and Reduce Workers


###Coordination

* Master Node - coordination
* Task status - idle, in-progress, completed
* idle tasks -> availbale worker
* map task completed (location, sizes of R intermediate files) -> Master -> Reducer
* Master ping workers periodically to detect fails


###Failure

* Map Task - completed and i-p Map tasks -> idle -> notice Reduce worker them rescheduled
* Reudce Task - i-p ->idle -> restarted
* Master Failure -> task aborted and notify the client


###Refinement

* pre-aggregating values in mapper
* partiation function - Hash mod R
