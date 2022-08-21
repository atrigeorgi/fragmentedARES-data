# fragmentedARES-data
 
This repository contains all the collected raw data from the experiments of the paper “Fragmented ARES: Dynamic Storage for Large Objects”. 
The link to the arXiv version of the paper is https://arxiv.org/abs/2201.13292. 

## Table of Contents  
[Folders’ Description](#Folders)  
[Different types of log files](#DifferentLogs)

## Folders’ Description

There are two separate folders, one that contains the results of experiments carried out using the AWS testbed, and the other, the experiments carried out on Emulab testbed, AWS_logs and Emulab_logs, respectively. These two main folders contain subfolders named with the titles of the experimental scenarios in the above paper. 
The two main folders have common scenarios, thus subfolders.  

**Performance VS. Initial File Sizes**: This folder contains a subfolder for each algorithm. The subfolder name has the pattern filesizeBig_fast + the name of the algorithm. In Emulab_logs there are two different subfolders for vmwARES_EC and its fragmented variant, each with different number in their name; this number is the parity value. At the end of each .log filename there is some number, e.g., 1048576_6-1-1_1. The first number is the filesize, the next three numbers define the number of servers, writers, and readers, and the last number is the iteration number. 

**Performance VS. MinAvg Block Sizes**: This scenario contains subfolders only for the fragmented version of the algorithms. At the end of each .log filename there is some number, e.g., 2097152_4194304_6-1-1_1. The first two numbers are the minimum and maximum block sizes, the next three numbers define the number of servers, writers, and readers, and the last number is the iteration number. 

**Performance VS. MinAvgMax Block Sizes**: This scenario contains subfolders only for the fragmented version of the algorithms. At the end of each .log filename there is some number, e.g., 16777216_33554432_6-1-1_1. The first two numbers are the minimum/average and maximum block sizes, the next three numbers define the number of servers, writers, and readers, and the last number is the iteration number. 

**Performance VS. Scalability**: This folder contains subfolders for all algorithms. At the end of each .log filename there is some number, e.g., 11-10-5-0_1. The first four numbers define the number of servers, writers, readers, and reconfigurers, and the last number is the iteration number. 
 
The Emulab_logs folder has three extra scalability scenarios that have reconfigurartions.  
Reconfiguring to a different number of servers 
Reconfiguring to a random DAP 
Reconfiguring to the same DAP 
These folders contain subfolders for ARES variants. At the end of each .log filename there is some number, e.g., 11-10-5-1_1. The first four numbers define the number of servers, writers, readers, and reconfigurers, and the last number is the iteration number. 

## Different types of log files

There are .log files starting with ’user’ and .log files starting with ’client’.  
According to our architecture there is the user level, where a client can pass command through our command-line interface. The log files starting with ’user’ record information from this system level. Subsequently, the requested commands are executed to the Distributed Shared Memory Module (DSMM). The log files starting with ‘client’ record information from the level of DSM Client. 

 ![architecture](https://user-images.githubusercontent.com/15169270/185813247-ddbbadb7-bd56-4bc4-8971-cb86de896b3d.png)

For our experimental results, we use the ’user’ files. Also, we do not consider the logs ending in phase1 in our results since they are files from the bootstrap phase. We also do not consider the files ending with read_file since they are files from an extra phase at the end, where we do a last read operation to get some statistics of the last generated object. 
 
