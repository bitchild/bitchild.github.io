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
  
Because here we just talking about **stdin**, **stdout**, and **stderr**(it'll be talked later), so I sorted the above funcs to learn deeply. I won't discuss these funcs one by one, instead I'll put them together to figure something out. 

Maybe you have paid attention to the type of data, **FILE**, which is a structure containing information about a file. In modern OS, we treat every thing as file, including device. This is very known by us. In *stdio.h*, it defines three expressions of type pointer to FILE:

	  stderr
	  	Standard error output stream.
	  stdin
	  	Standard input stream.
	  stdout
	  	Standard output stream.

God! I should have stopped talking about the basic knowledge. OK, now, Let's begin !

#### stdin 

> Firstly, see the code:
	
		char c1, c2;
		c1 = getchar();
		// getchar();
		c2 = getchar();
		printf("%d  %d\n", c1, c2);
	
A very simple code, but we can get some info from it. 

If you run the code, you'll find it just gets over after you input a character, following Enter key. And the output shows the num of c2 is 10, which means 'LF'(Enter key). When we done the input action, the stdin stream stored a char 
and '\n', so the c1 gets that char, and c2 gets '\n'. If we want to change to enable us input twice, we can insert another getchar(), like shown above. Here, we get a conclusion, that getchar func takes Enter key as terminal sign. And
it can be used as taking-up '\n'.

> Another Instance

Code as following:
	
	char s[10];
	scanf ("%s", s);
	printf ("%s", s);

	//getchar ();

	char buf[20];
	fgets (buf, 20, stdin);
	printf ("%snew line", buf);

Here we don't care about the out-of-boundary 0f scanf. It will be posted in detail later. As we know, scanf reads a string from stdin stream with leaving the '\n'. Then fgets reads from '\n' if we don't clean the stdin buffer. Under
 this circumstance, the second printf will just print "new line" in the next line, which means buf just stored '\n'.
Therefore, we can use getchar to absorb the '\n', and make the stdin empty. 

So far, we mainly introduced `getchar` and `fgets`. And we now know scanf won't keep '\n', but fgets will. In the Next 
post, more funcs will be discussed.

> In Wuhan 337 Prison
