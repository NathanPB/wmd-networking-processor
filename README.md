# WheresMyDuo Networking Processor Specification v1.0.0

## Target
The target of the Networking Processor Module is to process thousands of different WheresMyDuo Gaming Profiles per second and find the ones who are promising about social interaction based in pre-defined conditions.

## How
Since performance **is** a problem in this context, I analyzed benchmarks and paradigms and found the best way of dealing with this problem for now: Functional Programming.

### Why Functional Programming
Functional Programming is a programming paradigm inspired on **math**. The basic job of the WMD Networking Processor module is to compare different **data sets** and find relation between them, or in other words, **union theory**.

### Haskell
After analyzing some benchmarks of programming languages on common programming tasks, Haskell got my attention on some points:

- **Functional:** Haskell is a purely functional programming language, that means it fits perfectly with the initial condition of having process based on math theories.

- **Fast:** The most of the Haskell benchmarks shows that the Haskell performance is as good as as C's performance when compiled using GHC (Glasgow Haskell Compiler), and in some cases, it can be **even faster**.

- **Multicore:** Haskell has a fantastic Multicore implementation, thats one of the reasons why sometimes can be faster than C.

#### Benchmarks
All the benchmarks are done using an **Intel Core i5 8250u** CPU running on OpenSuse Tumbleweed (Linux 5.3.8-1 kernel) and the following compiler versions:
 - Java(TM) SE Runtime Environment (build 1.8.0_201-b09)
 - gcc (SUSE Linux) 9.2.1 20190903 [gcc-9-branch revision 275330]
 - Glasgow Haskell Compiler, Version 8.6.5, stage 2 booted by GHC version 8.4.3
 - GNU bash, version 5.0.11(1)-release (x86_64-suse-linux-gnu)

![Benchmarks](./benchmarks.png)