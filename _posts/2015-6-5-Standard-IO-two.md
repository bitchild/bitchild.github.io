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

代码中，我们定义了一个 4 个字节长度的 char 数组 s[4]，然后执行过程中输入了 5 个字符， “scanf“。按通常情况，我们最多
允许输入 3 个字符，最后一个字符作为 '\0'。但从输出来看，这里 s 的打印输出完全正确。 虽然正确，但这里已经出现访问越界
了，由于 scanf 并不检查访问越界，所以这种情况下超出数组长度的字符会去占用其他的内存地址，我们来看看 gdb 的一些调试结果。
