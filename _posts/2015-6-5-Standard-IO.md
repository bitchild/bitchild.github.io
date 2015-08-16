---
title: Standard I/O Learning
---

> Under  normal circumstances every UNIX program has three streams opened for it when it starts up, one for input, one for output,  and  one  for printing diagnostic or error messages.

### Important Functions

The following funcs are very common and more important than others.
  
  * `int		fflush(FILE *);`
  * `int		fgetc(FILE *);`
  * `char		*fgets(char *, int, FILE *);`
