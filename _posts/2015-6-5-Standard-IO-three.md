---
title: Standard I/O Learning (3)
---

> Under normal circumstances every UNIX program has three streams opened for it when it starts up, one for input, one for output, and one for printing diagnostic or error messages.

### stdout

我突发奇想地想从 **stdout stream** 中读取数据，能不能办到呢？ 先来一片代码：

        char str[10];
        fprintf (stdout, "%s\n", "stdout");
	rewind (stdout);           //Maybe i should seek to the head of stream
	fgets (stdout, "%s", str);
	fprintf (stdout, "%s\n", str);
	
哈哈，脑洞来了。但是很遗憾，**str** 输出是一串乱码，说明没有读取成功。 不过我并不感到失望，下面说说我的理解。	

屏幕是标准的输出设备，所以这里可以把屏幕看作一个文件。这一系列文章开头的摘要中反复提到，程序启动时，系统会为其打开三个 stream，**stdout** 就是其中一个，那么 **stdout** 这个 FILE 变量指针就指向屏幕这个文件。这里我想强调一下 FILE  类型仅仅是对文件描述符的一种包装，我个人认为这和 C++ 里流的概念有所不同，虽然使用上并无差别。我们向 **stdout** 写数据，就等于把信息显示在屏幕上。

那么再来看那个程序就
