---
title: Issues of Alignment
---

All machine architectures have *data alignment* requirements, or called *alignment of memory*. As we all know, the data 
stored in memory is in byte-sized. But our processors, do not read and write from memory in byte-sized chunks. Instead, 
processors access memory with a specific granularity, such as 2, 4, 8, or 16 bytes. SO, the binary data written with one 
application may not be readable by a different application, or even by the same application on a different machine.

### Why we should concern about alignment

Normally, the compiler naturally aligns all data. So for most of programmers, they needn't concern about it. while for 
system programmers, dealing with structures, performing memory managment by hand, saving binary data to disk, and comm
unicating over a network may bring alignment issues to the forefront. Therefore, we should be well versed in issues of 
alignment.

### 
