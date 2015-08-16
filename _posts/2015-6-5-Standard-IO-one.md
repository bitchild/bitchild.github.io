---
title: Standard I/O Learning (一)
---

> Under  normal circumstances every UNIX program has three streams opened for it when it starts up, one for input, one for output,  and  one  for printing diagnostic or error messages.

### Important Functions

The following funcs are very common and more important than others.
  
  * `int      fclose(FILE *);`
  * `int		  fgetc(FILE *);`
  * `int      fputc(int, FILE *);`
  * `char		  *fgets(char *, int, FILE *);`
  * `int      fputs(const char *, FILE *);`
  * `char     *gets(char *);`
  * `int      getc(FILE *)`
  * `int      putc(int, FILE *);`
  * `int      putchar(int);`
  * `int      puts(const char *);`
  * `int      scanf(const char *, ...);`
  * `int      printf(const char *, ...);`
  * `int		  fflush(FILE *);`
  * `void     rewind(FILE *);`
  * `void     setbuf(FILE *, char *);`
  
Because here we just talking about **stdin**, **stdout**, and **stderr**(it'll be talked later), so I sorted the above funcs to learn deeply. I won't discuss these funcs one by one, instead I'll put them together to figure something out. Now, Let's begin !

#### stdin

Maybe you have paid attention to the type of data, **FILE**, which is a structure containing information about a file. In modern OS, we treat every thing as file, including device. This is very known by us. In *stdio.h*, it defines three expressions of type pointer to FILE:

	  stderr
	  	Standard error output stream.
	  stdin
	  	Standard input stream.
	  stdout
	  	Standard output stream.
