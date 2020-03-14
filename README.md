# WheresMyDuo Networking Processor Specification

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

## How it Works
The main process of this module is given a raw GamingProfile on its input and a base GamingProfile to make the comparisons, it will compare the Tags and Hours fields.

### Input Layer
The gaming profile that the other ones will be compared with should be given via command line parameters:
```
    --tags 4390119fcd7f,6cd79977bcf8
    --hours 7,8,9,10
```

The list elements must be separated by a single ``,`` (comma).


The Gaming Profiles to be compared with the base one should be given via ``stdin``, separated by Unix Line Break (``/n``, byte ``0x0A``). ETX (``0x03``) means that there is no more profiles to input.

The input data must follow the **Gaming Profile Model**.

#### Gaming Profile Model
```
<12 bytes profile ID>, [Tag 0 (12 bytes)] ... [Tag n], [Hour 0] ... [Hour 23]
```

Each argument should be separated by ``, `` (comma followed by blank space), and each element of the tag list should be separated by a single blank space.

The Hours are formed by a 256 bit hexadecimal unsigned big-endian integer (16 hexadecimal characters). The state of the *n*th bit means that the *n*th hour of the week is marked as an available hour to the user to play. The left zeroes can be omitted.

E.g:
```507f1f77bcf8, 6cd799439011 72f81d9fcd7f, 40000F```

The example above means a profile with:
 - Id: ``507f1f77bcf8``
 - Tags: ``6cd799439011`` and ``72f81d9fcd7f``
 - Hours: ``0``, ``1``, ``2``, ``3`` and ``23``