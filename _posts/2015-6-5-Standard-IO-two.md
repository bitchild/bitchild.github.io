---
title: Standard I/O Learning (2)
---

> Under  normal circumstances every UNIX program has three streams opened for it when it starts up, one for input, one for output,  and one for printing diagnostic or error messages.

### Scanf 访问越界

先来看看上一篇中那个程序代码和执行输出:

Code:

	char s[4];
	scanf ("%s", s); 
	fprintf (stdout, "%s\n", s); 
	
	fgetc (stdin);
	
	char buf[5];
	fgets (buf, 5, stdin);
	fprintf (stdout, "%snew line", buf);

output:

	scanf
	scanf
	fgets
	fgetnew line

	
